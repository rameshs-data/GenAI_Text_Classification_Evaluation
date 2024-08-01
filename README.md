# Binary Text Classification for Safety and Security Messages

## Overview

This project involves cleaning up a notebook that trains models for a binary text classification task and brainstorming the pros and cons of using an LLM (Large Language Model) to create labels for the data.

## Problem Statement
The project has two main parts: Coding and Brainstorming.

### Coding
The provided notebook is full of issues, including poor coding practices, machine learning pitfalls, and silent bugs. The task is to clean up the notebook and fix these issues. The focus should be on the models provided; there is no need to train additional models, though experimentation is welcome.

### Brainstorming
Based on the classification task and the notebook, consider the pros and cons of using an LLM for data labeling. Discuss how this strategy affects other components of the classification pipeline. Focus on a specific concept or two for detailed discussion in an upcoming interview.

## Files
- `data.csv`: Data for the task
- `train_models.ipynb`: Notebook that trains the models
- `train_embs.npy`, `test_embs.npy`: Text embeddings for the data from `sentence-transformers/paraphrase-mpnet-base-v2`. The embeddings can be used directly as in the notebook, with code available to recreate them if needed.

## Classification Task
This is a binary text classification problem. The messages being classified are social recognition messages meant to express recognition and gratitude. The task is to determine whether a message is related to "safety or security". Positive examples include:

- "Mary went above and beyond her own personal comfort zone in assisting in a safety incident in the lab. She printed MS sheets and made the situation safe for both me and her colleagues in the area. She also was an amazing, calming influence on a high stress situation."
- "Lisa - thanks for taking the time to double check a suspicious contact that came in to you this week - although we were able to verify the message after a bit of digging it was certainly VERY odd looking and certainly worth a second look. You demonstrated fantastic security reflexes!"

Since human annotators were unavailable, the messages were labeled by an LLM using the following prompt:
```
You will be given a piece of recognition or gratitude message written between colleagues at workplace.
You will determine whether or not that message is related to safety or security based solely on its content. Return "True" if it is related, and "False" otherwise.
```
The `target` column in the dataset contains the LLM's output: True or False.

## Understanding Precision and Recall
This project emphasizes the importance of precision and recall in evaluating the performance of classification models.

### Precision
Precision is the ratio of true positive predictions to the total number of positive predictions (true positives + false positives). It indicates how many of the predicted positive instances are actually positive. High precision means that the classifier is accurate when it predicts a positive instance.

### Recall
Recall is the ratio of true positive predictions to the total number of actual positive instances (true positives + false negatives). It indicates how well the classifier can identify all positive instances. High recall means that the classifier is able to detect most of the actual positive instances.

### Importance in this Project
- **Precision**: In the context of classifying messages as related to safety or security, high precision ensures that the messages flagged as safety or security-related are indeed relevant. This minimizes false positives, which is crucial for maintaining trust in the system.
- **Recall**: High recall ensures that most safety or security-related messages are identified, which is critical for ensuring that important messages are not missed.

Balancing precision and recall is essential to create a reliable and effective classification model.

## How to Run the Project
1. **Install Dependencies**: Ensure all required libraries are installed. You can install them using:
   ```bash
   pip install -r requirements.txt

