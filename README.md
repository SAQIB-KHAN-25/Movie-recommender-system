# Movie Recommender System

A **content-based Movie Recommendation System** built with **Python, Streamlit, Pandas, NumPy, and Scikit-learn**.

The system recommends movies similar to a movie selected by the user using **Cosine Similarity**. It also retrieves and displays movie posters dynamically using the **TMDB API**.

---

## Features

* 🎬 Content-based movie recommendation
* 🔍 Search and select movies from the available dataset
* 🤖 Cosine Similarity-based recommendations
* ⭐ Top 5 similar movie recommendations
* 🖼️ Dynamic movie poster retrieval using the TMDB API
* 🌐 Interactive Streamlit web application
* ⚡ Fast recommendations using a precomputed similarity matrix
* 📊 Feature engineering using movie metadata
* 🔐 Secure API-key management using Streamlit Secrets

---

## Tech Stack

| Category             | Technologies             |
| -------------------- | ------------------------ |
| Programming Language | Python                   |
| Web Framework        | Streamlit                |
| Machine Learning     | Scikit-learn             |
| Data Processing      | Pandas, NumPy            |
| Dataset              | TMDB 5000 Movies Dataset |
| API                  | TMDB API                 |
| Model Storage        | Pickle                   |
| Development          | Jupyter Notebook         |

---

## Project Structure

```text
Movie-recommender-system/
│
├── app.py                          # Streamlit application
├── main.py                         # Starter template
├── requirements.txt                # Python dependencies
├── README.md                       # Project documentation
├── .gitignore                      # Git ignore rules
│
├── data/
│   ├── tmdb_5000_movies.csv        # Movie metadata
│   └── tmdb_5000_credits.csv       # Cast and crew information
│
├── model/
│   ├── movie_dict.pkl              # Processed movie data
│   ├── movies.pkl                  # Movie dataframe used by the app
│   └── similarity.pkl              # Precomputed similarity matrix
│
├── notebooks/
│   └── movie-recommender-system.ipynb
│                                     # Data preprocessing and model development
│
└── .streamlit/
    └── secrets.toml                # Local TMDB API key - not committed
```

> **Important:** `main.py` is currently a starter template. The actual data preprocessing, feature engineering, and model-development workflow is contained in `notebooks/movie-recommender-system.ipynb`.

---

## Recommendation Pipeline

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
             Save Model Files
                      │
                      ▼
            Streamlit Application
                      │
                      ▼
             Select a Movie
                      │
                      ▼
           Find Similar Movies
                      │
                      ▼
              Top 5 Results
                      │
                      ▼
             Fetch Movie Posters
                from TMDB API
```

---

## How It Works

The recommendation model is developed using:

```text
notebooks/movie-recommender-system.ipynb
```

### 1. Load the Dataset

The project uses the **TMDB 5000 Movies Dataset**, consisting of movie metadata and credits information.

The datasets are stored in:

```text
data/tmdb_5000_movies.csv
data/tmdb_5000_credits.csv
```

### 2. Data Preprocessing

The movie and credits datasets are loaded and processed.

The datasets contain information such as:

* Movie title
* Genres
* Keywords
* Cast
* Crew
* Overview
* Popularity
* Vote average

### 3. Feature Engineering

Relevant movie features are extracted and combined to represent each movie.

The recommendation system uses information such as:

* Genres
* Keywords
* Cast
* Crew
* Overview

These features are combined into text-based movie information.

### 4. Text Vectorization

The combined movie features are converted into numerical vectors using text vectorization techniques.

This allows the system to mathematically compare movies based on their content.

### 5. Cosine Similarity

Cosine Similarity is calculated between the movie vectors.

Movies with higher similarity scores are considered more similar.

### 6. Save Model Files

The processed movie data and similarity matrix are stored as Pickle files inside:

```text
model/
```

The Streamlit application uses:

```text
model/movies.pkl
model/similarity.pkl
```

### 7. Generate Recommendations

When a user selects a movie:

1. The selected movie is located in the movie dataset.
2. Its similarity scores are retrieved.
3. Movies are sorted according to similarity.
4. The most similar movies are selected.
5. The Top 5 recommendations are displayed.

### 8. Fetch Movie Posters

The application uses the **TMDB API** to retrieve poster information for recommended movies.

The posters are then displayed in the Streamlit interface.

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/SAQIB-KHAN-25/Movie-recommender-system.git
```

Move into the project directory:

```bash
cd Movie-recommender-system
```

---

### 2. Create a Virtual Environment

Windows:

```powershell
python -m venv .venv
```

Linux/macOS:

```bash
python3 -m venv .venv
```

---

### 3. Activate the Virtual Environment

#### Windows PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

#### Windows Command Prompt

```cmd
.venv\Scripts\activate
```

#### Linux/macOS

