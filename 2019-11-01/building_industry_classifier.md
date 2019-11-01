# Building an Industry Classifier
## Ido Shlomo - BlueVine

https://github.com/ido-sh/odsc_presentations

Business need: for every client, predict their industry from the business
website

Main tools: scrapy D, scrapy, PyTorch, BERT, SageMaker

## Target - Gathering Websites
Potential sources: 
- internal BV data -- not very big, skewed scope
- directed web searches "car dealerships in US" -- high effort, limited
  scope
- Propietary databases -- big, pricy, outdated

Solution -- use some combination of these

Problem -- we have 135 industries
- Want sample to be balanced
- Need to know the industry
- But, if we knew the industry, wouldn't need the model
Solution:
- Use proxy to guess the industry
    - Internal BV data
    - Web searches: search term

## Target - Tagging the Industry
Goals:
- Get quality tags, in reasonable timeframe, stay within budget

Crowdsourcing challenges
- Understanding 135 industry categories is hard
- Understanding what a business does is hard
- Tie-breaking is hard

Solution:
- Set max $$$ budget
- Set max time per task (in seconds)
- Develop small in-house tagged test set
- Host vendor trials for all strategies
- From vendors within max time cap: chose one with highest accuracy
- Used CloudFactory

Outcome:
- 3 months
- 250K observations (business names + websites)
- Not balanced, but sufficient

## Data - building the crawler
For each URL, we need:
- Home page text cleaned (no html)
- Internal pages text cleaned (no html)
- Page metadata (e.g. path, title, click text, etc.)
- Ability to choose where the crawler goes (which pages, etc.)
- Save the raw data as a backup

Tool: Scrapy - https://docs.scrapy.org/en/latest/index.html
- URL -> Request -> Response (includes internal links, more URLs) -> Item -> Pipeline -> Storage

good_hit = ['about', 'story', 'what we do', 'capabilities', 'services', ...]

## Crawling at scale
- 250K urls, run batches, in parallel
- Persistent
- Some logging / UI mechanism to follow progress

ScrapyD - starts up a project and creates a webpage to view progress

## Model - Design (BERT)
- BERT, simplified
- Turns a string of text into a vector of length 768 (or 1024)
- Max 512 tokens allowed (a word, a piece of a word)
- Open-source pre-trained models available (cased, uncased
- For PyTorch - https://github.com/huggingface/transfer-learning-conv-ai

- Uses WordPiece tokenization to split words into tokens
- Bi-directional (rtl, ltr)
- Achieves state of the art results

- Recommendation - read BERT paper
- Pass in a sentence, spit out 1x768 vector

Implementation:
- Use first 5 links per domain
- Free text: page text, page title, website domain
- Metadata - domain extension
- Other - business name

## Model - Train
Tool: PyTorch -- basically NumPy + GPU's
- Easiest to debug
- Autograd -- figuring out what kind of gradient descent to do

## Model - Deploy
Goal:
- Model hosted in the cloud
- Always up (persistence)
- Communicates via API
- Auto-scaling
- All the pros of docker deployment without writing docker code

Include optional ML packages - zipped & put in S3 -> builds Docker image
-> spins up Ec2 instance -> Model app & endpoint started
- Can use with "local" mode -- stored on host and image run on host

model_fn:
- Load trained model
- Load pretrained tokenizer
- Return response

https://aws.amazon.com/getting-started/tutorials/build-train-deploy-machine-learning-model-sagemaker/
