# Apartment Price Prediction

### by
[ETTARBAOUI BADR](https://github.com/EttarbaouiBadr)

Predicting apartment prices using machine learning.

## Table of Contents

1. [Introduction](#introduction)
2. [Dataset](#dataset)
3. [Data Preprocessing](#data-preprocessing)
4. [Exploratory Data Analysis](#exploratory-data-analysis)
5. [Feature Selection](#feature-selection)
6. [Model Training](#model-training)
7. [Model Evaluation](#model-evaluation)
8. [Deployment](#deployment)
9. [Conclusion](#conclusion)
10. [Contributing](#contributing)
11. [License](#license)

## Introduction

In this project, we leverage machine learning techniques to analyze a comprehensive dataset containing information about apartments. Through data preprocessing, exploratory data analysis, and model development, we strive to create a predictive model capable of estimating apartment prices with precision.
The predictive model considers various factors such as location, size, amenities, and other relevant features to make informed predictions. By the end of this project, we aim to not only create an accurate model but also share insights into the factors that significantly influence apartment prices.
Feel free to explore the project, contribute to its development, and utilize the predictive model for your own analyses. Let's delve into the world of apartment price prediction and unlock the potential of data-driven decision-making in real estate!

## Dataset
![Done](https://img.shields.io/badge/Status-DONE-green)

### Source
The dataset for this project was obtained by scraping apartment listings from the Avito website using BeautifulSoup. Avito is a popular online classified advertisements platform where users can find and publish listings for various products and services, including real estate.

### Data Overview
The dataset consists of information gathered from apartment listings, with each observation representing a unique apartment listing. The data includes both numerical and categorical features, providing insights into various aspects of the apartments listed on Avito.

### Features
1. **House Name**: The name or identifier of the apartment building or complex.
2. **Prix (Price)**: The listed price of the apartment.
3. **Équipements (Amenities)**: Features and amenities associated with the apartment.
4. **Type**: The type of apartment, such as studio, one-bedroom, etc.
5. **Secteur (Sector)**: The geographical sector or location of the apartment.
6. **Frais de syndic / mois (Monthly Syndicate Fees)**: Monthly fees associated with the apartment's building management.
7. **Surface habitable (Living Area)**: The total living area of the apartment in square meters.
8. **Étage (Floor)**: The floor on which the apartment is located.
9. **Salons (Rooms/Living Rooms)**: The number of living rooms in the apartment.
10. **Caution (Deposit)**: The deposit amount required for renting the apartment.
11. **Âge du bien (Property Age)**: The age of the property/building.
12. **Horaire d'arrivée (Check-in Time)**: The specified check-in time for the apartment.
13. **Horaire de départ (Check-out Time)**: The specified check-out time for the apartment.

## Data Preprocessing
![Done](https://img.shields.io/badge/Status-DONE-green)

The raw dataset obtained from Avito underwent a series of preprocessing steps to ensure its suitability for training a machine learning model. The primary objectives of data preprocessing were to handle missing values, encode categorical variables, and address any outliers or inconsistencies in the data.

### 1. Handling Missing Values

Several columns in the dataset were examined for missing values. Depending on the nature of the missing data, the following strategies were applied:

- **Numeric Features:** Missing values in numeric columns, such as *Surface habitable* and *Âge du bien*, were addressed by imputing the mean or median value.
- **Categorical Features:** For categorical columns like *Type* and *Équipements*, missing values were handled by replacing them with the mode or a designated category.

### 2. Encoding Categorical Variables

Machine learning models typically require numerical inputs, so categorical variables, such as *Type* and *Secteur*, were encoded using appropriate techniques:

- **One-Hot Encoding:** Applied to categorical features with multiple categories, creating binary columns for each category.
- **Label Encoding:** Used for ordinal categorical variables where the order matters, such as *Étage* (Floor).

### 3. Cleaning and Transformation

Certain columns required specific cleaning and transformations:

- **Textual Data:** The *Équipements* column, which contains textual information about amenities, underwent text processing to extract relevant features and convert them into numerical representations.
- **Timestamps:** Columns like *Horaire d'arrivée* and *Horaire de départ* were converted into datetime objects for easier manipulation.

### 4. Outlier Detection and Handling

Outliers were identified in numeric columns, especially in features like *Prix* and *Surface habitable*. These outliers were either removed or transformed to minimize their impact on model training.

### 5. Feature Scaling

Numeric features were scaled to a standard range to prevent certain features from dominating others during model training. Standard scaling (z-score normalization) was applied to features with varying scales.

The preprocessed dataset is now ready for model development, ensuring that it is free from missing values, properly encoded, and suitable for training a machine learning model for apartment price prediction.


## Exploratory Data Analysis
![Done](https://img.shields.io/badge/Status-DONE-green)

The Exploratory Data Analysis phase involved a thorough examination of the dataset to uncover patterns, relationships, and insights that could inform the subsequent steps in the apartment price prediction project.

### 1. Univariate Analysis

#### Distribution of Price
We began by exploring the distribution of apartment prices (*Prix*) to understand the central tendency, spread, and presence of any outliers. Visualization tools like histograms and box plots were employed to illustrate the distribution.

#### Numeric Features
A comprehensive analysis of numeric features, including *Surface habitable*, *Étage*, and *Âge du bien*, provided insights into their distributions and potential impact on apartment prices.

#### Categorical Features
Exploration of categorical features, such as *Type*, *Secteur*, and *Équipements*, involved examining the frequency of each category to identify prevalent characteristics within the dataset.

### 2. Bivariate Analysis

#### Price vs. Numeric Features
Scatter plots and correlation matrices were utilized to explore the relationship between apartment prices and numeric features, helping identify potential correlations or trends.

#### Price vs. Categorical Features
Box plots and bar charts were employed to visualize the influence of categorical features on apartment prices, providing insights into how different categories contribute to price variations.

### 3. Feature Interactions

Heatmaps and pair plots were generated to explore interactions between multiple features, revealing potential dependencies or multicollinearity among predictors.

### 4. Outlier Detection

Further investigation into potential outliers, especially in features like *Surface habitable* and *Prix*, helped ensure the robustness of the dataset and identify any extreme values that might impact model performance.

### 5. Summary Insights

The EDA phase provided the following key insights:

- Apartments in certain sectors (*Secteur*) tend to have higher prices.
- The number of rooms (*Salons*) and the living area (*Surface habitable*) exhibit positive correlations with prices.
- Specific amenities (*Équipements*) contribute to price variations.

## Feature Selection
![Done](https://img.shields.io/badge/Status-DONE-green)

Feature selection is a pivotal step in constructing an effective machine learning model for predicting apartment prices. This process involves identifying and retaining the most relevant features that significantly contribute to the model's predictive accuracy while eliminating redundant or less impactful variables.

### 1. Correlation Analysis

#### Correlation Matrix
A correlation matrix was computed to examine relationships between different features, especially focusing on their correlation with the target variable (*Prix*). Notable features in this analysis include:
- **Secteur:** The geographical sector of the apartment.
- **Surface habitable:** The total living area of the apartment.
- **Étage:** The floor on which the apartment is located.
- **Salons:** The number of living rooms.
- **equipments_nbr:** The number of amenities in the apartment.

#### Feature Importance
For tree-based models, such as Random Forest, we calculated feature importance scores. This analysis provided insights into the most influential features, with a particular emphasis on:
- **Type_Appartements, à louer:** Binary indicator for the apartment type available for rent.
- **Type_Locations de vacances, à louer:** Binary indicator for vacation rentals.

## Model Training
![In Progress](https://img.shields.io/badge/Status-In%20Progress-yellow)
## Model Evaluation
![In Progress](https://img.shields.io/badge/Status-In%20Progress-yellow)
## Deployment
![not done yet](https://img.shields.io/badge/Status-Not%20Done%20Yet-red)
## Conclusion


 
