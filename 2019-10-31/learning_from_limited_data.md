# Learning from Limited Training Data
## Shanghang Zhang

Deep learning has been very successful, but:
    Most deep learning are not data efficient -- requires millions of
    pieces of data
    Models to not generalize well to new domains or tasks

Domain & modality shift widely exist -- simulation vs real-world, rgb vs rgbd (depth)

Rely on large-scale *human annotated* data to learn a competent model

Traffic counting for multiple cameras with limited annotations
- Different perspectives, different backgrounds
- Differences even with one camera -- cloudy/sunny/rainy, traffic
  density
- Difficult to label enough training data

Source cameras: lots of labeled data
Target cameras: lots of unlabeled data

But, the cameras are different, need domain adaptation

