# Course-Recommendation-System

# 🎓 Course Recommendation System

A content-based recommendation system that suggests Udemy courses based on your learning interests. Type what you want to learn (e.g. *"Python programming, data analysis, web development"*) and get the top matching courses instantly through a simple web interface.

## 📌 Overview

With tens of thousands of online courses available, finding the right one is hard. This project uses **TF-IDF** and **cosine similarity** to match a user's free-text interests against course descriptions and return the most relevant results.

## 📊 Dataset

- **Source:** [Udemy Course Dataset: Categories, Ratings and Trends](https://www.kaggle.com/datasets/emrebayirr/udemy-course-dataset-categories-ratings-and-trends) on Kaggle
- **Size:** 98,104 courses, 13 columns
- **Columns:** `id`, `title`, `url`, `is_paid`, `instructor_names`, `category`, `headline`, `num_subscribers`, `rating`, `num_reviews`, `instructional_level`, `objectives`, `curriculum`
- No duplicate rows were found.

## ⚙️ How It Works

1. **Load the data** from Kaggle using `kagglehub`.
2. **Build a text profile** for each course by combining `category`, `headline`, `objectives` and `instructional_level` into one field.
3. **Vectorize** the profiles with `TfidfVectorizer` (English stop words removed).
4. **Transform the user's input** into the same TF-IDF space.
5. **Compute cosine similarity** between the user's vector and every course.
6. **Return the top N courses** with the highest similarity scores.

Each recommendation includes the course **title, category, level, rating and similarity score**.

## 🖥️ Demo App

The project includes a [Gradio](https://www.gradio.app/) interface where users enter their interests in a text box and receive the top 5 recommended courses in a table.

<!-- Add a screenshot or GIF of the app here -->
<!-- ![Demo](demo.png) -->

## 🚀 Getting Started

### Requirements

```bash
pip install pandas scikit-learn gradio kagglehub
```

### Run

1. Open the notebook in Google Colab or Jupyter.
2. Run all cells in order. The dataset downloads automatically via `kagglehub`.
3. Launch the Gradio app from the last cells and open the generated link.

### Use the function directly

```python
recommend_courses("machine learning with python", top_n=5)
```

## 🛠️ Tech Stack

- Python
- pandas
- scikit-learn (TF-IDF, cosine similarity)
- Gradio
- kagglehub

## 🔮 Future Improvements

- Weight results by rating and popularity (`num_subscribers`, `num_reviews`)
- Use semantic embeddings (e.g. Sentence-BERT) for smarter matching
- Add filters for category, level and free vs. paid courses
- Include course URLs in the results
- Deploy permanently on Hugging Face Spaces


