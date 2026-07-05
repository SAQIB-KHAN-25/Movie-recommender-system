#  Movie Recommender System

A **content-based Movie Recommendation System** built with **Python, Streamlit, and Scikit-learn** that recommends movies similar to a selected movie using **Cosine Similarity**. The application also fetches and displays movie posters dynamically using the **TMDB API**.

---

##  Highlights

-  Content-based movie recommendation using **Cosine Similarity**
-  Trained on the **TMDB 5000 Movies Dataset**
-  Displays movie posters using the **TMDB API**
-  Interactive web application built with **Streamlit**
-  Machine Learning pipeline for preprocessing, feature engineering, vectorization, and similarity computation
-  Fast recommendations using precomputed similarity scores

---


---

##  Tech Stack

| Category | Technologies |
|-----------|--------------|
| Language | Python |
| Web Framework | Streamlit |
| Machine Learning | Scikit-learn |
| Data Processing | Pandas, NumPy |
| Dataset | TMDB 5000 Movies Dataset |
| API | TMDB API |
| Model Storage | Pickle |

---

##  Project Structure

```text
Movie-recommender-system/
│
├── app.py                      # Streamlit application
├── main.py                     # Data preprocessing and model generation
├── requirements.txt
├── README.md
├── .gitignore
│
├── data/
│   ├── tmdb_5000_movies.csv
│   └── tmdb_5000_credits.csv
│
├── model/
│   ├── movie_dict.pkl
│   └── movies.pkl
│
└── notebooks/
    └── movie-recommender-system.ipynb
```

---

##  Recommendation Pipeline

```text
                TMDB Dataset
                     │
                     ▼
             Data Preprocessing
                     │
                     ▼
           Feature Engineering
                     │
                     ▼
          Combine Movie Features
                     │
                     ▼
            Text Vectorization
                     │
                     ▼
         Cosine Similarity Matrix
                     │
                     ▼
          Save Model (.pkl Files)
                     │
                     ▼
           Streamlit Web Application
                     │
                     ▼
          Recommend Similar Movies
                     │
                     ▼
        Fetch Posters from TMDB API
```

---

##  How It Works

1. Load the TMDB Movies and Credits datasets.
2. Merge the datasets using the movie title.
3. Perform data preprocessing and cleaning.
4. Extract important movie features:
   - Genres
   - Keywords
   - Cast
   - Crew
   - Overview
5. Combine these features into a single **tags** column.
6. Convert text into vectors using text vectorization.
7. Compute **Cosine Similarity** between all movies.
8. Store the processed data as Pickle files.
9. The Streamlit application loads the model files.
10. Recommend the Top 5 most similar movies.
11. Fetch movie posters dynamically using the TMDB API.

---

##  Installation

### Clone the Repository

```bash
git clone https://github.com/SAQIB-KHAN-25/Movie-recommender-system.git

cd Movie-recommender-system
```

### Create a Virtual Environment

```bash
python -m venv .venv
```

### Activate the Environment

**Windows**

```bash
.venv\Scripts\activate
```

**Linux / macOS**

```bash
source .venv/bin/activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run the Application

```bash
streamlit run app.py
```

---

##  Model Files

The application uses the following model files:

- `movie_dict.pkl`
- `movies.pkl`
- `similarity.pkl`

> **Note:**  
> `similarity.pkl` is **not included** in this repository because it exceeds GitHub's **100 MB file size limit**.
>
> To regenerate the file:
>
> 1. Open the notebook in the `notebooks/` directory.
> 2. Run all cells.
> 3. Move the generated `.pkl` files into the `model/` folder.

---

##  Features

- Content-based recommendation engine
- Fast similarity search
- Interactive Streamlit UI
- Movie poster integration using TMDB API
- Easy-to-understand recommendation pipeline
- Modular project structure
- Easy to extend with additional recommendation techniques

---


##  Dataset

This project uses the **TMDB 5000 Movies Dataset**, which contains movie metadata including:

- Title
- Genres
- Keywords
- Cast
- Crew
- Overview
- Popularity
- Vote Average

---
