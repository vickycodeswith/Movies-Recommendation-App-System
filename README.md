# 🎬 Movies Recommendation App System

A **content-based movie recommendation system** built with Python and Streamlit.  
The application recommends movies similar to a selected movie by analyzing movie metadata and calculating **cosine similarity** between feature vectors.

---

## 🚀 Live Demo

> Add your deployed Hugging Face Spaces link here:

  [![Live Demo](https://img.shields.io/badge/Live%20Demo-Hugging%20Face-yellow?style=for-the-badge&logo=huggingface)](https://huggingface.co/spaces/Vicky8021/movies-recommensation-system)

---

## 📌 Project Overview

Finding a movie to watch can be difficult when thousands of options are available. This project solves that problem by suggesting related movies based on their content.

The recommendation engine uses information such as:

- Movie overview
- Genres
- Keywords
- Cast
- Crew
- Director

These features are combined into a single text representation and converted into numerical vectors. Cosine similarity is then used to find the movies that are most similar to the movie selected by the user.

---

## ✨ Features

- Search and select a movie from the available movie list
- Get multiple similar movie recommendations
- Content-based recommendation approach
- Movie posters fetched using the TMDB API
- Simple and interactive Streamlit interface
- Fast recommendations using precomputed similarity scores
- Deployable on Hugging Face Spaces or Streamlit Community Cloud

---

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| Data Processing | Pandas, NumPy |
| Machine Learning | Scikit-learn |
| Recommendation Technique | Content-Based Filtering |
| Similarity Measure | Cosine Similarity |
| Web Application | Streamlit |
| External API | TMDB API |
| Deployment | Hugging Face Spaces |
| Development Tools | Jupyter Notebook, Git, GitHub |

---

## 📂 Project Structure

```text
Movies-Recommendation-App-System/
│
├── app.py                     # Streamlit web application
├── movie recomender.ipynb     # Data preprocessing and model development
├── movie_dict.pkl             # Processed movie data
├── similarity.pkl             # Precomputed similarity matrix
├── tmdb_5000_movies.csv       # Movie dataset
├── tmdb_5000_credits.csv      # Cast and crew dataset
├── .gitignore                 # Ignored files and folders
├── .gitattributes             # Git attributes configuration
└── README.md                  # Project documentation
```

---

## ⚙️ How the Recommendation System Works

### 1. Data Collection

The project uses the following TMDB datasets:

- `tmdb_5000_movies.csv`
- `tmdb_5000_credits.csv`

### 2. Data Preprocessing

The datasets are merged and useful features are selected. Missing values and duplicate records are handled before model creation.

### 3. Feature Engineering

Important text features such as genres, keywords, cast, crew, and movie overview are cleaned and combined into a new feature called `tags`.

### 4. Text Vectorization

The tags are converted into vectors using `CountVectorizer`.

### 5. Similarity Calculation

Cosine similarity is calculated between movie vectors.

\[
\text{Cosine Similarity} =
\frac{A \cdot B}{\|A\| \|B\|}
\]

### 6. Recommendation

When a user selects a movie, the system:

1. Finds the movie index
2. Retrieves its similarity scores
3. Sorts the scores in descending order
4. Returns the most similar movies
5. Fetches and displays movie posters using the TMDB API

---

## 💻 Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/vickycodeswith/Movies-Recommendation-App-System.git
cd Movies-Recommendation-App-System
```

### 2. Create a Virtual Environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

#### macOS/Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Required Libraries

```bash
pip install streamlit pandas numpy scikit-learn requests
```

You can also create a `requirements.txt` file containing:

```text
streamlit
pandas
numpy
scikit-learn
requests
```

Then install all dependencies using:

```bash
pip install -r requirements.txt
```

### 4. Add the TMDB API Key

Create an API key from the TMDB website and store it securely.

A recommended approach is to create the following file:

```text
.streamlit/secrets.toml
```

Add:

```toml
TMDB_API_KEY = "your_tmdb_api_key"
```

Then access it inside `app.py` using:

```python
import streamlit as st

api_key = st.secrets["TMDB_API_KEY"]
```

> Never upload your actual API key to GitHub.

### 5. Run the Application

```bash
streamlit run app.py
```

Open the local URL shown in the terminal, usually:

```text
http://localhost:8501
```

---

## 🧠 Sample Recommendation Function

```python
def recommend(movie):
    movie_index = movies[movies["title"] == movie].index[0]
    distances = similarity[movie_index]

    movie_list = sorted(
        list(enumerate(distances)),
        reverse=True,
        key=lambda item: item[1]
    )[1:6]

    recommended_movies = []

    for index, score in movie_list:
        recommended_movies.append(movies.iloc[index]["title"])

    return recommended_movies
```

---

## 📊 Dataset Information

The project uses the **TMDB 5000 Movie Dataset**, containing approximately:

- 4,800 movie records
- Movie titles and overviews
- Genres and keywords
- Cast and crew information
- Budget, revenue, popularity, and ratings

---

## 📸 Application Screenshots

<img width="1470" height="956" alt="image" src="https://github.com/user-attachments/assets/4aeda692-86fb-4035-a516-88842660eea1" />
<img width="1470" height="956" alt="image" src="https://github.com/user-attachments/assets/39a82d13-2452-4553-ac6f-591d13efbff6" />
<img width="1470" height="956" alt="image" src="https://github.com/user-attachments/assets/6c73ab51-20f5-4f41-b167-846a15c513f4" />

```

---

## 🔐 Security Recommendation

Do not write the TMDB API key directly inside `app.py`.

Use one of the following:

- Streamlit Secrets
- Environment variables
- Hugging Face repository secrets

Add sensitive files to `.gitignore`:

```text
.env
.streamlit/secrets.toml
__pycache__/
venv/
```

---

## 🔮 Future Improvements

- Add collaborative filtering
- Build a hybrid recommendation model
- Include movie trailers
- Add filters for genre, language, year, and rating
- Allow users to create watchlists
- Add user login and personalized recommendations
- Improve recommendations using transformer embeddings
- Add movie details, ratings, and release dates
- Deploy a lightweight API using FastAPI

---

## 🤝 Contributing

Contributions are welcome.

1. Fork this repository
2. Create a new branch

```bash
git checkout -b feature/new-feature
```

3. Commit your changes

```bash
git commit -m "Add new feature"
```

4. Push the branch

```bash
git push origin feature/new-feature
```

5. Open a Pull Request

---

## 👨‍💻 Author

**Nitesh Kumar Yadav**

- GitHub: [@vickycodeswith](https://github.com/vickycodeswith)
- Repository: [Movies-Recommendation-App-System](https://github.com/vickycodeswith/Movies-Recommendation-App-System)

---

## ⭐ Support

If you found this project useful, please give the repository a **star**.

---

## 📄 License

This project is created for learning and portfolio purposes.  
You may add an MIT License if you want others to reuse and contribute to the project.
