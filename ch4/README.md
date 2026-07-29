## Chapter 4: Text classification  

### Key takeaways
- To classify textual data we can use both generative and representation models.
- It may be useful to use a pre-trained model that suits the specific data we want to classify. This is called a task-specific model. However, it might be hard to find a suitable task-specific model for our desired application.
- We can also use an embedding model, which is a foundation model that gets trained with a labeled dataset or domain data.
- Additionally, we can also perform a zero-shot classification, which predicts labels even though it wasn't trained on them. We achieve this by defining candidate labels, and then the model decides how an input is related to those candidate labels (more on this below in "projects").
- To measure how accurate our model is in classifying data, we use the below metrics (and a confusion matrix to make it easier to understand):

  <img width="537" height="247" alt="Screenshot 2026-07-25 at 10 51 17" src="https://github.com/user-attachments/assets/97fdb21c-fc59-49b6-a46a-199914dc34e3" />

  - Precision: answers the question “Of the items the classifier predicted as this class, how many were actually that class?”  
  
    $Precision = \frac{True Positives}{True Positives + False Positives}$

  - Recall: answers the question "Of all the actual positives, how many did the classifier correctly identify?"
  
    $Recall = \frac{True Positives}{True Positives + False Negatives}$

  - Accuracy: answers the question "How often is the classifier correct overall?"
  
    $Accuracy = \frac{True Positives + True Negatives}{True Positives + False Negatives + True Negatives + False Positives}$

  - F1 score: combines precision and recall using their harmonic mean. 

    $Accuracy = 2 · \frac{precision · recall}{precision + recall}$

  <img width="537" height="264" alt="Screenshot 2026-07-25 at 11 12 52" src="https://github.com/user-attachments/assets/d1a79f69-e505-4b8e-836b-a679b60896a5" />

- The book takes the weigthed average of the F1 score into account (highlighted in bold).

### Links
- [Huggingface MTEB Leaderboard](https://huggingface.co/spaces/mteb/leaderboard): to select the most relevant model for an application  
- [How OpenAI trained ChatGPT](https://openai.com/index/chatgpt/)

### Projects
1. **classification_task_specific:** both dataset and model libraries seem to have been modified since the publication of the book. I used the "cardiffnlp/twitter-roberta-base-sentiment-latest" pre-trained model that classifies positive/neutral/negative tweets. I had to group the negative and neutral labels of the model together as the dataset only had negative=0 and positive=1 labels.
2. **classification_embedding_model:** the base model is "sentence-transformers/all-mpnet-base-v2" and fine tuned with the train data of the dataset with logistic regression.
3. **zero-shot-classification:** two opposite sentiment labels are embedded and the model indicates what movie review of the test dataset is similar to them using cosine similarity.
  
   <img width="529" height="292" alt="Screenshot 2026-07-25 at 11 55 26" src="https://github.com/user-attachments/assets/aa1c90a9-6c49-41dc-88e2-626476ac3b83" />


