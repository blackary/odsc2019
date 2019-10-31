# Regulation of AI

AI Fairness 360 Toolkit
Watson Open Scale

# Security in AI

Attacking AI
    - Integrity
        - Cause system not to produce indended results
        - Cause system to produce targed results
    - Confidentiality
Misuse AI
    - Attack other systems, devise attacks

Example: self-driving cars
- Stickers on stop sign - change image classification to say "speed
  limit 45km/h"
- These can work under different distances, angles, other conditions

Adversarial perturbation to images can fool state of the art Visual Q&A systems
Can also work in deep reinforcement learning -- you can fool trained deep
reinforcement learning agents

These are all white-box attacks, assuming attackers have access to the
details of the models

Can be very effective

Black-box attacks -- attackers don't know details of learning model
- Even in these settings, attacks can be successful

Adversarial Machine Learning -- learning in the presence of adversaries
- Hundreds of papers published on detecting or preventing these types of
  attacks
- Today, no general defence

Can Neural Networks remember training data, so that adversaries can
extract secrets from the training data by querying?

Example: language model
- Trained language model on Entron Email dataset
- Contains actual people's credit card and SSNs
- Can extract 3 of the 10 secrets completely by querying trained models
- New measure "Exposure" for memorization

Preventing memorization -- train a differentially-private neural network
- Differential privacy -- a formal notion of privacy
- Exposure it lower empirically

Differential privacy
- One dataset has one more data point than other
- A randomized model trained on each data set produces very similar
  results

Goals:
- Usability for non-experts
- Broad support for analytics and ml workload
- Easy integration with existing data environments

Chorus -- automatically rewrites SQL input queries into "intrinsically
private queries"

# Algorithmic Bias
- gendershades.org
    - Performed much more poorly on dark-skinned women

Different sources of bias
- *Representation bias*
- *Evaluation bias* (benchmark datasets may be biased)

Machine Bias - prediction fails different for black defendants

Recitivism software - 137 inputs to black box system
- https://www.theatlantic.com/technology/archive/2018/01/equivant-compas-algorithm/550646/
- https://advances.sciencemag.org/content/4/1/eaao5580.full
- "21 definitions of fairness"

Even when race and gender are not inputs, machine learning excels at
finding latent variables

Predictive policing -- predicting more crime in certain neighborhood -->
more police --> more arrests --> predicting more crime

*Historical bias*
- Fundamental structural issue with the first step of the data generation
  process, and can exist even with perfect sampling
- Work with domain expers and those affected

Case study: Online Ad Delivery
- Names associated with black people trigger ads suggesting they may have
  been arrested
- Using A/B testing to see which more people are clicking on lead to this

What human rights and civil rights do we need to protect?

*Measurement Bias*
- Using historical electronic health records data, which are most
  predictive of having a stroke?
  - Prior stroke
  - Cario disease
  - Accidental injury??
  - Benign breast lump??
  - Colonoscopy??
  - Sinusitus??

Really measuring people who utilize healthcare, and those who don't, for
whatever reason

NYT - "Racial Bias, Even When We Have Good Intentions"

##If humans are biased, why does algorithmic bias matter?

ML can amplify bias

Algorithms are used differently than human decision makers
- They are assumed to be objective and error-free
- More likely to be implemented with no appeals process in place
- They're cheap, and scale well

"The privileged are processed by people; the poor are processed by
algorithms"

Questions to ask:
- Should we even be doing this? Could it be weaponized?
- What bias is in the data?
    - Datasheets for datasets
- Can the code and data be audited
- What are error rates for different sub-groups?
- What is the accuracy of a simple rule-based alternative?
    - e.g. simple linear classifier with 2 inputs works as well as Compas with
      137 inputs - https://advances.sciencemag.org/content/4/1/eaao5580.full
