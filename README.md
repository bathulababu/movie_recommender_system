# movie_recommender_system

This project implements a movie recommendation system using a content-based filtering approach. It utilizes a dataset of movies to provide recommendations based on movie overviews and genres.

## Project Description

The goal of this project is to develop a system that can suggest movies to users based on their preferences. By analyzing the textual descriptions (overview) and genres of movies, the system identifies similarities between them and recommends movies that are likely to be of interest to the user.

## Data

The dataset used in this project (`dataset.csv`) contains information about various movies, including:

-   `id`: Unique identifier for each movie.
-   `title`: Title of the movie.
-   `genre`: Genre(s) of the movie.
-   `original_language`: Original language of the movie.
-   `overview`: A brief summary or description of the movie.
-   `popularity`: A measure of the movie's popularity.
-   `release_date`: Date when the movie was released.
-   `vote_average`: Average rating given to the movie.
-   `vote_count`: Number of votes received by the movie.

## Methodology

1.  **Data Loading and Exploration**:
    -   The dataset is loaded using pandas.
    -   Initial exploration involves displaying the first few rows, descriptive statistics, data types, and checking for missing values.
2.  **Feature Selection**:
    -   The project focuses on the `id`, `title`, `overview`, and `genre` columns for the recommendation system.
3.  **Feature Engineering**:
    -   A new feature `tags` is created by combining the `overview` and `genre` columns. This consolidated text is used to represent each movie.
4.  **Text Vectorization**:
    -   The `CountVectorizer` from scikit-learn is used to convert the text in the `tags` column into a matrix of token counts. This helps in quantifying the textual data.
    -   Stop words are removed, and the maximum number of features is limited to 10,000 to reduce dimensionality.
5.  **Similarity Calculation**:
    -   Cosine similarity is computed between the vectorized representations of the movies. This similarity matrix is used to find movies that are similar to each other.
6.  **Movie Recommendation**:
    -   A function `recommand(movie)` is defined to take a movie title as input and return the top 5 most similar movies.
    -   The function works by:
        -   Finding the index of the input movie.
        -   Retrieving the similarity scores for that movie.
        -   Sorting the movies based on their similarity scores.
        -   Returning the titles of the top 5 movies.
7.  **Model Persistence**:
    -   The processed data (`new_data`) and the similarity matrix are saved using pickle for future use. This allows the recommendation system to be deployed without retraining the model.

## Libraries Used

-   pandas
-   scikit-learn (CountVectorizer, cosine_similarity)
-   pickle

## Usage

To use the movie recommendation system:

1.  Ensure you have the required libraries installed (`pandas`, `scikit-learn`).
2.  Place the `dataset.csv` file in the same directory as the script.
3.  Run the script.  
4.  Call the `recommand(movie_title)` function with the title of a movie to get recommendations.

## Files

-   `dataset.csv`: The movie dataset.
-   `Movies.ipynb`: Jupyter Notebook containing the code for the movie recommendation system.
-   `movies_list.pkl`: Pickle file containing the processed movie data.
-   `similarity.pkl`: Pickle file containing the cosine similarity matrix.

## Example

```python
recommand("Iron Man")
