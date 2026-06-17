# Data Analytics Job Market Analysis and Salary Prediction in Indonesia

## Overview
This repository contains a comprehensive data mining and machine learning research project aimed at analyzing job postings for "Data and Analytics" roles from Jobstreet Indonesia. The primary objective is to uncover the underlying determinants of salaries in the data analytics sector by extracting insights from unstructured job descriptions and predicting salaries using advanced machine learning regression models.

## Methodology

### 1. Data Cleansing & Parsing
- **Salary Extraction:** The dataset contained unstructured salary texts. A complex parser was built to extract numeric values, normalize different payment periods (hourly, daily, monthly, yearly), and calculate a standardized middle monthly salary in Indonesian Rupiah (IDR).
- **Text Preprocessing:** All text data was lowercased and stripped of special characters to ensure uniformity.

### 2. Feature Engineering & Text Mining
- **Skill Extraction:** We implemented text mining techniques to flag the presence of specific technical skills (e.g., Python, SQL, Excel, Power BI, Tableau, Machine Learning) directly from the job descriptions.
- **Seniority Inference:** By analyzing the required years of experience and specific keywords in the job title or description, the project successfully inferred the seniority level for each posting (e.g., Entry Level, Junior, Middle, Senior, Manager).
- **TF-IDF Vectorization:** Stopwords and generic job terms were removed. The remaining textual data was converted into numerical format using TF-IDF (Term Frequency-Inverse Document Frequency) to capture the true essence of the job requirements.

### 3. Machine Learning Modeling
We evaluated three different modeling approaches to predict the monthly salary:
1. **Baseline Model (No Text):** A simple Linear Regression model using only numerical and categorical features (ignoring text).
2. **Ridge Regression (L2 Regularization):** A linear model that incorporates all text features (TF-IDF) alongside numerical and categorical data.
3. **Lasso Regression (L1 Regularization):** A linear model that forces many feature weights to zero, effectively selecting only the most prominent text features.

## Visualization and Results Analysis

### 1. Salary Distribution
- **Histogram of Salaries:** The distribution of raw salaries exhibits a right-skewed pattern, indicating that while most data analytics roles offer standard market wages, a few positions (likely executive or highly specialized roles) offer exceptionally high salaries.
- **Log Transformation:** Applying a logarithmic transformation to the salaries results in a much more normal (bell-shaped) distribution, which is ideal for linear regression models.

### 2. Salary by Seniority Level (Boxplot)
- The boxplot visualization clearly demonstrates a positive correlation between seniority and compensation. 
- **Entry Level / Junior:** These roles show the lowest median salaries and relatively tight variance.
- **Senior / Manager:** These roles not only have significantly higher median salaries but also exhibit a wider spread (variance), suggesting that compensation at higher levels is highly negotiable and depends heavily on the specific company or the exact skill set of the candidate.

### 3. Model Performance (Actual vs. Predicted & Residuals)
- **Model Comparison:** 
  - The Baseline model performed poorly (negative $R^2$), proving that numerical and categorical data alone are insufficient to predict salary.
  - The **Ridge Regression** model performed the best ($R^2 \approx 0.216$, MAE $\approx$ 3.38 Million IDR). 
- **Residual Plots:** The actual versus predicted scatter plots and residual plots for the Ridge model show a tighter clustering around the zero-error line compared to Lasso. However, some variance remains, which is expected given the subjective nature of salary determinations in the real world.

### 4. Top Salary Determinants (Coefficients)
By analyzing the coefficients of the Ridge and Lasso models, we extracted the top drivers of salary in the data analytics job market:
- **Positive Drivers (Higher Salary):** 
  - `Experience Years`: The strongest positive predictor.
  - `Location`: Being based in Central Jakarta (Jakarta Pusat) or West Jakarta (Jakarta Barat) significantly boosts the expected salary.
  - `Specific Tools`: Mastery of advanced BI tools like **Power BI** correlates with higher pay.
  - `Seniority`: Positions labeled as "Senior Level" or "Manager" naturally command a premium.
- **Negative Drivers (Lower Salary):**
  - `Basic Skills`: Mentions of foundational skills like "Excel" or "Google Data Studio" as primary requirements tend to be associated with lower-paying or entry-level roles.
  - `Location`: Roles based in regions outside the main business hubs (e.g., Bandung, Bogor) show lower expected salaries.
  - `Entry Level`: As expected, roles explicitly marked as entry-level significantly drag down the predicted wage.

## Conclusion
This project successfully demonstrates that text mining applied to unstructured job descriptions provides critical predictive power that numerical data alone cannot offer. By utilizing natural language processing (NLP) and Ridge Regression, we established a clear hierarchy of skills, locations, and seniority levels that dictate the compensation landscape for Data and Analytics professionals in Indonesia.

## Files in this Repository
- `RM.ipynb`: The main Jupyter Notebook containing all the Python code, data processing, modeling, and visualizations.
- `paper kelompok 12.pdf`: The final research paper associated with this project.
- `AcceptanceLetter (8).pdf`: Acceptance documentation for the research.
