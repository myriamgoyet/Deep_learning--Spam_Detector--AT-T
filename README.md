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
│ ├── AT&T_PART3_DistilBERTwithTensorflow.ipynb
│ ├── AT&T_PART4_DistilBERT+LRwithPyTorch.ipynb
│ └── AT&T_Spam_Detector.ipynb
├── Models_trained/
│ ├── DistilBERT_ft/
│ ├── DistilBERT+lr/
│ ├── Baseline_model.joblib
│ └── tokenizer_baseline_model.json
├── Evaluations/
│ ├── DistilBERT_lr/
│ ├── baseline_model_metrics.json
│ ├── DistilBERT_ft_metrics.json
│ └── DistilBERT_ft_threshold_metrics.json
└── README.md    
```
## Models tested 📬

 1. A simple deep learning model with good results :     
  **Model architecture :**     
  ![Sans titre](https://github.com/user-attachments/assets/bb334c9d-30a9-4409-9e86-0e93c6c81ac8)     
  **Model metrics :**     
  ![Sans titre](https://github.com/user-attachments/assets/57a8ab20-bf4e-47c7-b4d0-bbc205258c9b)  
  **Model confusion matrice :**     
  ![Sans titre](https://github.com/user-attachments/assets/be95d6a5-41f0-40c8-ab6f-774280a94755)
![Sans titre](https://github.com/user-attachments/assets/14a0ccc5-2f33-4d81-a262-241767a50382)
```
Classification_report - Training set
              precision    recall  f1-score   support

           0       1.00      1.00      1.00      3161
           1       1.00      0.98      0.99       457

    accuracy                           1.00      3618
   macro avg       1.00      0.99      0.99      3618
weighted avg       1.00      1.00      1.00      3618

Classification_report - Validation set
              precision    recall  f1-score   support

           0       0.98      1.00      0.99      1355
           1       0.98      0.86      0.92       196

    accuracy                           0.98      1551
   macro avg       0.98      0.93      0.95      1551
weighted avg       0.98      0.98      0.98      1551
```     


 2. A DistrilBERT pretrained model finetuned with tensorflow with low efficiency results:
  
