# Tutorial on Reinforcement Learning
## Pieter Abbeel -- UC Berkeley

https://covariant.ai/

Agent interacts with environment, agent acts, maybe there's a reward, and
then it continues

What can it learn?
- Mastery in wide range of domains

How fast does it learn?
- Humans after 15 minutes tend to outperform DDQN after 115 hours

How come humans can learn so quickly? How to bridge this cap?
- Humans might play Atari for the first time
- But, they come in with a lot of experience
- Can we build AI systems to similarly exploit experience?

## Few-Shot Reinforcement Learning
- Need all your data ahead of time

Agent exposed to Environment A, B, C, D, and then when faced with a new
environment Z, it's ready to learn fast
- Learn to be ready to learn -- a lot like school/job

Similar to train/test -- train in "training environments", hope it does
well in "test environments"

Recurring Neural Network -- has activations it can reuse and adapt

Evaluation: Multi-Armed Bandits
- Each bandit has its own distribution
- Good RL agent should explore bandits sufficiently, yet also exploid the
  good/best ones

There are ascimtotically provably optimal algorithms
- RNN does as well as the optimal algorithm!

Visual navigation:
    - Agent that learns to explore, look around corners, and remember where 
    treasure is

## Leveraging Simulation
- What if you don't have enough data to train a learned-to-learn agent?

- Simulated data collection is easier to collect, less expensive, etc.

How do we make sure it's like reality?

Approach 1: Use realistic simulator
- Not always possible/practical

Approach 2: Domain confusion/adaptation
- Don't want it to know if it's the real world
- Have some layers erase some of the information, so that the data you get
  to work with is the same whether from simulation or real-world
  - Have another network trying to detect whether something is sim/real,
    and try to fool it

Approach 3: Domain randomization:
- If you can generate lots of data really really quickly, and patterns are
  random enough, then the real world may just look like the next simulator
    - e.g. different coloring, lighting, orientation, shading, etc.

(cad)^2 rl: Real Single-Image Flight Without a Single Real Image
- Quadcopter collision avoidance -- it works!

If you generate enough images to train on, simulated images

Randomize across different material properties -- mass, friction, etc. --
works much better than training on the 'ideal' simulation -- need an
ensemble of simulators

If it can adapt to many thousands/millions of simulations, it can adapt to
the real world

## Learning Representations for Exploration
- Can reinforcement do exploration that's not just random?

- Traditionally:
    - Action space noise (e.g. jittering randomly)
    - Parameter space noise (e.g. moving in random pattern/direction)
    - Exploration bonuses -- after the fact, try to visit again something
      not often visited
        - But, this is too late

Can we explore in a more informed way?
Can we learn a latent space that indexes into good exploratory behaviors?
- e.g. a list of actions that will likely be beneficial to explore

Approach 1: Hausment 2018
- Train against many tasks, and keep track -- "Test/Generalize"

Approach 2: Gupta 2018
- Train against many tasks, and keep track -- "Test/Generalize" in z-space

## Resources
- Berkeley Deep RL Bootcamp (all materials online)
- Berkley Deep RL Course
- David Silver Lectures - youtube 
- Deepmind Lectures - youtube
- spinningup.openai.com

Deep RL Code Bases
- rllab (berkley)
- spinning up (OpenAI)
- rlpyt (berkley)
- baselines (openai)
- dopamine (Google)
- horizon (Facebook)
- rllib/ray (berkley)

Environments:
- Arcade Learning Environment
- Mujoco.org
- Minecraft
- Deepmind Lab/Labyrinth
- OpenAI Gym
- OpenAi Universe
