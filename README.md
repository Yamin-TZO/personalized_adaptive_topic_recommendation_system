# Adaptive Topic Recommendation System

An implicit-feedback recommendation prototype designed to personalize learning topics for people using a chatbot-based learning platform in low-connectivity environments.

## Project overview

Learners do not always state what they want to study, and their interests can change as they interact with new content. This project explored how content-view behavior could be used to generate relevant topic recommendations without requiring explicit ratings.

I led the implementation as Product Owner during the ABW Data Analytics Fellowship. The project was recognized as one of the fellowship's top 8 projects in 2023.

## Notebooks

- [Topic Recommendation Based on Content Views](./Updated_Topic%20Recommendation%20based%20on%20content%20view.ipynb) demonstrates the end-to-end implicit-feedback pipeline, including interaction weighting, ALS model training, personalized recommendations, similar-content discovery and batch recommendations.
- [User Trend and Persona Exploration](./user_trend.ipynb) explores learner-interest data, standardization and clustering to identify user personas and inform recommendation features.

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

## Demonstrator scope

This prototype demonstrates an end-to-end recommendation workflow using implicit content-view signals. It generates personalized recommendations for individual learners and learner batches, identifies similar content, and supports filtering previously viewed items.

## Path to production

Production development would extend the demonstrator with ranking benchmarks, offline relevance metrics, cold-start strategies and controlled experiments measuring learning engagement, completion and competency outcomes.

## Technology

- Python
- pandas and NumPy
- SciPy sparse matrices
- implicit
- Alternating Least Squares
- BM25 weighting
- Google Colab

## References

- [implicit documentation](https://benfred.github.io/implicit/)
- [implicit GitHub repository](https://github.com/benfred/implicit)
- [Collaborative Filtering for Implicit Feedback Datasets](http://yifanhu.net/PUB/cf.pdf)
