# Project Part 2 Write-Up: Amazon review binary classifier

## By Yuchuan Ma, Shay McBride
### Kaggle IDs: Helen Maaa, Shay Mcbride


In this project, you will be given product reviews from Amazon. Your task is to perform binary classification, where the goal is to identify if the text represents a high-star review or a low-star review. For the purposes of this task, we define a high-star review as one with a score > 3 (i.e. a 4 or 5 star review), with low-star reviews being <= 3 (i.e. 1,2,3 star reviews).

### Data
#### Dataset Description
The dataset used for building an Amazon review binary classification model contains various attributes. The primary target variable is the 'overall' column, categorized as high-star reviews (> 3) or low-star reviews (<= 3).

#### Preprocessing & Feature Engineering
Initial data had missing values, particularly in the 'reviewerName', 'summary', 'vote', 'image', and 'style' columns. Rows with null 'summary' values were dropped for data integrity. The 'overall' rating was converted to binary form ('target'). Text columns, 'reviewText' and 'summary', underwent standardization, including tokenization, stop word removal, and lemmatization. 

#### Methods
**Model Building**
Three classifiers were chosen: Logistic Regression, Random Forest, and Support Vector Machine (SVM). TF-IDF vectorizer was used for text vectorization due to its ability to consider word frequency and importance.

**Hyperparameters and Cross-Validation**
Tuning was performed for each classifier to enhance model performance. Different solvers, penalties, and C hyperparameters were tested in Logistic Regression. Random Forest’s max features and the number of estimators were optimized. SVM kernels and the penalty parameter were explored.

**Sentiment Analysis**
NLTK’s SentimentIntensityAnalyzer was employed to calculate sentiment scores for the review text and summary, with the 'compound' score being chosen for model training.

### Performance and Results
**Text Only**

| Model                     | ROC_AUC | Macro F1 | Accuracy | Confusion Matrix     |
|---------------------------|---------|----------|----------|----------------------|
| Logistic Regression       | 0.83076 | 0.83715  | 0.84872  | [Details of Confusion Matrix] |
| Random Forest Classifier  | 0.80116 | 0.80945  | 0.82508  | [Details of Confusion Matrix] |
| SVM                       | 0.57472 | 0.66113  | 0.53958  | [Details of Confusion Matrix] |

In the text-only models, Logistic Regression outperformed Random Forest and SVM across multiple metrics.

**Text with Sentiment Analysis**

| Model                     | ROC_AUC  | Macro F1 | Accuracy | Confusion Matrix     |
|---------------------------|----------|----------|----------|----------------------|
| Logistic Regression       | 0.81410  | 0.82594  | 0.81571  | [Details of Confusion Matrix] |
| Random Forest Classifier  | 0.81565  | 0.82451  | 0.83896  | [Details of Confusion Matrix] |

Including sentiment analysis improved model performance, albeit slightly, with Random Forest performing marginally better than Logistic Regression.

The sentiment-only analysis results showed that the F1 score was significantly lower than the text-only models.

### Insights and Future Work
While Logistic Regression performed well, more feature engineering on the sentiment analysis could be explored in the future. The SVM model took longer to converge, impacting its practicality. Feature engineering on the sentiment analysis output could improve model performance in future iterations.

