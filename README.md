# **Book Recommender System**  
_A comprehensive book recommendation system utilizing various techniques to predict user preferences._

---

## **Table of Contents**  
1. [Introduction](#introduction)  
2. [Dataset Description](#dataset-description)  
3. [Data Preprocessing](#data-preprocessing)  
4. [Methodology](#methodology)  
    - [Baseline Methods](#baseline-methods)  
    - [Content-Based Filtering](#content-based-filtering)  
    - [Collaborative Filtering (SVD)](#collaborative-filtering-svd)  
    - [Neural Collaborative Filtering (NCF)](#neural-collaborative-filtering-ncf)  
    - [Hybrid Recommendation System](#hybrid-recommendation-system)  
5. [Performance Evaluation](#performance-evaluation)  
6. [Discussion](#discussion)  
7. [Conclusion](#conclusion)  
8. [Future Work](#future-work)  
9. [References](#references)  

---

## **Introduction**  
In the era of information overload, recommendation systems have become essential for guiding users toward relevant content. This project aims to develop a book recommendation system using the [Book-Crossing dataset](https://www.kaggle.com/datasets) and evaluate its performance with various algorithms.  

### **Objectives**  
- Implement multiple recommendation techniques.  
- Compare performance using appropriate evaluation metrics.  
- Enhance system accuracy through advanced methods like Neural Collaborative Filtering (NCF).  

---

## **Dataset Description**  
The project uses the [Book-Crossing dataset](https://www.kaggle.com/datasets), comprising:  
- `Users.csv`: User demographic data.  
- `Books.csv`: Metadata for books.  
- `Ratings.csv`: User ratings for books.  

### **Dataset Statistics**  
- **Users**: 278,858 entries.  
- **Books**: 271,360 entries.  
- **Ratings**: 1,149,780 entries (scale: 1–10).  

---

## **Data Preprocessing**  
Key preprocessing steps included:  
1. **Handling Missing Values**  
   - Imputed missing user ages and clipped to [10–100].  
   - Replaced missing book authors/publishers with "Unknown."  

2. **Data Filtering**  
   - Retained users with ≥5 ratings and books with ≥10 ratings.  

3. **Data Splitting**  
   - Split dataset into 80% training and 20% testing.  

### **Resulting Dataset**  
- Filtered Ratings: 96,234 entries.  
- Training Set: 76,987 entries.  
- Testing Set: 19,247 entries.  

---

## **Methodology**  
This project implements the following techniques:  

### **1. Baseline Methods**  
- **Global Mean**: Average rating across all users/books.  
  - RMSE: 1.7476  
- **User Mean**: Average rating by each user.  
  - RMSE: 1.6774  

---

### **2. Content-Based Filtering**  
Recommends items based on their similarity to user preferences.  
- **TF-IDF Vectorization**: Extracted features from book titles.  
- **Cosine Similarity**: Calculated similarity scores.  
- **Example**: Given *"The Lovely Bones"*, recommendations included *"Bare Bones"* and *"Lovely in Her Bones"*.  

---

### **3. Collaborative Filtering (SVD)**  
Predicts user preferences using latent factors derived via Singular Value Decomposition (SVD).  
- **RMSE**: 1.5828  

---

### **4. Neural Collaborative Filtering (NCF)**  
Uses neural networks for non-linear user-item interaction modeling.  
- **Optimized Hyperparameters**:  
  - Latent Dimension: 40  
  - Dropout Rate: 0.1  
- **Performance**:  
  - RMSE: **1.5805**  

---

### **5. Hybrid Recommendation System**  
Combines collaborative filtering and content-based filtering for improved recommendations.  
- **Weighted Hybrid**: SVD (70%), Content-Based (20%), Global Mean (10%).  
- **Performance**: RMSE: 2.1531  

---

## **Performance Evaluation**  
### **Metrics**  
- **RMSE**: Measures prediction accuracy.  
- **Precision, Recall, F1 Score**: Evaluate relevance and coverage of recommendations.  

### **Model Comparison**  
| Model                | RMSE   | Precision (≥6) | Recall (≥6) |  
|----------------------|--------|----------------|-------------|  
| SVD                 | 1.5828 | 0.8825         | 0.9901      |  
| NCF                 | 1.5805 | 0.8860         | 0.9858      |  
| Hybrid              | 2.1531 | 0.9175         | 0.8044      |  

---

## **Discussion**  
### **Key Findings**  
- NCF surpassed SVD with proper hyperparameter tuning.  
- Hybrid systems struggled with recall despite high precision.  

### **Challenges**  
- **Data Sparsity**: Limited ratings hindered learning.  
- **Cold-Start Problem**: Difficulty recommending for new users/items.  

---

## **Conclusion**  
This project demonstrated the value of advanced techniques like NCF in recommendation systems. Optimizing hyperparameters and balancing precision/recall were critical to success.  

---

## **Future Work**  
- Address cold-start problems with demographic-based recommendations.  
- Incorporate additional metadata like genres and descriptions.  
- Experiment with ensemble methods and attention mechanisms.  

---

## **References**  
1. [Book-Crossing Dataset](https://www.kaggle.com/datasets)  
2. [Surprise Library](https://surprise.readthedocs.io/)  
3. [TensorFlow Keras API](https://www.tensorflow.org/guide/keras)  
