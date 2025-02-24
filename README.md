
# Pratilipi Recommendation System

This project builds a recommendation system to predict the pratilipis (stories) that a user is likely to read based on their historical interactions. The system uses collaborative filtering, specifically **Singular Value Decomposition (SVD)**, to make predictions.


## Installation and Requirements

Before running the code, make sure you have the following Python libraries installed:

- pandas
- numpy
- scikit-learn
- surprise

You can install the dependencies using `pip`:

```bash

!pip install pandas numpy scikit-learn surprise

```
    
##  Dataset

The project uses two CSV files:

- **user_interaction.csv**: Contains user interaction data with pratilipis.
- **meta_data.csv**: Contains metadata about the pratilipis, such as author, category, and reading time.


## Code Walkthrough

## 1.Data Preprocessing

The first step involves cleaning and preprocessing the data:

1.1 Timestamps: The updated_at column is converted to datetime for easier manipulation.

1.2 Missing Values: Rows with missing published_at values in meta_data.csv are dropped.

1.3 Outliers: Outliers in the read_percent column (values greater than 100) are removed to ensure the data is within a valid range.
## 2.Feature Engineering
We extract meaningful features from the data:

2.1 User Features: We calculate:

2.1.1 Total number of pratilipis read by the user.

2.1.2 Average percentage of pratilipis read by the user.

2.2 Pratilipi Features: We extract:

2.2.1 The category of pratilipis (note that pratilipis can belong to multiple categories).

2.2.2 The reading time for each pratilipi.


## 3.Train-Test Split
We split the data into training (75%) and testing (25%) based on the updated_at column. This ensures that we do not have data leakage from future interactions into the training set.

## 4.Collaborative Filtering Model (SVD)
We use the SVD model from the Surprise library to make predictions:

4.1 SVD decomposes the user-item interaction matrix into latent factors, capturing the underlying patterns in user preferences and pratilipi characteristics.

4.2 The model is trained on the training set, and predictions are made for the test set.

## 5.Evaluation
We evaluate the model using Root Mean Squared Error (RMSE), which measures the difference between predicted and actual values. The model's performance is assessed based on the RMSE score, which helps us understand the accuracy of the predictions.

## 6.Top-5 Recommendations
For each user, we generate a list of the top 5 pratilipis they are most likely to read based on the model's predictions. The top recommendations are sorted in descending order of predicted reading percentage.
## How to Run

 1.Open the Pratilipi_Recommendation_System.ipynb notebook in Google Colab.

2.Ensure that all the necessary libraries are installed by running the code cells for the libraries.

3.Execute each cell in the notebook sequentially. The code will:

3.1 Load the dataset from Google Drive.

3.2 Preprocess the data.

3.3 Train the recommendation model using Singular Value Decomposition (SVD).

3.4 Provide top 5 pratilipi recommendations for each user based on their reading history.

3.5 The final output will show the RMSE score and the predicted pratilipis for each user.

DriveLink:
https://drive.google.com/drive/folders/1VOgKR-nGTtvQfzlj_L8wq1_zzNLvLvng?usp=drive_link

## Model Explanation
We used Singular Value Decomposition (SVD) as the collaborative filtering technique for the recommendation system. SVD works by decomposing the user-item interaction matrix into three matrices that represent the relationships between users and pratilipis. By learning these latent factors, SVD makes predictions about user interactions with pratilipis they have not yet read.

## Why SVD?
SVD is a widely-used collaborative filtering technique that:

1.Reduces the dimensionality of the data, making it more computationally efficient.

2.Captures latent relationships between users and pratilipis, improving the quality of predictions.

3.Works well for large-scale recommendation systems, where users and items can be numerous.

## Results
1.The model is evaluated using RMSE (Root Mean Squared Error), with the final RMSE score being 22.37.

2.The system predicts the top 5 pratilipis that each user is likely to read, based on their historical behavior.

## Sample Output:
RMSE: 22.37

User 5506791966280495: [(1377786219672726, 100)]

User 5506791968624247: [(1377786223936248, 100), (1377786222606858, 100), (1377786224655297, 100), (1377786228039628, 100), (1377786222825840, 100)]

User 5506791987341146: [(1377786227792278, 100), (1377786227820041, 100), (1377786221889554, 100), (1377786222685592, 100), (1377786222053149, 100)]

User 5506791973485874: [(1377786221237656, 100), (1377786221321675, 100)]

User 5506791983111623: [(1377786220907572, 100), (1377786221024320, 100)]

