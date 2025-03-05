# 🎬 Movie Analysis Project

## 📌 Overview
This project performs **data analysis on movie datasets** to extract meaningful insights, visualize trends, and discover interesting patterns in **IMDB scores, genres, countries, and more!**

## 🛠️ Technologies Used
- **Python** (Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn)
- **Jupyter Notebook**
- **Excel (for data storage & output)**

## 📂 Dataset
The dataset contains information on various movies, including:
- 🎭 **Genres**
- 🌍 **Countries**
- ⭐ **IMDB Scores**
- 🎬 **Plot Keywords**
- 💰 **Budget & Revenue**

## 🔍 Key Features & Analysis
### 1️⃣ **Data Cleaning & Preprocessing**
✅ Handling missing values
✅ Encoding categorical features
✅ Data transformation for better analysis

### 2️⃣ **Exploratory Data Analysis (EDA)**
📊 **IMDB Scores vs. Countries**
```python
# Convert country names to numerical codes
df['country_code'] = df['country'].astype('category').cat.codes

# Scatter plot
plt.scatter(df['imdb_score'], df['country_code'])
plt.xlabel("IMDB Score")
plt.ylabel("Country (Encoded)")
plt.show()
```
📈 **Genre Popularity**
```python
from collections import Counter
all_genres = ",".join(df['genres'].dropna()).split(",")
genre_counts = Counter(all_genres)
top_10_genres = genre_counts.most_common(10)
```

### 3️⃣ **Sentiment Analysis on Movie Descriptions**
💬 **TextBlob for Sentiment Scores**
```python
from textblob import TextBlob

def get_sentiment(text):
    if pd.isna(text):
        return 0  # Neutral if no keywords
    return TextBlob(text.replace("|", " ")).sentiment.polarity

df["sentiment_score"] = df["plot_keywords"].apply(get_sentiment)
```

### 4️⃣ **Saving Cleaned Data to Excel**
```python
df.to_excel("movies_cleaned.xlsx", index=False)
```

## 📊 Visualizations
📍 **IMDB Score Distributions**
📍 **Genre Correlations**
📍 **Country-wise Movie Trends**
📍 **Sentiment Analysis of Movie Descriptions**

## 🚀 How to Run
1. Clone this repository
2. Install dependencies: `pip install -r requirements.txt`
3. Open **Jupyter Notebook**
4. Run `movies.ipynb`

## 📌 Future Improvements
- 🎭 **Advanced NLP for sentiment analysis**
- 🔍 **Deeper correlation analysis between budget & revenue**
- 🎥 **Movie recommendations using ML models**

📢 **Contributions & Feedback are Welcome!** 🎉

