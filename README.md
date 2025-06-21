# NYC-Airbnb-Data-Analysis

![](New_York_City_Photo.jpg)

## Introduction

Well known for having the 'Statue of Liberty', which was gifted from France, New York City (NYC) is the most populous city in the United States of America, with 5 boroughs, namely, Bronx, Brooklyn, Manhattan, Queens, and Staten Island. The NYC Airbnb Data Analysis is a project aimed at accessing the Airbnb listings in New York City, and also analyzing how each borough compares to others in terms of their prices. In total, 3 datasets were involved in order to analyze the city's response to the Airbnb listings. The datasets were cleaned and analyzed, using Python (on Jupyter Notebook), and the outcome was visualized.

**_Disclaimer_**: _The NYC image (just before the introduction) was obtained from sonnenklar.tv and has only been used for illustrative purposes. Also, the datasets do not represent the city and have been utilized to demonstrate the various functions in Python._

## Skills Demonstrated
* Data Importation
* Null Values Check
* Duplicates Check
* Column String Removal
* DataFrame Merging
* Data Categorization
* Exploratory Data Analysis (EDA)

## Problem Statement
* What is the average price, per night, of an Airbnb listing in NYC?
* How does the average price of an Airbnb listing, per month, compare to the private rental market?
* What timeframe are we working with?
* Join all DataFrames involved in the analysis
* How do Airbnb listing prices compare across the five NYC boroughs?
* Categorize the price range by boroughs.

## Data Sourcing
In total, 3 datasets were used for this analysis, and all of them were sourced from [DataCamp](https://www.datacamp.com). The datasets have been uploaded as part of the files on this repository. The 3 datasets were Price, Room Type, and Review datasets, and each had 25,209 rows and 3 columns.

## Data Cleaning
Python was the technical skill used in the data cleaning and EDA throughout this analysis. All codes were written and run on Jupyter Notebook. All Python library packages that were used include Pandas, Numpy, Matplotlib, Seaborn, Datetime, and Locale.
The following steps were covered in the course of cleaning the 3 datasets that were involved in this analysis:

* **Importing Python Libraries:**

The first step in Jupyter Notebook was to import the Python libraries before accessing, cleaning, and transforming the datasets.

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import datetime as dt
import locale
```

---

* **Importing and Loading the Datasets:**

Since there were three datasets for this project, each with a different format, they were all imported individually. The first dataset (Price), a CSV file, was imported using 'pd.read_csv'. 

```python
# Importing and loading the 3 datasets
# Airbnb price

airbnb_price = pd.read_csv("airbnb_price.csv")
airbnb_price
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_3.png)

The second dataset (Room Type) was imported as an Excel file due to the '.xlsx' extension. 

```python
# Importing and loading the Airbnb room type

airbnb_room_type = pd.read_excel("airbnb_room_type.xlsx")
airbnb_room_type
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_4.png)

Lastly, the third dataset (Review), a tab-separated file, was imported using 'pd.read_csv' but with the inclusion of '\t' as the separator or delimiter.

```python
# Importing and loading the Airbnb reviews

airbnb_review = pd.read_csv("airbnb_last_review.tsv", sep = "\t")
airbnb_review
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_5.png)

---

* **Viewing All DataFrames:**

After importing and loading all 3 datasets and using them to create DataFrames, their first 5 rows were viewed in a combined format, using '.head()' to show the first 5 rows, and '\n' to move to a new line after displaying the rows of each DataFrame. For this documentation, the DataFrames will be given an alias.

-- **Airbnb Price** alias **Price DF**

-- **Airbnb Room Type** alias **Room Type DF**

-- **Airbnb Review** alias **Review DF**

```python
# Viewing the first 5 rows of all tables

print (airbnb_price.head(), "\n", airbnb_room_type.head(), "\n", airbnb_review.head())
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_6.png)

---

* **DataFrames Information:**

This function was carried out to display the columns in all DataFrames, the count of non-null rows, and the data types of all columns. By using the '.info' function, it was possible to get a glimpse of the presence of null values in each of the DataFrames. 

-- **Price DF.info:**

All columns had no null values in their rows.

```python
# Info of the 3 DataFrames
# Airbnb price

