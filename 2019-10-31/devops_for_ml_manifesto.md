# Chaos and Pain in Machine Learning and the 'DevOps for ML Manifest'
## Dr. Nick Ball - Dotscience
https://dotscience.com/manifesto/

## AI Efforts Today
- An immature discipline -- wild west
- Chaos and pain operationalizing AI

### Key Problems
- Wasting time
    - Multiple people doing the same work, etc.
- Inneficient collaboration
- Manual tracking 
    - somebody keeps a spreadsheet of all the models they ran
- No reproducibility or provenance
- Unmonitored models

## What is needed: DevOps for ML
- AKA "MLOps"

We were here before with software in the 90s -- siloed, no version control, no 
continuous delivery

### Requirements for DevOps for ML
1. *Reproducible* -- be able to retrain a months-old model and achieve the
   same results
2. *Accountable* -- must be able to trace back from model in production to
   its provenance
3. *Collaborative* -- must be able to do asynchronous collaboration
    - Someone who didn't start a project should be able to start working
      on it
4. *Continuous* -- must be able to deploy automatically & monitor
   statistically

### Data Engineering and ML are Different from Software Development
- There are more steps than just code, test, deploy, monitor
- Code - Data Runs - Parameters - Model Runs - Models/Metrics - Deploy
  - Monitor
- Existing DevOps tools are insufficient

ML has more moving parts -- tracking "runs", not just "code"
- Must include versions of these used each time

## How to achieve DevOps for ML
- Version control is fundamental to all of this

### Making it reproducible 
- Must know the environment as exactly as you can -- version the
  environment
- Version the code + notebooks, including parameters
- Version the data

### How?
For environment, Docker
For code, git
- But, it's not natural to commit every time you change anything (e.g.
  while tuning parameters in a huge grid-search)
- Dotmesh with ZFS -- tracks the data "git for data"
- OpenZFS
- Tracks metrics, lineage, diff

For CI/CD
- Should be able to get things to production with no manual steps
- Most commonly, you could use Kubernetes

For monitoring
- Think of ML models as microservices, use Prometheous
- For dashboards, prometheus is often paired with Grafana

Docker + Git + Kubernetes + Prometheus + Grafana + ...

Or, try dotscience :)

dotscience.com/deploy
dotscience.com/blog
