Movie Recommendation System Using SVD
This code implements a movie recommendation system using Singular Value Decomposition (SVD). It takes a dataset containing user ratings for movies and uses SVD to calculate similarity between movies based on their ratings. The code then recommends the top N similar movies for a given movie.

Importing the basic libraries
The code begins by importing the necessary libraries: numpy and pandas. These libraries are commonly used for numerical computations and data manipulation.

Importing & Parsing the dataset as ratings and movies details
The code reads two input files: ratings.dat and movies.dat. The ratings.dat file contains user ratings for movies, while the movies.dat file contains details about the movies. The data is parsed and stored in two pandas DataFrames: ratingData and movieData.

Create the ratings matrix of shape (m×u)
Next, the code creates a ratings matrix of shape (m x u), where m is the maximum movie ID and u is the maximum user ID. The ratings from the ratingData DataFrame are used to populate the matrix. Each row represents a movie, and each column represents a user. The value at each cell represents the rating given by the user for that movie. The ratings matrix is stored in the variable ratingMatrix.

Subtract Mean off - Normalization
To normalize the ratings matrix, the mean rating is subtracted from each element. This normalization step helps in removing biases and scaling the ratings. The normalized matrix is stored in the variable normalizedMatrix.

Computing SVD
SVD (Singular Value Decomposition) is performed on the normalized matrix A. The matrix A is obtained by dividing the transposed normalized matrix by the square root of m - 1, where m is the number of movies. SVD decomposes the matrix A into three matrices: U, S, and V. U and V are orthogonal matrices, and S is a diagonal matrix containing singular values. These matrices are stored in the variables U, S, and V respectively.

Calculate cosine similarity, sort by most similar and return the top N
A function named similar is defined to calculate the cosine similarity between a given movie and all other movies. The function takes the ratingData, a movie_id, and top_n as input parameters. It calculates the cosine similarity between the ratings of the given movie and all other movies in the ratingData matrix. The similarity scores are sorted in descending order, and the indices of the top top_n similar movies are returned.

Select k principal components to represent the movies, a movie_id to find recommendations and print the top_n results
The code sets the values for k (the number of principal components) as 50, movie_id as 2 (representing a specific movie), and top_n as 5 (the number of recommendations to be generated).

The code then slices the matrix V.T to select the first k principal components. This selection represents the movies in a reduced dimensional space. The function similar is called with the sliced matrix, movie_id, and top_n to get the indexes of the most similar movies.

Finally, the code prints the recommendations for the given movie by retrieving the movie titles from the movieData DataFrame using the obtained indexes.

Overall, this code implements a movie recommendation system using SVD by calculating cosine similarity between movies based on their ratings and providing recommendations for a given movie.