airbnb_price.info()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_7.png)

-- **Room Type DF.info:**

Null traces were observed in the 'Description' column as the number of non-null counts was less and did not tally with that of the 'Listing ID' and 'Room Type' columns.

```python
# Airbnb room type info 

airbnb_room_type.info()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_8.png)

-- **Review DF.info:**

Similar to the Room Type situation, the 'Host Name' column of the Review DF appeared to have some null values contained in its rows.

```python
# Airbnb review info

airbnb_review.info()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_9.png)

---

* **Accessing All Columns in the DataFrames:**

By using the '.columns' function, all columns of the 3 DataFrames were displayed. From the view, it was clear that all DataFrames had a linking possibility with the 'Listing ID' column.

```python
# Accessing the columns of the 3 DataFrames
# Airbnb price

airbnb_price.columns
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_10.png)

```python
# Airbnb room type columns

airbnb_room_type.columns
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_11.png)

```python
# Airbnb review columns

airbnb_review.columns
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_12.png)

---

* **Rows and Columns Count:**

The total number of rows and columns was displayed using the '.shape' function. This function sums the number of rows and columns and does not specify the presence or absence of null values in the count.

```python
# Number of rows and columns for the 3 DataFrames
# Airbnb price

airbnb_price.shape
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_13.png)


```python
# Airbnb room type rows and columns number

airbnb_room_type.shape
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_14.png)


```python
# Airbnb review rows and columns number

airbnb_review.shape
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_15.png)

---

* **Data Type Check:**

To ensure consistency and ease of data manipulation, the data type of all DataFrames were assessed using '.dtypes'.

-- **Price DF.dtypes:**

The data type of the 'Price' column was displayed as 'object', which would affect data manipulation. For that reason, the column should be cleaned and the data type changed.

```python
# Checking for data types
# Airbnb price

airbnb_price.dtypes
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_16.png)

-- **Room Type DF.dtypes:**

All data types were accurate and had no issues in the Room Type DF.

```python
# Airbnb room type data types 

airbnb_room_type.dtypes
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_17.png)

-- **Review DF.dtypes:**

From the 'Last Review' column, the entries showed the review date, so the data type should be changed from 'object' to 'datetime'.

```python
# Airbnb review data types

airbnb_review.dtypes
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_18.png)

---

* **Neighbourhood Count (Price DF):**

The '.value_counts' function was used to show the distinct row entries and their count in the 'Neighbourhood' column. 

```python
# Counting the Airbnb price value according to neighbourhood

airbnb_price['nbhood_full'].value_counts()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_19.png)

* **Room Type Count (Room Type DF):***

Distinct entries of the 'Room Type' column were also displayed. Due to irregularities in the letters/cases, some information appeared more than once, although they had the same meaning. The column needed to be cleaned.

```python
# Counting the Airbnb room types

airbnb_room_type['room_type'].value_counts()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_20.png)
  
* **Host Name Count (Review DF):**

Host names were displayed, as Michael topped the list with 215 reviews.

```python
# Counting the hostname and their number of reviews

airbnb_review['host_name'].value_counts()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_21.png)

---

* **Copy of Data Frames:**

Copies of each dataframe were created to ensure that nothing tampers with the original data in the DataFrames during the cleaning process.

```python
# Creating a copy of all 3 DataFrames

airbnb_price_c = airbnb_price.copy()
airbnb_rm_type_c = airbnb_room_type.copy()
airbnb_review_c = airbnb_review.copy()
```

---

* **Null Values Check (Price DF):**

No indication of null values was observed in all columns when the Price DF was checked for null values.  

```python
# Checking the 3 DataFrames for null values
# Airbnb price null

airbnb_price_c.isnull().sum()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_23.png)

---

* **Null Values Check (Room Type DF):**

'Description' column of the Room Type DF had 10 null values in total when the DataFrame was checked for null values.

```python
# Airbnb room type null