```bash
source .venv/bin/activate
```

---

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## TMDB API Configuration

The application uses the **TMDB API** to retrieve movie posters.

The API key should **not** be written directly inside `app.py`.

Instead, the project uses Streamlit Secrets.

### Create the Secrets File

Create the following file:

```text
.streamlit/secrets.toml
```

Add:

```toml
TMDB_API_KEY = "YOUR_TMDB_API_KEY"
```

The application accesses the key using:

```python
st.secrets["TMDB_API_KEY"]
```

### Security

Do **not** commit:

```text
.streamlit/secrets.toml
```

to GitHub.

The `.gitignore` file should contain:

```text
.streamlit/secrets.toml
```

If an API key has previously been exposed publicly, it should be revoked or rotated and replaced with a new key.

---

## Running the Application

Make sure you are in the project root directory:

```text
Movie-recommender-system/
```

Activate the virtual environment and run:

```bash
python -m streamlit run app.py
```

Streamlit will provide a local URL where you can open the application in your browser.

---

## Model Files

The application uses the following model files:

```text
model/
├── movie_dict.pkl
├── movies.pkl
└── similarity.pkl
```

The current Streamlit application specifically loads:

```text
model/movies.pkl
model/similarity.pkl
```

These files must be available in the `model/` directory for the application to run correctly.

---

## Regenerating the Model

The model-development workflow is located in:

```text
notebooks/movie-recommender-system.ipynb
```

### Steps

1. Open the notebook.
2. Make sure the datasets are available in the `data/` directory.
3. Run the notebook cells in order.
4. Perform the preprocessing and feature-engineering steps.
5. Generate the movie feature vectors.
6. Calculate the Cosine Similarity matrix.
7. Save the generated model files inside the `model/` directory.
8. Verify that the required files exist:

```text
model/movies.pkl
model/similarity.pkl
```

9. Start the Streamlit application:

```bash
python -m streamlit run app.py
```

> `main.py` is currently a starter template and is **not** the model-generation script.

---

## Dataset

This project uses the **TMDB 5000 Movies Dataset**.

The dataset files included in the project are:

```text
data/tmdb_5000_movies.csv
data/tmdb_5000_credits.csv
```

The dataset contains movie-related information including:

* Movie titles
* Genres
* Keywords
* Cast
* Crew
* Overview
* Popularity
* Vote average
* Vote count

---

## Example Recommendation Flow

Suppose the user selects:

```text
Avatar
```

The recommendation system:

```text
Avatar
   │
   ▼
Find Avatar in movies.pkl
   │
   ▼
Retrieve similarity scores
   │
   ▼
Sort movies by similarity
   │
   ▼
Select Top 5 similar movies
   │
   ▼
Fetch posters using TMDB API
   │
   ▼
Display recommendations
```

---

## Application Interface

The Streamlit application provides:

* Movie selection dropdown
* Recommendation button
* Five recommended movies
* Movie posters for the recommendations

---

## Important Notes

* Run the application from the **project root directory**.
* Make sure the virtual environment is activated.
* Install dependencies using `requirements.txt`.
* Keep `movies.pkl` and `similarity.pkl` inside the `model/` directory.
* Keep datasets inside the `data/` directory.
* Keep the TMDB API key inside `.streamlit/secrets.toml`.
* Do not commit `.streamlit/secrets.toml`.
* Do not commit the `.venv/` directory.
* `main.py` is currently a starter template.
* Use `notebooks/movie-recommender-system.ipynb` for the model-development workflow.

---

## Requirements

The main dependencies are:

```text
streamlit
requests
pandas
```

Additional machine-learning and data-processing dependencies required by the notebook should be listed in:

```text
requirements.txt
```

Install everything with:

```bash
pip install -r requirements.txt
```

---

## Project Workflow

```text
Dataset
   │
   ▼
Jupyter Notebook
   │
   ├── Data Cleaning
   ├── Feature Engineering
   ├── Text Processing
   ├── Vectorization
   └── Cosine Similarity
          │
          ▼
      Model Files
          │
          ▼
   Streamlit Application
          │
          ▼
    Movie Selection
          │
          ▼
  Similarity Calculation
          │
          ▼
 Top 5 Movie Recommendations
          │
          ▼
    TMDB Movie Posters
```

---

## Future Improvements

Possible future improvements include:

* Add movie search functionality
* Add movie ratings
* Add movie descriptions
* Improve recommendation quality
* Add genre-based filtering
* Add popularity-based filtering
* Add user-based recommendations
* Deploy the application online
* Improve the Streamlit interface
* Add recommendation explanations

---

## Author

**Saqib Ahmed Khan**

GitHub:

[SAQIB-KHAN-25](https://github.com/SAQIB-KHAN-25)

---

## License

This project is intended for educational and portfolio purposes.
