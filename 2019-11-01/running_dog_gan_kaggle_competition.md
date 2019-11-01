# How we ran a dog image generation/GAN competition on Kaggle
## Wendy Kan

Deep Learning -- first came out on Kaggle in 2012 Merck
XGBoost appeared on Kaggle in 2014
Keras appeared on Kaggle in 2016

Generative Adversarial Network
- Generator -- black box neural network
- Discriminator -- trained to produce a score

Input vector -> Generator -> Image

BigGAN -- current state of the art, developed by DeepMind

Design challenges:
- What to generate?
- Kernals with no internet access

Evaluation challenges:
- Human evaluation is not feasible
- Automatic evaluation is difficult

Evaluating GANs remains controversial, and is a hot-topic in research
- Inception score -- example
- Fréchet Inception Distance (FID)

3 parts of the metric:
    - If pre-trained models think this is definitely a dog, then it's a better 
    quality image (*Saliency*) -- lower entropy between classes

    - *Diversity* -- Even distrobution across different classes

    - *Memorization* -- look at nearest neighbor (cosine difference) of training 
    images, and see if it's too close

Memorization informed Freched Inception Distance

Public/Private score
- Public -- use Inception model, use ImageNot dogs
- Private -- NASNet, use ImageNet dogs + Kaggle employees' dogs + internet
  dogs

Compute limit
- Submission is only allowed on Kaggle's cloud computing service to
  prevent service -- compute is not unlimited

900 teams, 37,000 submissions, 11,000 scores
- Top FID (public) = 31.06, comparing to BigGAN 18.6
- Not as good, but impressive for limited compute resources
- 4 out of top 5 used BigGAN
- Memory limit - 13GB CPU, and 9 hours of compute

Smart ways to cheat:
    - Memorization GANs -- training discriminator to fit the training set,
    freezing the discriminator, and then training the generator -- have to
    read the code to catch it
    - Mapping 10k-one-hot vectors to the 10k training images
    - VAE - variational auto-encoder -- generating results for
      reconstructing images
      - Augmentation or blending (cropping, morphing, adding noise, etc.)
        of training set
    - Had to manually adjust cutoff for memorization distance threshold by
      looking 

User progression:
- GANs are hard to train. They get pretty unstable and it's a lot of work
  to get them right -- the community really worked together

System design:
- Our system design is decent in terms of giving real-time (5min) feedback
- Having public/private scores eliminates overfitting/cheating potentials

Metric design:
- MiFID works well and overall consistent with quality/dieversity of
  images
- Memorization score privides good distinction between cheaters and not
- Some "very good" images didn't win -- maybe need to rebalance
  diversity/saliency
