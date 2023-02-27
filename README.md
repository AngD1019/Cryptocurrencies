# Cryptocurrencies
Use unsupervised Machine Learning techniques to analyze cryptocurrency data

## Project Overview
The Advisory Services Team at Accountability Accounting, a prominant investment bank is interested in offering a new cryptocurrency investment portfolio for its customers. However, the company is lost in the vast universe of cryptocurrencies, so they would like to see a report that includes which cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new system they would like to implement.

The data we are working with is not ideal, so it will need to be processed to fit the machine learning models. Since there is no known output for what we are looking for, we have decided to use unsupervised learning. To group the cryptocurrencies, we decided on a clustering algorithm. We will use data visualizations to share findings with the board.

This project includes four technical analysis parts:

* Part 1: Preprocessing the Data for PCA
* Part 2: Reducing Data Dimensions Using PCA
* Part 3: Clustering Cryptocurrencies Using K-means
* Part 4: Visualizing Cryptocurrencies Results

## Analysis

#### Part 1: Preprocessing the Data for PCA
* Read in the crypto_data.csv to the Pandas DataFrame named crypto_df.
* Keep all the cryptocurrencies that are being traded.
* Drop the IsTrading column.
* Remove rows that have at least one null value.
* Filter the crypto_df DataFrame so it only has rows where coins have been mined.
* Create a new DataFrame that holds only the cryptocurrency names, and use the crypto_df DataFrame index as the index for this new DataFrame.
* Remove the CoinName column from the crypto_df DataFrame since it's not going to be used on the clustering algorithm.
*  Use the get_dummies() method to create variables for the two text features, Algorithm and ProofType, and store the resulting data in a new DataFrame named X.
* Use the StandardScaler fit_transform() function to standardize the features from the X DataFrame.

![part1_image_4column_df](https://user-images.githubusercontent.com/114960958/221658737-fbac68ce-9d6a-4601-b5cc-e6a5bac47aef.png)

#### Part 2: Reducing Data Dimensions Using PCA
*Continue using the crypto_clustering.ipynb file from Objective 1 where you’ve already performed the preprocessing steps.
* Using the information we’ve provided, apply PCA to reduce the dimensions to three principal components
* Create a new DataFrame named pcs_df that includes the following columns, PC 1, PC 2, and PC 3, and uses the index of the crypto_df DataFrame as the index.

![part2_pcs_df](https://user-images.githubusercontent.com/114960958/221658769-af8b3f26-3182-41eb-b7be-d83d98b84c56.png)

#### Part 3: Clustering Cryptocurrencies Using K-means
* Continue using the crypto_clustering.ipynb file that you used in Objective 2 to reduce the dataset to three dimensions
* Using the pcs_df DataFrame, create an elbow curve using hvPlot to find the best value for K.
* Next, use the pcs_df DataFrame to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data
* Create a new DataFrame named clustered_df by concatenating the crypto_df and pcs_df DataFrames on the same columns. The index should be the same as the crypto_df DataFrame
* Add the CoinName column that holds the names of the cryptocurrencies, which you created in Step 7 of Objective 1, to the clustered_df.
* Add another new column to the clustered_df named Class that holds the predictions, i.e., model.labels_,
* Create an hvplot scatter plot with x="TotalCoinsMined", y="TotalCoinSupply", and by="Class", and have it show the CoinName when you hover over the the data point

![part3_clustered_df](https://user-images.githubusercontent.com/114960958/221658808-b8095f68-8219-47dc-abd3-55a45bf51803.png)

#### Part 4: Visualizing Cryptocurrencies Results
* Continue using the crypto_clustering.ipynb file from Objective 3 where you have predicted the K clusters for the cryptocurrencies’ data.

* Create a 3D scatter plot using the Plotly Express scatter_3d() function to plot the three clusters from the clustered_df DataFrame

* Add the CoinName and Algorithm columns to the hover_name and hover_data parameters, respectively, so each data point shows the CoinName and Algorithm on hover

* Create a table with tradable cryptocurrencies using the hvplot.table() function. 

![part4_hvplot_table](https://user-images.githubusercontent.com/114960958/221659146-14a4ae5d-d002-440d-9325-198d968c858d.png)

* Print the total number of tradable cryptocurrencies in the clustered_df DataFrame

* Use the MinMaxScaler().fit_transform method to scale the TotalCoinSupply and TotalCoinsMined columns between the given range of zero and one

* Create a new DataFrame using the clustered_df DataFrame index that contains the scaled data you created in Step 5

* Add the CoinName column from the clustered_df DataFrame to the new DataFrame

* Add the Class column from the clustered_df DataFrame to the new DataFrame

![part4_clustered_classcolumn_df](https://user-images.githubusercontent.com/114960958/221659335-c7806b5c-c9cd-4c83-a5e4-95f3fe375841.png)

![part4_scatter_plot](https://user-images.githubusercontent.com/114960958/221659349-6a6e95a9-c784-43c0-9165-2e188518ddc6.png)
