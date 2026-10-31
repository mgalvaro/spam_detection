# Spam Email Detection

A machine learning project to classify emails as **spam** or **legitimate**, with a particular focus on minimizing false positives.

## Project Overview

The goal of this project is to build a model that identifies unwanted emails while ensuring that fewer than 1% of legitimate emails are incorrectly classified as spam.

In this context, avoiding false positives is especially important: a legitimate email incorrectly sent to the spam folder could cause the user to miss an important message.

## Dataset

The project uses a labelled email dataset containing two categories:

- `0`: Legitimate email
- `1`: Spam email

The dataset is explored and prepared before training the classification model.

## Methodology

The project follows these main steps:

1. **Exploratory Data Analysis:** Inspect the dataset and examine the distribution of the target classes.
2. **Text preprocessing:** Convert text to lowercase, replace URLs and email addresses with tokens, remove punctuation and numbers, remove stopwords, and apply lemmatization.
3. **Feature extraction:** Use `CountVectorizer` to transform email text into Bag-of-Words features.
4. **Model training:** Train a `RandomForestClassifier`.
5. **Model evaluation:** Analyse the confusion matrix, accuracy, precision, recall, F1-score and False Positive Rate (FPR).
6. **Threshold selection:** Adjust the probability threshold to reduce false positives while retaining as much spam detection performance as possible.
7. **Model persistence:** Save the trained pipeline and selected threshold using pickle.

## Results

The final model was evaluated on an independent holdout set.

| Metric | Result |
|---|---:|
| Decision threshold | 0.65 |
| False Positive Rate | 0.82% |
| Spam Recall | 80.00% |
| Accuracy | 93.62% |

The model achieved the main project objective on the evaluation set: the False Positive Rate remained below 1%.

The selected threshold reflects a trade-off: reducing false positives comes at the cost of missing some spam emails.

## Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- NLTK
- Matplotlib
- Seaborn
- Jupyter Notebook

## Project Structure

```text
spam-email-detection/
│
├── Data/
│   └── spam.csv
│
├── spam_detection.ipynb
├── spam_detection_model.pkl
└── README.md
```

The dataset and trained model are not necessarily included in the repository. Check the repository contents before running the notebook.

## Future Improvements

Some possible next steps include:

- Comparing Random Forest with other classifiers, such as Naive Bayes and Logistic Regression.
- Testing TF-IDF as an alternative to Bag of Words.
- Performing systematic hyperparameter tuning.
- Evaluating model stability across different data splits.
- Building a simple interactive application using Streamlit.

## Disclaimer

The reported metrics describe performance on the available holdout dataset. They do not guarantee the same performance on new emails or in a real-world email filtering system.

---

**Author:** Álvaro Mejía
