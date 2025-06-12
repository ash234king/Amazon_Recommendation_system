 # **Apparel Recommendation System**  
This project implements a content-based recommendation system for apparel items, leveraging product title, brand, and color information to suggest similar products. The system cleans and preprocesses a large dataset of apparel, then uses a Bag-of-Words model to calculate similarities between product titles.
  
  
## **Table of Contents**  
 -Project Overview  
 -Dataset  
 -Data Preprocessing and Cleaning  
 -NLP Preprocessing  
 -Recommendation Model (Bag-of-Words)  
 -How to Run  
 -Results  
  
  
## **Project Overview**   
The goal of this project is to build a recommendation engine that suggests apparel items based on their textual descriptions (titles), brands, and colors. This is achieved by:  
  
-Loading and inspecting a large dataset of apparel products.  
-Cleaning and filtering the data to handle missing values and duplicates.  
-Preprocessing textual data using NLP techniques like stop word removal and stemming.  
-Vectorizing product titles using a Bag-of-Words model.  
-Calculating similarity between product titles to find relevant recommendations.    
-Visualizing the recommended items along with their similarity scores.  
  
  
## **Dataset**  
The project uses a dataset named tops_fashion.json, which contains detailed information about various apparel products. Initially, the dataset comprises 183,138 data points and 19 features.  
  
Key features used in this project include:  
  
 -asin: Amazon Standard Identification Number (unique product ID)  
 -brand: Brand name of the product  
 -color: Color of the product  
 -medium_image_url: URL of the product image  
 -product_type_name: Category of the product (e.g., SHIRT, DRESS)  
 -title: Product title/description  
 -formatted_price: Price of the product  
  
  
## **Data Preprocessing and Cleaning**  
Several steps were undertaken to clean and refine the dataset:  
  
 -Feature Selection: Reduced the dataset to the most relevant 7 features.  
 -Handling Missing Values:  
   -Removed entries where formatted_price was NULL, reducing data points to 28,395.  
   -Further removed entries where color was NULL, resulting in 28,385 data points.  
 -Removing Short Descriptions: Filtered out products with titles containing 4 words or fewer, leaving 27,949 data points.  
 -Deduplication: A two-stage deduplication process was implemented based on title similarity to remove near-duplicate product entries.  
 -Stage 1 Deduplication: Reduced data points to 17,593.  
 -Stage 2 Deduplication: Further reduced data points to 16,042.  
   
## **NLP Preprocessing**  
Natural Language Processing (NLP) techniques were applied to the title column to prepare it for vectorization:  
 -Stop Word Removal: Common English stop words (e.g., "the", "a", "is") were removed from product titles to focus on more meaningful terms. This step significantly improves the quality of text-based similarity calculations.  
 -Stemming: The Porter Stemmer was used to reduce words to their base or root form (e.g., "arguing" becomes "argu", "fishing" becomes "fish"). While implemented, its application is optional and can be further integrated into the preprocessing pipeline.  
  
  
## **Recommendation Model (Bag-of-Words)**  
The core of the recommendation system is built using the Bag-of-Words (BoW) model:  
 -Count Vectorization: The preprocessed product titles were converted into a numerical representation using CountVectorizer. This created a vocabulary of 12,609 unique words across all titles.  
 -Similarity Calculation: Euclidean distance is used to measure the similarity between product titles in the Bag-of-Words feature space.  
Recommendation Logic: Given a query product, the system identifies and returns the n most similar products based on the calculated distances.  
  
  
## **How to Run**  
To run this project, you will need to have the following libraries installed:  
 -pandas  
 -numpy  
 -matplotlib  
 -seaborn  
 -Pillow (PIL)  
 -requests  
 -BeautifulSoup (bs4)  
 -nltk  
 -scikit-learn  
 -plotly  
   
Steps to run the code:  
 -Place the tops_fashion.json file in the same directory as your Python script.  
 -Run the provided Python script. It will perform data loading, preprocessing, and demonstrate the recommendation system using the Bag-of-Words model.  
 -The script saves intermediate processed dataframes as pickle files in a pickles directory. Make sure this directory exists or create it before running.  

    
## **Results**  
The bag_of_words_model function takes a doc_id (index of the query product) and num_results (number of recommendations) as input. It then outputs:  
 -The image of the recommended product.  
 -Product details: ASIN, Brand, Title.  
 -The Euclidean similarity score with the query image.  
 -The results are visualized with heatmaps showing word frequencies and an image of the recommended product.  

## **Dataset**  
The project utilizes the `tops_fashion.json` dataset. Due to GitHub's file size limitations, this dataset cannot be directly uploaded to this repository.  
