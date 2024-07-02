# Overview

## Instructions
You've been given a short jupyter notebook that trains and evaluates a couple of models on a simple classification task.   
There are two parts to this assignment: Coding & Brainstorming.
#### Coding
The notebook is full of issues, ranging from general poor coding & ML practices to silent bugs. We'd like you to clean up the notebook and fix those issues.    
You can just focus on the models provided, there's no need to train any others. Though feel free to experiment if you'd like!  
#### Brainstorming
Based on the classification task description and notebook, think about: what are the pros and cons of the data labeling strategy that we're using and how does it affect other components of the classification pipeline? (We're using an LLM to create labels - see the bottom section for details). 
There are many components to that answer - don't worry about covering everything. Instead, focus more in detail on a specific concept or two, and we'll discuss it at one of your next interviews!

## Files:
* `data.csv`: data for the task
* `train_models.ipynb`: notebook that trains the models
* `train_embs.npy`, `test_embs.npy`: Text embeddings for the data from `sentence-transformers/paraphrase-mpnet-base-v2`. Feel free to use these embeddings directly as in the notebook. The code to generate them is in the notebook, so you can recreate them if you'd like.


## Classification Task
This problem is a binary text classification problem. The messages being classified are social recognition messages which are supposed to be all about recognition & gratitude. Feel free to peruse examples in the notebook.  

The classification task is to determine whether a message is related "safety or security", and messages that are positively labeled should be related. Here are a couple of positive examples (they're also in the dataset):
* `Mary went above and beyond her own personal comfort zone in assisting in a safety incident in the lab. She printed MS sheets and made the situation safe for both me and her colleagues in the area. She also was an amazing, calming influence on a high stress situation.`
* `Lisa - thanks for taking the time to double check a suspicious contact that came in to you this week - although we were able to verify the message after a bit of digging it was certainly VERY odd looking and certainly worth a second look. You demonstrated fantastic security reflexes !`


However, our annotators were busy working on other projects, so these messages were not human labeled. Instead, they're labeled by an LLM with the following prompt:  
```
You will be given a piece of recognition or gratitude message written between colleagues at workplace.
You will determine whether or not that message is related to safety or security based solely on its content. Return "True" if it is related, and "False" otherwise.
```
The column `target` in the dataset, which is what the models in the notebook predict, is the LLM's output - True or False.
