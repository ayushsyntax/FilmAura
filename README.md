# FilmAura
FilmAura: A smart, AI-powered movie and series recommendation system that understands your taste and suggests perfectly matched films.


Here’s a more readable version of your document, with improved formatting and structure for clarity:

# 🎬 Movie Recommendation System — Cleaned Dataset

A production-ready, cleaned, and feature-engineered dataset for building movie recommendation systems. This dataset is derived from raw TMDB metadata (~1.2 million movies) and transformed into a **modeling-ready format** with intelligent imputation, robust features, and optimized performance.

📁 **Final Output:** `movieclean.parquet`

---

## 📁 Dataset Overview

- **Source**: [TMDB Movies Metadata](https://www.kaggle.com/tmdb/tmdb-movie-metadata)
- **Rows**: Approximately 1.2 million movies
- **Cleaned & Processed**: Yes
- **Format**: Parquet (fast, compressed, preserves data types)
- **File**: `movieclean.parquet`

---

## ✅ Key Features

| Column              | Description                                                  |
|---------------------|--------------------------------------------------------------|
| `id`                | Unique movie ID                                             |
| `title`             | Movie title                                                |
| `overview`          | Plot summary                                               |
| `genres`            | Pipe-separated genres (e.g., `Action|Adventure`)          |
| `vote_average`      | User rating (0–10)                                        |
| `vote_count`        | Number of votes                                            |
| `popularity`        | TMDB popularity score                                      |
| `release_date`      | Release date                                              |
| `original_language` | Language code (e.g., `en`)                                 |
| `adult`             | Indicates whether the content is adult                     |
| `weighted_rating`   | IMDb-style balanced score (vote average + vote count)     |
| `combined_text`     | Concatenation of `title` and `overview` for recommendations |
| `genre_count`       | Number of genres assigned                                   |
| `movie_age`         | Years since release                                        |
| `era`               | Decade bucket (e.g., 1980, 1990)                          |
| `is_cold_start`     | Flag for movies with little data (low votes, no overview) |

---

## 🛠️ How It Was Built

1. **Data Cleaning**  
   - Removed irrelevant columns (e.g., `homepage`, `tagline`, `keywords`).  
   - Parsed JSON-like strings (e.g., `genres`) into usable lists.  
   - Fixed data types for memory efficiency (`int32`, `float32`, `string`, `category`).  

2. **Missing Data Handling**  
   - Filled `overview` with `"No description available"`.  
   - Imputed `genres` using **keyword-based matching** on `overview` as a robust fallback.  

3. **Feature Engineering**  
   - Added `weighted_rating` for balanced quality scoring.  
   - Created `combined_text` for content-based filtering.  
   - Engineered contextual features: `movie_age`, `genre_count`, `is_cold_start`, etc.  

4. **Optimization**  
   - Reduced memory usage by over 40% with efficient data types.  
   - Saved the final dataset in **Parquet format** for fast loading.  

---

## 💾 How to Use

```python
import pandas as pd

# Load the cleaned dataset
df = pd.read_parquet('movieclean.parquet')

print(df.shape)
print(df.columns)
```

