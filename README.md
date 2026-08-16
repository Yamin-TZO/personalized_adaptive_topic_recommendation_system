# Adaptive Topic Recommendation System

An implicit-feedback recommendation prototype designed to personalize learning topics for people using a chatbot-based learning platform in low-connectivity environments.

## Project overview

Learners do not always state what they want to study, and their interests can change as they interact with new content. This project explored how content-view behavior could be used to generate relevant topic recommendations without requiring explicit ratings.

I led the implementation as Product Owner during the ABW Data Analytics Fellowship. The project was recognized as one of the fellowship's top 8 projects in 2023.

## Product goal

The prototype was designed to help:

- Learners discover relevant topics based on their observed interests.
- Content teams identify useful learning pathways and prioritize resources.
- Product and development teams test personalized learning experiences before investing in production integration.

## Data and approach

The working notebook used a snapshot of:

- 2,018 content-view events
- 388 learners
- 179 content items

The prototype converted learner-content interactions into a sparse matrix and treated repeated views as implicit positive feedback. It then:

1. Aggregated view counts for each learner-content pair.
2. Applied BM25 weighting to reduce the influence of unusually frequent viewers and highly popular content.
3. Trained a confidence-weighted Alternating Least Squares collaborative-filtering model.
4. Generated top-N recommendations for individual learners and batches of learners.
5. Explored similar-content recommendations using learned item relationships.

The model used 64 latent factors, 0.05 regularization and an alpha value of 2.0 in the tested notebook.

## Prototype workflow

```text
Content-view events
        ↓
Learner and content indexing
        ↓
Sparse interaction matrix
        ↓
BM25 confidence weighting
        ↓
Implicit-feedback ALS model
        ↓
Personalized topics and similar-content recommendations
```

## What the prototype demonstrated

- Behavioral data can provide a useful personalization signal when explicit ratings are unavailable.
- Confidence weighting can balance repeated engagement against popularity bias.
- The same model can support single-user, batch and similar-content recommendation use cases.
- Recommendation outputs can be filtered to exclude content a learner has already viewed.

## Limitations and next steps

This was a fellowship prototype, not a production deployment. The notebook demonstrated recommendation generation but did not include a formal offline evaluation or an online experiment.

The next validation steps would be:

- Define relevance and learning-success metrics such as precision at K, completion and competency improvement.
- Compare ALS recommendations with popularity and content-based baselines.
- Test cold-start strategies for new learners and new content.
- Add recency, explicit feedback and learning-goal signals.
- Run controlled experiments before integrating recommendations into a live chatbot experience.

## Technology

- Python
- pandas and NumPy
- SciPy sparse matrices
- implicit
- Alternating Least Squares
- BM25 weighting
- Google Colab

## Repository note

This repository documents the product problem, prototype method and findings. The project deck is intentionally not included, and organization-specific data and notebook paths remain private.

## References

- [implicit documentation](https://benfred.github.io/implicit/)
- [implicit GitHub repository](https://github.com/benfred/implicit)
- [Collaborative Filtering for Implicit Feedback Datasets](http://yifanhu.net/PUB/cf.pdf)