airbnb_rm_type_c.isnull().sum()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_24.png)

* **Null Values Assessment (Room Type DF):**

The null values in the 'Description' column were further assessed.

```python
# Assessing the null rows in Airbnb room type descriptions

desc_null = airbnb_rm_type_c[airbnb_rm_type_c['description'].isnull()]
desc_null
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_25.png)

* **Null Values Replacement (Room Type DF):**

All null values in the 'Description' column were replaced with 'Not Available', and 'inplace = True' was used to effect the change in the Room Type DF. The null value replacement was successful, as the confirmation showed that there were 0 null values.

```python
# Replacing the null values in the description column with "Not Available"

airbnb_rm_type_c['description'].fillna('Not Available', inplace = True)
```

```python
# Confirming the null values in the room type description

airbnb_rm_type_c['description'].isnull().sum()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_27.png)

---

* **Null Values Check (Review DF):**

Upon assessing the Review DF for null values, it was observed that the 'Host Name' column had 8 null values.

```python
# Airbnb review null

airbnb_review_c.isnull().sum()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_28.png)

* **Null Values Assessment (Review DF):**

The null values of the 'Host Name' column were further assessed.

```python
# Assessing the null rows in the host name

host_null = airbnb_review_c[airbnb_review_c['host_name'].isnull()]
host_null
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Output_29.png)

* **Null Values Replacement (Review DF):**

All null values in the 'Host Name' column were replaced with 'Absent' and the changes were effected in the Review DF, using 'inplace = True'. Further confirmation showed that there were no more null values in the 'Host Name' column.

```python
# Replacing the null values in the host name with "Absent"

airbnb_review_c['host_name'].fillna('Absent', inplace = True)
```

```python
# Confirming the null values in the reviews' host name

airbnb_review_c.isnull().sum()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Replacing_Null_Dataset_3_Review.png)

---

* **Duplicates Check (All DataFrames):**

After checking all 3 DataFrames for duplicate values, no duplicate was found in any of the DataFrames.

```python
# Checking for duplicates
# Airbnb price

airbnb_price_c.duplicated().sum()
```

```python
# Airbnb room type duplicates

airbnb_rm_type_c.duplicated().sum()
```

```python
# Airbnb review duplicates

airbnb_review_c.duplicated().sum()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Duplicate_Checks_All_Datasets.png)

---

* **Room Type Column Uniformity (Lower Case):**

From the initial assessment of the 'Room Type' column in the Room Type DF, it was observed that the non-uniformity of the letters resulted in extra entries with the same meaning down the column. All cases were changed to lowercase to ensure uniformity so that Python would pick the distinct room types for analysis.

```python
# Make all letters lowercase in the room type

airbnb_rm_type_c['room_type'] = airbnb_rm_type_c['room_type'].str.lower()
airbnb_rm_type_c['room_type']
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Lower_Case_Room_Type.png)

After unifying the cases, the count of room types was done, and it was seen that there were 3 distinct room types.

```python
# Counting the Airbnb room types

airbnb_rm_type_c['room_type'].value_counts()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Value_Count_New_Dataset_2_Room_Type.png)

---

* **Column String Removal (Price DF):**

Recall that the 'Price' column had some string entries (dollars), which meant that the data type was not float, and hence it would be difficult to manipulate the column during analysis. The 'dollars' string was removed from the column.

```python
# Removing the "dollars" from the price column

airbnb_price_c['price'] = airbnb_price_c['price'].str.replace(' dollars', '')
airbnb_price_c
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Column_Split_String_Removal_Dataset_1_Price.png)

After extracting the string, the data type was changed to float for ease of data manipulation.

```python
# Changing the price data type to float

airbnb_price_c['price'] = airbnb_price_c['price'].astype('float')
airbnb_price_c['price'].dtype
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Datatype_to_Float_Dataset_1_Price.png)

