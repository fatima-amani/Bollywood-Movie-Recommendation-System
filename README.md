# 🎬 Bollywood Movie Recommender System 🍿

A content-based Bollywood movie recommendation system that suggests similar Hindi films based on user preferences. Built using Python, Pandas, Scikit-learn, and Streamlit.

> 🌎 **Looking for international movie recommendations?** Check out our general Movie Recommendation System: [https://github.com/fatima-amani/Movie-Recommender.git](https://github.com/fatima-amani/Movie-Recommender.git)

## ✨ Features

- 🔍 Recommends 6 most similar Bollywood movies based on a selected title
- 📊 Uses movie metadata (genres, keywords, cast, crew, overview) for recommendations
- 🌐 Interactive Streamlit web interface for easy interaction
- 🇮🇳 Specialized for Hindi cinema enthusiasts

## 🛠️ Technologies Used

- **Python** 🐍 - Core programming language
- **Pandas** 🐼 - For data manipulation and preprocessing
- **Scikit-learn** 📊 - For TF-IDF vectorization and cosine similarity calculations
- **Streamlit** 📱 - For interactive web application development
- **IMDB dataset** 🎥 - For comprehensive Bollywood movie data (1951-2023)

## 📁 Files Structure

```
Bollywood-Movie-Recommender/
├── app.py                                 # Streamlit application with UI
├── bollywood_movie_recommender_model.ipynb # Jupyter notebook with model development
└── IMDB-Movie-Dataset(2023-1951).csv      # IMDB Bollywood movie dataset
```

## 🎞️ Dataset

The system uses the IMDB Bollywood Movie Dataset (1951-2023) which contains:
- Decades of Hindi cinema with detailed metadata
- Features like genres, cast information, director, overview, etc.
- Comprehensive coverage of classic and contemporary Bollywood films

## ⚙️ How It Works

1. Data is preprocessed in the Jupyter notebook and important features are combined
2. Text data is vectorized using TF-IDF (Term Frequency-Inverse Document Frequency)
3. Cosine similarity between movies is calculated to find similarities
4. Results are exported as pickle files for the app to use
5. Streamlit app imports these pickle files to make real-time recommendations

## 🚀 Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/fatima-amani/Bollywood-Movie-Recommendation-System.git
   cd Bollywood-Movie-Recommendation-System
   ```

2. **Install required packages**:
   ```bash
   pip install streamlit pandas scikit-learn requests
   ```

3. **Generate model files**:
   - Run the `bollywood_movie_recommender_model.ipynb` notebook to generate the pickle files
   - Ensure the necessary pickle files are created in the project root

4. **Run the Streamlit application**:
   ```bash
   streamlit run app.py
   ```

5. **Access the application** in your browser (typically at `http://localhost:8501`)

## 📱 Usage

1. Select a Bollywood movie from the dropdown menu
2. Click "Get similar Recommendations" button
3. View the 6 recommended Hindi movies in a clean layout

## 💡 Key Implementation Details

```python
# How recommendations work
def recommend(movie):
    # Find the index of the selected movie
    movie_index = movie_list[movie_list['title'] == movie].index[0]
    
    # Get similarity scores for this movie with all others
    distances = similarity_vector[movie_index]
    
    # Sort and get top 6 similar movies (excluding the selected movie itself)
    recommendation_list_id = sorted(list(enumerate(distances)), 
                                    reverse=True, key=lambda x: x[1])[1:7]
    
    # Fetch titles for recommended movies
    recommendation_list = []
    for i in recommendation_list_id:
        recommendation_list.append(movie_list.iloc[i[0]].title)
        
    return recommendation_list
```

## 👩‍💻 Author

**Fatima Amani**  
GitHub: [@fatima-amani](https://github.com/fatima-amani)

⭐ **Find this useful?** Star the repository to show your support! ⭐
