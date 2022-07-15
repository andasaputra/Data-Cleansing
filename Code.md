# Code Guideline

This file will show you step by step to archieve the goals mentioned in the readme file

## Step by Step Explained
Before starting the data cleansing, here are few step needed :

* Import Pandas & Numpy 
  * importing Pandas and Numpy are necessary as we work with dataframe
  * How to :
    `import pandas as pd`
    `import numpy as np`
    
* Loading the Data
  * You could loading the data by uploading the file or connect your google collab by using google drive (I personally using google drive access)
  * How to :
    `df = pd.read_csv('/content/drive/MyDrive/Colab Notebooks/Tugas Dibimbing/Day 8/telco_customer_churn.csv')`
    
* Showing all type of the data
  * How to : `df.dtypes`
  
* Rename customerID into CustID
  * How to : `df = df.rename(columns={'customerID':'CustID'})`

* Lowercase all columns name
  * How to : `df.columns = df.columns.str.lower()`
 
* Remove word 'automatic' and removing all whitespace in front and end of word
  * How to : `df['paymentmethod'] = df['paymentmethod'].str.replace("automatic",'').str.replace("(","").str.replace(")","").str.strip()`
  * Notes : for removing whitespace, the method using is `.str.strip()` and you can combine this into only one function
  
* Data Pre-Processing & One hot encoding from `phoneservice` and using `service` as prefix
  * How to :
    * Create new dataframe first : `df_phoneservice = df[['phoneservice']]`
    * Create the one hot encoding : `pd.get_dummies(df_phoneservice, columns=['phoneservice'],prefix='service')`

* Data Pre-Processing & Normalization (using monthlycharges as dataframe)
  * How to :
    * Create new dataframe : `df_monthlycharges = df[['monthlycharges']]`
    * Import MinMaxScaler : `from sklearn.preprocessing import MinMaxScaler`
    * Assign MinMaxScaler : `min_max_scaler = MinMaxScaler()`
    * Doing the Normalization : `df['monthlychargesnormalize'] = min_max_scaler.fit_transform (df[['monthlycharges']])`

* Data Pre-Processing & Normalization (using totalcharges as dataframe)
  * How to :
    * Notes : As the datatype is object, we need to change the datatype into float : `df['totalcharges'] = pd.to_numeric(df['totalcharges'],errors='coerce')`
      * Coerce is not necessary for some of other data
    * Import StandartScaler : `from sklearn.preprocessing import StandardScaler`
    * Assign StandartScaler : `std_scaler = StandardScaler()`
    * Doing the Normalization : `df['totalchargesSTD'] = std_scaler.fit_transform (df[['totalcharges']])`


## Complete Result

For the complete code and result, I also upload the files, but in "Bahasa Indonesia". I hope, this explanation will guide some of you that maybe also learn python and datascience from the beginning. Godspeed.