## EDA
This section explored more insights from all DataFrames during the analysis.

* **Summary Statistics (Price DF):**

The count, mean, percentiles, minimum and maximum values of the 'Price' column were assessed.

```python
# Assessing the summary statistics for Airbnb price

airbnb_price_c['price'].describe()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Summary_Stat_Dataset_1_Price.png)

---

* **Histogram of the Prices:**
  
The histogram displays the frequency of data points in the 'Price' column. It is evident that most of the data points are between $0 - $1,000, and the histogram is right-skewed as the majority of the data points are on the left-hand side. 

```python
# Frequency of data points in the prices column

x = airbnb_price_c['price']

plt.hist(x, bins = 50)
plt.title('Histogram Showing the Frequency of Prices', pad = 20)
plt.show()
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Histogram_Dataset_1_Price.png)

---

* **Timeframe Covered in the Analysis:**

Before assessing the timeframe covered in the analysis, the 'Last Review' column was changed from 'object' to 'datetime' for ease of data manipulation.

```python
# Timeframe in the Airbnb review
# Changing the last_review data type to datetime

airbnb_review_c['last_review'] = pd.to_datetime(airbnb_review_c['last_review'])
```

```python
# Confirming the data type change

airbnb_review_c.dtypes
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Timeframe_Datatype_Change_Dataset_3_Review.png)

From the earliest date in the 'Last Review' column to the most recent date, the time frame was assessed. The earliest date was 01-01-2019, and the most recent date was 09-07-2019.

```python
# Assessing the first and last dates to see the time frame
# First date

first_date = airbnb_review_c['last_review'].dt.date.min()
first_date
```

```python
# Last date

last_date = airbnb_review_c['last_review'].dt.date.max()
last_date
```

```python
# Timeframe for the Airbnb review

print ("The time frame is between {} and {}.". format (last_date, first_date))
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Timframe_Solution_Dataset_3.png)

---

* **Joining the 3 DataFrames:**

An outer join was done on all 3 DataFrames using 'pd.merge' with the 'Listing ID' column as the major link on which the merge was done.

```python
# Joining the 3 DataFrames

# Merging the first 2 (price and room type) DataFrames
price_room = pd.merge(airbnb_price_c, airbnb_rm_type_c, how = 'outer', on = 'listing_id')

# Adding the last DataFrame
airbnb_merged = pd.merge(price_room, airbnb_review_c, how = 'outer', on = 'listing_id')

airbnb_merged
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Joining_All_Datasets.png)

---

* **Comparing the Airbnb Listing Prices to the Private Rental Market:**

This was done to see how the Airbnb listing measures against the private rental market. DataCamp gave a figure from 'Zumper.com' to evaluate the average cost of 1 bedroom apartment in NYC, which was given as $3,100.00.

```python
# Comparing the costs to the private rental market (online)
# According to Zumper, 1 1-bedroom apartment in NYC costs, on average, $3,100 per month.
# Prices in the DataFrame are per night

# Calculating the monthly price
airbnb_merged['price_per_month'] = airbnb_merged['price'] * 365/12

# Average of yearly price
avg_per_year = round(airbnb_merged['price_per_month'].mean(), 2)

print("Airbnb monthly costs are ${}, while the private rental market, it costs {}.". format (avg_per_year, '$3100.00'))
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Comparing_Cost_to_Private_Rental.png)

---

* **Price Range by Borough:**

By considering the classification based on boroughs, a new column, 'Borough', was created by splitting the 'Neighbourhood' column by the delimiter (,).

```python
# Price range by borough
# Borough - first part of the nbhood before the delimiter (,)
# Creating a new column known as borough

airbnb_merged['borough'] = airbnb_merged['nbhood_full'].str.split(',').str[0]
airbnb_merged
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Price_by_m_Borough_Merged_Datasets.png)

---

* **Average Price by Borough:**

The average price of the Airbnb listing was evaluated based on the 5 boroughs.

```python
# Checking the mean, sum, and count of price by borough

