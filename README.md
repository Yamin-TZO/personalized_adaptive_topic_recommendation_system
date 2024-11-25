# Background Information
As one of the pioneers in Southeast Asia of implementing the chatbot-based learning management system, learners' learning experiences are enhanced by personalized feedback, which resonates with their distinct skill sets, individual learning strategies, and diverse goals. Besides, owing to the limited internet access in Myanmar, learners require a flexible learning pace that allows them to study at their convenience.

This led to one of our solutions to ensure that our chatbot not only delivers personalized content based on learner’s persona, interest and behavior but also evolves with the learner, adapting to their changing needs and abilities.

As an end-user (learner) in the chatbot, they will be able to get the personalized experience in learning in order to achieve the respective goal effectively within the short period of time.

# Introduction
This project is contributing a critical role of achieving the above mentioned experience through chatbot.

## Goal:
The goal of the project is to give the topic recommendation to learners based on user interest on topics.

## Model Reference:
This project is based on implicit library which focuses on implicit feedback recommenders systems - where we are given positive examples of what the user has interacted with, but aren't given the corresponding negative examples of what users aren't interested in. I will use the AlternatingLeastSquares model that's based off the paper Collaborative Filtering for Implicit Feedback Datasets. This model aims to learn a binary target of whether each user has interacted with each item - but weights each binary interaction by a confidence value of how confident we are in this user/item interaction. The implementation in implicit uses the values of a sparse matrix to represent the confidences, with the non zero entries representing whether or not the user has interacted with the item.

# Stakeholders and their use cases
+77,000 learners for their effective and engaging learning experience for achieving respective goal(s) through chatbot
The content team will be able to prioritize the courses, pathways to provide effective learning resources to learners.
The development and product team will be able to allocate resources in order to conduct the progressive test on the initial algorithm for the better and effective user experience

# Reference:
https://github.com/benfred/implicit/tree/main
https://benfred.github.io/implicit/
