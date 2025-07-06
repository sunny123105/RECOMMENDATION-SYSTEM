COMPANY : CODTECH IT SOLUTIONS

NAME : PATEL SUNNY KANAKKUMAR

INTERN ID : CT04DG881

DOMAIN : MACHINE LEARNING

DURATION : 4 WEEK

MENTOR : NEELA SANTOSH

DESCRIPTION OF TASK :This project implements a User-Based Collaborative Filtering recommendation engine using cosine similarity to find similar users and suggest items based on shared preferences. Collaborative filtering is a widely-used method in recommendation systems across platforms like Netflix, Amazon, and Spotify. It provides personalized recommendations by analyzing user behavior, without requiring any item-specific metadata.

  Objective
The main goal is to recommend top-rated items to a user by identifying other users with similar rating patterns. The algorithm is designed to:

Compute similarities between users.

Weight the ratings of similar users.

Recommend items the target user has not yet rated.

This method is particularly useful when item metadata is unavailable or unreliable, and we rely solely on user-item interactions (ratings).

  Dataset Description
  
The dataset used is a CSV file named realistic_ratings.csv, which contains the following columns:

userId – Unique identifier for each user.

itemId – Unique identifier for each item (e.g., product, movie).

rating – Rating given by a user to an item.

This user-item interaction data is used to build a user-item matrix for computing similarities and generating recommendations.

  Workflow
  
1. Load and Prepare the Data
df = pd.read_csv("realistic_ratings.csv")
We create a user-item matrix where each row represents a user and each column represents an item. The cells contain rating values (0 if unrated).

user_item_matrix = df.pivot_table(index='userId', columns='itemId', values='rating').fillna(0)

2. Compute User-User Similarity
Using cosine_similarity from scikit-learn, we calculate how similar each user is to others based on their rating vectors.

user_similarity = cosine_similarity(user_item_matrix)
similarity_df = pd.DataFrame(user_similarity, index=user_item_matrix.index, columns=user_item_matrix.index)

3. Recommendation Function
We define a function recommend_items(user_id, num_recommendations) which performs:

Fetching top similar users (excluding the user themself).

Weighting their ratings by similarity scores.

Removing items already rated by the user.

Returning the top N highest-scoring items as recommendations.

recommend_items(user_id=1, num_recommendations=3)

OUTPUT:![Image](https://github.com/user-attachments/assets/a7f5d551-e240-4938-aa9e-c638072b9329)