abmg = airbnb_merged.groupby('borough')['price'].agg(['mean', 'sum', 'median', 'count']).sort_values('mean', ascending = False)
abmg
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Avg_Price_Per_Borough_Merged_Datasets.png)

---

* **Summary Statistics by Borough:**

Further statistical analysis was done based on boroughs for the Airbnb price, and this also revealed the minimum and maximum prices per borough.

```python
# Summary statistics of the price by borough

abmgs = airbnb_merged.groupby('borough')['price'].describe().sort_values('mean', ascending = False)
abmgs
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Summary_Stat_by_Borough_Merged_Datasets.png)

---

* **Categorizing Borough According to Price Range:**

The Airbnb prices were categorized according to specified labels and bins/ranges: 'Budget: $0 - $69', 'Average: $70 - $175', 'Expensive: $176 - $350', 'Extravagant: greater than $350'. Although some boroughs had values greater than $4,000, the ranges assigned to the categories were done on the basis that the histogram of prices was positively skewed and most of the data points were on the left (between $0 - $1,000).

```python
# Categorizing borough according to the price range

labels = ['Budget', 'Average', 'Expensive', 'Extravagant']
bins = [0, 69, 175, 350, np.inf]

# Inserting price range as a new column
airbnb_merged['price_range'] = pd.cut(airbnb_merged['price'], labels = labels, bins = bins)

# Price range by borough
abmg_cat_grp = airbnb_merged.groupby(['borough', 'price_range'])['price_range'].count()
abmg_cat_grp
```

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Categorizing_Borough_by_Price_Range.png)

---

* **Plot of Revenue Generated by Borough:**

At this stage, the prices according to boroughs were compared.

```python
# Plotting the prices generated by the borough

x = top_borough.values
y = top_borough.index

# Setting the locale to format numbers with comma separators
locale.setlocale(locale.LC_NUMERIC, 'en_US.UTF-8')

bar_a = plt.barh(y, x, height = 0.5, color = 'lightgrey')

# Formatting labels with commas after every thousand from the second decimal place
formatted_labels = [locale.format_string('%.2f', value, grouping=True) for value in x]
plt.bar_label(bar_a, labels=formatted_labels, padding=10)


# Removing the spines of the plot
location = ['top', 'bottom', 'left', 'right']

for l in location:
    plt.gca().spines[l].set_visible(False)

plt.title('Revenue Generated by Borough', pad = 20)
plt.ylabel('Borough')
plt.xlabel("Price (in USD)")
plt.gca().patches[4].set_facecolor('#85542d')
plt.xticks([])
plt.show()
```

The horizontal bar plot showed that Manhattan led the other boroughs in generated revenue.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Plot_Show_Borough_Price.png)

## Conclusion 
* The average price per night for an Airbnb listing is approximately $142.00.
* Manhattan generated the highest revenue ($1,899,255.00) from Airbnb, compared to other boroughs in NYC.
* There were 3 distinct room types: 'entire home/apt', 'private room', and 'shared room'.
* Amongst all host names, Michael had the most reviews (215).
* The timeframe covered in the analysis was between 01-01-2019 and 09-07-2019.
* The least revenue ($22,974.00) by borough came from Staten Island.
* Airbnb monthly listing price ($4,312.41) was more expensive when compared to that of the private rental market ($3,100.00).
* After categorizing the boroughs by price range, extravagant had the fewest offers (despite having the highest price range).

## Recommendation
* The Review DF only had host names and last review (date) columns. Ratings should be included in the future to understand the customer satisfaction rate and see ways where the Airbnb services can be improved. 
* More data should be provided that can show more insight as to why boroughs like Staten Island were the least in terms of generated revenue. It could be as a result of low online presence on social media, poor nightlife in the boroughs or other attractions like game nights or nearness to facilities like the airport that could have made the difference.
* Shows and other social activities should be encouraged in the boroughs that had lesser turnout in revenue to boost income.

