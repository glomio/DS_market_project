<h1>DSmarket<img src='ds_market.png' align='center' width = '100'></h1>

# Self Organizing Maps

This project consist on 4 parts working on the DS_MARKET data.

- Business Analysis
- Items clustering
- Sales predictions
- Store supply use case

# Installation


The project is stored in:

    https://github.com/lukyluca/DS_market_project


# Requirements

Python version 3.8

All packages in the used environment are in the file:

    requirements.txt

# Part 1: Business Analysis
In this part we will review all the different business aspects of DS supermaket. This review will be based on unit sales as well as unit revenue

## Getting Started
To run the notebooks, it is first necessary to run the "dollar_value_table.ipynb" notebook. This is because running this specific notebook will generate a new csv fille that is used in the other notebooks. In this notebook we have created a dataframe with the dollar revnue per unit sold per day, based on the other available tables. Once saved, The csv file was too large to store dircetly in the repository. The DS_market_data folders contains all other csv/zip file that are imported in the notebooks. The "Dashboar_data" folder contains several csv/Xlsx files which we have used to fead our dashboard

### Dependencies

* Pandas, sklearn, plotly and other package should be installed prior to running these notebooks

# Part 2: Item clustering

The clustering part works on the item_sales.csv.
The clustering part is aiming in identifying products that behave similarly.

The data from the Tribeca store (most selling store) were used to create the clusters.

Clustering features created are: frequency (total number of sold products per item) and recency (days since last purchased).
For the model creation the features were log transformed since their distribution was not gaussian.

95% of the Tribeca data was used to train the model, 5% for testing.

Data normalization was performed within Pycaret with MinMax scaler.

A k-means model with number of cluster = 5 has been created.
The elbow curve was used to find the best number of clusters.

The cluster model is saved as cluster_model_items.pkl
The cluster model is applied to all other stores and results saved in csv files.

Cluster interpretation
---------------------

The cluster identified can be interpreted as follow:

* Cluster 0 - Transition Items:Cluster with medium recency and a wide range in frequency: they could be emerging products (lower-left part of the cluster) or fading products (upper-right) part of the cluster;
* Cluster 1 - Common Items: Cluster with medium frequency and low recency: these are common products, should be most of the product and as a matter of fact it is the cluster with more items;
* Cluster 2 - Hot Items: Cluster with high frequency and low recency: these are the hot/top selling products
* Cluster 3 - Old or Bad Items: Cluster withhigh recency and a wide range in frequency: they could be bad products, that never sold (lower part of the cluster) or old product (left part of the cluster) that sold in the past but now are not selling anymore
* Cluster 4 - New Items: Cluster with low frequency and low recency: there are new/appearing products
