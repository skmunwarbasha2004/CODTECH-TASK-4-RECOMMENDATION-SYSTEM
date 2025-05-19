# CODTECH-TASK-4-RECOMMENDATION-SYSTEM

COMPANY : CODTECH IT SOLUTION

NAME : SHAIK MUNWAR BASHA

INTERN ID : CT06DM431

DOMAIN : Machine Learning

MENTOR : Neela Santosh

DURATION : 6 weeks


Building a Movie Recommendation System Using Collaborative Filtering

The code builds a movie recommendation system using collaborative filtering with the MovieLens dataset (movies.csv and ratings.csv). It processes the data, applies collaborative filtering via nearest neighbors on a sparse matrix, and provides movie recommendations through a Gradio interface. Here's a breakdown of the process, concepts, and outputs.<br/>

A recommendation system predicts items (e.g., movies) a user might like based on their past behavior or preferences. Collaborative filtering, used here, leverages user-item interactions (ratings) to find patterns. It assumes that users who agreed in the past (e.g., rated similar movies highly) will agree in the future, recommending movies based on user similarity or item similarity.<br/>

Matrix factorization is a technique often used in recommendation systems to decompose a user-item rating matrix into lower-dimensional matrices representing latent factors (e.g., user preferences and item characteristics). F. These latent factors capture hidden patterns (e.g., a user’s preference for action movies). While this code doesn’t explicitly use matrix factorization, it uses a nearest neighbors approach on a sparse matrix, which is an alternative collaborative filtering method. Matrix factorization methods like Singular Value Decomposition (SVD) or Alternating Least Squares (ALS) could be applied to this dataset for better scalability and accuracy.<br/>
Procedure and Process<br/>

1.Data Loading and Preparation:<br/>

The movies.csv dataset contains movie metadata (e.g., movieId, title, genres), and ratings.csv contains user ratings (e.g., userId, movieId, rating).<br/>
A pivot table (final_dataset) is created with movies as rows, users as columns, and ratings as values, resulting in a sparse matrix (9724 movies × 610 users). Missing ratings are filled with 0.<br/>


2.Noise Reduction:<br/>

Movies with fewer than 10 user votes and users with fewer than 50 movie votes are filtered out to reduce noise, leaving a matrix of 2121 movies × 378 users.<br/>
This step ensures the model focuses on movies and users with sufficient data, improving recommendation quality.<br/>


3.Sparse Matrix Conversion:<br/>

The matrix is converted to a compressed sparse row (CSR) format using scipy.sparse.csr_matrix to handle the sparsity efficiently (sparsity ~80%, meaning 80% of entries are 0).
Sparse matrices reduce memory usage and speed up computations.<br/>


4.Collaborative Filtering with Nearest Neighbors:<br/>

A NearestNeighbors model from sklearn is used with cosine similarity to find movies similar to a given movie.<br/>
Cosine similarity measures the angle between two movie rating vectors, identifying movies with similar user rating patterns.<br/>
The model is trained on the CSR matrix (csr_data).<br/>


5.Recommendation Function:<br/>

The get_recommendation function takes a movie name, finds its movieId, and uses the KNN model to identify the 10 most similar movies based on rating patterns.<br/>
It returns a DataFrame with recommended movie titles and their similarity distances (lower distance = more similar).<br/>


6.Gradio Interface:<br/>

A Gradio UI (gr.Interface) allows users to input a movie name and receive recommendations as text output.<br/>



Output
![Image](https://github.com/user-attachments/assets/f8fd2fe0-e9d4-4b9a-baae-0b8d0a5d389d)

These are movies similar to "Avatar" based on user rating patterns, with distances indicating similarity (e.g., "Up" is the most similar with a distance of 0.398180).<br/>

