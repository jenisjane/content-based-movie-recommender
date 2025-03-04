# Content-Based Movie Recommendation System  

## Overview  
This project is a **Content-Based Recommendation System** for movies, utilizing **TF-IDF, Cosine Similarity, and FuzzyWuzzy**. The system suggests movies based on their genres and allows users to input movie titles (even with typos), returning a list of similar movies.  

## Dataset  
The dataset contains movie titles and genres. Missing values are handled, and genres are processed into numerical representations for similarity computations.  

## Key Features  
- ✅ **Genre-Based Recommendations:** Uses **TF-IDF (Term Frequency-Inverse Document Frequency)** to convert genres into numerical vectors.  
- ✅ **Cosine Similarity:** Computes similarity scores between movies based on genre representation.  
- ✅ **FuzzyWuzzy Matching:** Handles **misspelled movie titles** by calculating similarity using **Levenshtein Distance**.  
- ✅ **Exploratory Data Analysis (EDA):** Visualized genre distributions using **Matplotlib** and **Plotly**.  

## Methodology  

### 1. Data Preprocessing  
- Extracted movie titles and genres.  
- Handled missing values and cleaned formatting inconsistencies.  

### 2. Feature Engineering  
- Transformed movie genres into **TF-IDF vectors**.  
- Computed **Cosine Similarity** between movies to measure closeness.  

### 3. Recommendation Engine  
- Given a movie title, finds the most similar movies based on **genre similarity**.  
- Integrated **FuzzyWuzzy** to handle typos and improve search accuracy.  

## Usage  
- Input a movie title, and the system returns a list of similar movies.  
- Works even if the movie title has minor spelling errors.  
- Recommendations are based purely on **content (genres)**, without user ratings or collaborative filtering.  

## Technologies Used  
- 🛠 **Python** (Pandas, NumPy, Scikit-learn, FuzzyWuzzy, Matplotlib, Plotly)  

---
