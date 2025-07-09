# Deep_learning--Spam_Detector--AT-T

Fictive project completed as part of my Data Scientist Training with jedha Bootcamp (Paris)

## Project 🚧

One of the main pain point that AT&T users are facing is constant exposure to SPAM messages.

AT&T has been able to manually flag spam messages for a time, but they are looking for an automated way of detecting spams to protect their users.

## Goals 🎯
The goal for this project is to build a spam detector, that can automatically flag spams as they come based solely on the sms' content.

## Scope of this project 🖼️

Dataset used for this project : [Dowload the Dataset](https://full-stack-bigdata-datasets.s3.eu-west-3.amazonaws.com/Deep+Learning/project/spam.csv)

## 📁 Project Structure
```
Deep_learning--Spam_Detector--AT-T/
│
├── notebooks/
│ ├── AT&T_PART1-Preprocessing.ipynb
│ ├── AT&T_data_preprocessed.csv
│ ├── AT&T_PART2_Baseline-model.ipynb
│ ├── AT&T_PART3_DistilBERT+LRwithPyTorch.ipynb
│ └── AT&T_Spam_Detector.ipynb
├── Evaluations/
│ ├── DistilBERT_lr/
│ └── baseline_model_metrics.json
└── README.md    
```
## Models tested 📬

 1. A simple sequential Deep learning model     
     **Model architecture :**     
    ```
    model = tf.keras.Sequential([ # to create neural network models with layers stacked on top of each other
      tf.keras.layers.Embedding(input_dim=vocab_size, output_dim=50, name="embedding"),  # Converts tokens into dense vectors of 50 dimensions
      tf.keras.layers.GlobalAveragePooling1D(),  # Averages the word embeddings across the sentence to reduce dimensions
      tf.keras.layers.Dense(16, activation='relu'),  # Hidden Dense layer with ReLU activation
      tf.keras.layers.Dense(1, activation="sigmoid")  # Output layer (Binary Classification)
    ])
    optimizer = Adam(learning_rate=0.001)
    ```
 2. A model in two steps using first DistrilBERT pretrained model for embedding, and then logistic regression for classification       
    **Model used for Embedding :**      
    ```
    model_name = "distilbert-base-uncased"
    tokenizer = AutoTokenizer.from_pretrained(model_name)
    model = AutoModel.from_pretrained(model_name)
    ```
    **Model used for classification :**
    ```
    model_lr = make_pipeline(
        StandardScaler(),
        LogisticRegression(max_iter=1000)
    )
    ```

  ## ⭐ Models performance
|                | Accuracy Train | Accuracy Test | F1 Score Train | F1 Score Test | Precision Train | Precision Test | Recall Train | Recall Test |
|----------------|----------------|---------------|----------------|---------------|-----------------|----------------|--------------|-------------|
| Baseline model |   1.00         |   0.98        |    0.99        |    0.92       |  1.00           | 0.98           |  0.98        | 0.86        |
| DistilBERT+lr  |    1.00        |      0.99     |       1.00     |        0.95   |   1.00          | 0.97           |  1.00        |  0.94       |  

### ✨The Baseline model is already good!    
✅ Strong accuracy and F1 score   
🚩 But recall on test set is slighlty lower, suggesting that the model is not perfect at identifying spams     

### 😍 The DistilBERT + Logistic regression model gets better metrics     
✅ Strong accuracy and F1 score + better recall     
🚩 However, the model is heavyer (even if not excissively) and takes more time to run. Depending of the machine used and the database, a lighter model could be prefered.
