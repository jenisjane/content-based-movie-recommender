# Content-Based Movie Recommendation System
A movie recommendation system using TF-IDF, Cosine Similarity, and FuzzyWuzzy to provide personalized suggestions.

## Overview
This project is a **Content-Based Movie Recommendation System** that suggests movies based on genre similarity. It utilizes **TF-IDF, Cosine Similarity, and FuzzyWuzzy** to generate recommendations. The system processes movie titles, genres, and applies similarity measures to find the most relevant suggestions for a user.

## Features
- Extracts movie **titles and release years** from the dataset.
- Handles missing values and formatting inconsistencies.
- **Analyzes genre distribution** using Matplotlib and Plotly.
- Converts genres into **numerical vectors** using TF-IDF.
- Computes **Cosine Similarity** between movies based on genre.
- Uses **FuzzyWuzzy (Levenshtein Distance)** to match user input with the closest movie title.
- Provides **personalized movie recommendations** based on content similarity.

## Dataset
The dataset contains movie metadata, including **title, release year, and genres**. The genres are converted into numerical representations to compute similarity between movies.

## Installation
Ensure you have Python installed, then install the required libraries:

```bash
pip install pandas scikit-learn fuzzywuzzy numpy matplotlib plotly
```

## Usage
1. **Load the dataset**:
   ```python
   import pandas as pd
   dataset = pd.read_csv("movies.csv")
   ```

2. **Check for missing values**:
   ```python
   print(dataset.isnull().sum())
   ```

3. **Extract title and year**:
   ```python
   dataset['year'] = pd.to_numeric(dataset['year'], errors='coerce').astype('Int64')
   ```

4. **Visualize genre distribution**:
   ```python
   import matplotlib.pyplot as plt
   dataset['genres'].value_counts().plot(kind='bar')
   plt.show()
   ```

5. **Compute TF-IDF for genres**:
   ```python
   from sklearn.feature_extraction.text import TfidfVectorizer
   tfidf = TfidfVectorizer()
   tfidf_matrix = tfidf.fit_transform(dataset['genres'])
   ```

6. **Compute similarity using Cosine Similarity**:
   ```python
   from sklearn.metrics.pairwise import cosine_similarity
   similarity = cosine_similarity(tfidf_matrix)
   ```

7. **Handle user input using FuzzyWuzzy**:
   ```python
   from fuzzywuzzy import process
   user_input = "Avengers"
   closest_match = process.extractOne(user_input, dataset['title'])[0]
   print("Did you mean:", closest_match)
   ```

8. **Generate movie recommendations**:
   ```python
   def recommend_movie(movie_title):
       index = dataset[dataset['title'] == movie_title].index[0]
       similar_movies = list(enumerate(similarity[index]))
       similar_movies = sorted(similar_movies, key=lambda x: x[1], reverse=True)[1:6]
       recommendations = [dataset.iloc[i[0]]['title'] for i in similar_movies]
       return recommendations
   ```
   ```python
   print(recommend_movie("The Dark Knight"))
   ```

## Project Structure
```
📂 content-based-movie-recommender
 ├── 📄 movies.csv                # Dataset
 ├── 📄 content_based_recommender.ipynb  # Jupyter Notebook
 ├── 📄 README.md                 # Project documentation

```
