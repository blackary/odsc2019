# Building End-To-End ML Pipelines with Open-Source Technologies

https://pipeline.ai/ -- all the slides

KubeFlow

When you push your model to production, your model is:
- Already out of date -- need to re-train
- Biased - need to validate before pushing
- Broken -- need to A/B test in production
- Hacked - need to train with data privacy
    - TFPrivacy - https://github.com/tensorflow/privacy
    - Differential privacy -- "introduce noise during training so you
      can't get to the initial training data"
- Slow -- need to quantize and speed up predictions

MLFlow - tracking experiments
Papermill - lets you pass parameters to a jupyter notebook, version them,
scheduled jobs, etc.

"FeatureStore" -- "data lake for features"

TFX - TensorFlow Extended - is an end-to-end platform for deploying production 
ML pipelines

KubeFlow

Airflow ML Pipelines - workflow orchestration

HyperParameter Tuning - Katib
