# Personalized-Fashion-Recommendation-Model
Using Clustering, Classification and Ranking Method for Recommendation System with H&amp;M Customer Data

### Intro
This is a group project from a Data Science course at University of Washington.
Our "H&M Personalized Fashion Recommendations" data source is from this kaggle website: https://www.kaggle.com/code/rahulappana/h-m-recommendation

### I. Data Overview
Data used in this project contains three major themes which are customer, article, and transaction. The transaction contained millions of records, so the data curation phase is difficult for us.
1. Articles: Metadata of each product available for purchase, including the product ID, product types, colors...etc. (105,542 observations)
2. Customers: Detailed information of each customer, including membership, age, postal code...etc. (31,788,324 observations)
3. Transactions: Each customer‘s transaction details, including order date, ordered products, order amount...etc. (1,371,980 observations)

We sample 300,000 observations from the Transaction table since we cannot process the full data. We’ll mention it again in our limitation section.

**The way we worked**

We utilized the Google Cloud Platform and migrated our services. Firstly, we created bucket storage to store the three CSV files. Then we used Big Query to create a cloud data warehouse based on the bucket storage. Thirdly, we configured a Compute Engine that primarily supports high CPU usage and connected with our Collab repository. Lastly, we linked the Big Query database and our Collab project so that we can have the high processing power and reduced pressure on our laptop’s RAM. 

### II. Data Curation
Below are our steps to tidy and organize our datasets in preparation for later exploratory analysis and modeling.
1. Remove missing or incomplete data; fill null values. For example, the FN, Active, and club_member_status columns from the customer dataset have missing values. We utilize two approaches: dropping the null values and replacing the null value with Scikit-learn’s SimpleImputer.
2. To ensure consistency, we correct spelling (e.g. “None” and “none”) and label categorical values using LabelEncoder.
3. Normalize numeric data by using a standard scaler
4. Extracted validation data based on each customer’s last purchase
