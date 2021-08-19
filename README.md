# Cryptocurrencies

## Overview of Project 

You and Martha have done your research. You understand what unsupervised learning is used for, how to process data, how to cluster, how to reduce your dimensions, and how to reduce the principal components using PCA. It’s time to put all these skills to use by creating an analysis for your clients who are preparing to get into the cryptocurrency market.

Martha is a senior manager for the Advisory Services Team at Accountability Accounting, one of your most important clients. Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked you to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

The data Martha will be working with is not ideal, so it will need to be processed to fit the machine learning models. Since there is no known output for what Martha is looking for, she has decided to use unsupervised learning. To group the cryptocurrencies, Martha decided on a clustering algorithm. She’ll use data visualizations to share her findings with the board.

## Deliverables:

### Deliverable 1: Preprocessing the Data for PCA
### Deliverable 2: Reducing Data Dimensions Using PCA
### Deliverable 3: Clustering Cryptocurrencies Using K-means
### Deliverable 4: Visualizing Cryptocurrencies Results

This new assignment consists of three technical analysis deliverables and a proposal for further statistical study:
  * Data Source: `crypto_data.csv`
  * Data Tool: `crypto_clustering_starter_code.ipynb`
  * Software: `Python 3.7`, `Anaconda`, `Jupyter Notebook`

## Analysis: Unsupervised Machine Learning and Cryptocurrencies
Using Unsupervised Learning to Discover Unknown Patterns

### Deliverable 1: Preprocessing the Data for PCA

* The following six preprocessing steps have been performed on the `crypto_df` DataFrame:
    - All cryptocurrencies that are not being traded are removed
    - All cryptocurrencies that do not have a defined algorithm are removed
    - The `IsTrading` column is dropped 
    - All the rows that have at least one null value are removed 
    - All the rows that do not have coins being mined are removed 
    - The `CoinName` column is dropped
* A new DataFrame is created that stores all cryptocurrency names from the CoinName column and retains the index from the `crypto_df` DataFrame 
* The `get_dummies()` method is used to create variables for the text features, which are then stored in a new DataFrame, `X` 
* The following was done to preprocess the data:
  1. Remove cryptocurrencies not being traded.
  2. Keep all the cryptocurrencies that have a working algorithm
  3. The `IsTrading` column it was dropped.
  4. Rows that have null value were dropped.
  5. Filter dataset with only mined coins.
  6. Create a new DataFrame `CoinNames`, and use the index from the previous dataset as the index for this new DataFrame `cc_names_df`
<img width="1026" alt="Screen Shot 2021-08-19 at 5 16 28 PM" src="https://user-images.githubusercontent.com/82353749/130145414-57c9d5fc-49d7-4b54-ae5b-fba1c9cfabf3.png">

* The features from the `X` DataFrame have been standardized using the StandardScaler `fit_transform()` function
<img width="996" alt="Screen Shot 2021-08-19 at 5 17 24 PM" src="https://user-images.githubusercontent.com/82353749/130145491-18b153ed-7f8a-4598-bbd0-4ed254638610.png">

### Deliverable 2: Reducing Data Dimensions Using PCA 

* Continue using the crypto_clustering.ipynb file from Deliverable 1 where you’ve already performed the preprocessing steps.

* Using the information we’ve provided, apply PCA to reduce the dimensions to three principal components.
<img width="1009" alt="Screen Shot 2021-08-19 at 5 21 33 PM" src="https://user-images.githubusercontent.com/82353749/130145959-e1d65e18-543c-4a5a-a4f7-0d1f708f46ae.png">

* Create a new DataFrame named pcs_df that includes the following columns, Principal Component 1, Principal Component 2, and Principal Component 3, and uses the index of the crypto_df DataFrame as the index.
<img width="993" alt="Screen Shot 2021-08-19 at 5 22 23 PM" src="https://user-images.githubusercontent.com/82353749/130146049-97be2f41-683b-49b8-a735-341da50bc075.png">

### Deliverable 3: Clustering Cryptocurrencies Using K-means

Follow the instructions below and use the information in the crypto_clustering_starter_code.ipynb file to complete Deliverable 3.

1. Continue using the `crypto_clustering.ipynb` file that you used in Deliverable 2 to reduce the dataset to three dimensions.
2. Using the `pcs_df` DataFrame, create an elbow curve using `hvPlot` to find the best value for **K**.
3. Next, use the `pcs_df` DataFrame to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data.
If you’d like a hint on how to use the K-means algorithm, that’s totally okay. If not, that’s great too. You can always revisit this later if you change your mind.
4. Create a new DataFrame named `clustered_df` by concatenating the `crypto_df` and `pcs_df` DataFrames on the same columns. The index should be the same as the `crypto_df` DataFrame.
5.  Add the CoinName column that holds the names of the cryptocurrencies, which you created in Step 7 of Deliverable 1, to the `clustered_df`.
6. Add another new column to the `clustered_df` named `Class` that holds the predictions, i.e.,` model.labels_`, from Step 3.
<img width="1019" alt="Screen Shot 2021-08-19 at 5 24 15 PM" src="https://user-images.githubusercontent.com/82353749/130146278-4b35c849-67cd-4702-980d-268bb7d55365.png">
<img width="1042" alt="Screen Shot 2021-08-19 at 5 26 21 PM" src="https://user-images.githubusercontent.com/82353749/130146505-fde65225-7800-4991-8944-38a181eefcec.png">
<img width="1028" alt="Screen Shot 2021-08-19 at 5 27 07 PM" src="https://user-images.githubusercontent.com/82353749/130146659-0da3d1a5-a7a2-490b-bcb3-8a49214400ab.png">

### Deliverable 4: Visualizing Cryptocurrencies Results 

Using your knowledge of creating scatter plots with Plotly Express and `hvplot`, you’ll visualize the distinct groups that correspond to the three principal components you created in Deliverable 2, then you’ll create a table with all the currently tradable cryptocurrencies using the `hvplot.table()` function.

1. Creating a 3D-Scatter with the PCA data and the clusters
<img width="1023" alt="Screen Shot 2021-08-19 at 5 31 43 PM" src="https://user-images.githubusercontent.com/82353749/130147142-c2fc1719-532c-424e-82f7-5415e9d9b95f.png">
2. Create a table with tradable cryptocurrencies
<img width="975" alt="Screen Shot 2021-08-19 at 5 32 29 PM" src="https://user-images.githubusercontent.com/82353749/130147236-c6b80fdd-e013-453e-863e-cd39f938425c.png">
3. Create a new DataFrame that has the scaled data with the clustered_df DataFrame index. Add the "CoinName" column from the clustered_df DataFrame to the new DataFrame. Add the "Class" column from the clustered_df DataFrame to the new DataFrame. 
<img width="1029" alt="Screen Shot 2021-08-19 at 5 34 43 PM" src="https://user-images.githubusercontent.com/82353749/130147445-1ad7428c-74fe-4552-9a7b-a1f7899791af.png">
4. Create a hvplot.scatter plot using x="TotalCoinsMined" and y="TotalCoinSupply".
<img width="994" alt="Screen Shot 2021-08-19 at 5 37 01 PM" src="https://user-images.githubusercontent.com/82353749/130147699-c208f9bf-8f06-412a-b8cc-61b9fe5d09ce.png">

##### Cryptocurrency analysis completed by Jing Tang
 

 


