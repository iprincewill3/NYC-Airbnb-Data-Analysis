# NYC-Airbnb-Data-Analysis

![](New_York_City_Photo.jpg)

## Introduction

Well known for having the 'Statue of Liberty' which was gifted from France, New York City (NYC) is the most populous city in the United States of America, with 5 boroughs namely; Bronx, Brooklyn, Manhattan, Queens, and Staten Island. The NYC Airbnb Data Analysis is a project aimed at accessing the Airbnb listing in New York City, and also analyzing how each borough compares to each other in terms of their prices. In total, 3 datasets were involved in order to analyze the city's response to the Airbnb listings. The datasets were cleaned and analyzed, using Python (on Jupyter Notebook) and the outcome was visualized.

**_Disclaimer_**: _The NYC image (just before the introduction) was gotten from sonnenklar.tv and has only been used for illustrative purposes. Also, the datasets do not represent the city, and have been utilized to demonstrate the various functions in Python._

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
In total, 3 datasets were used for this analysis and all of them were sourced from [DataCamp](https://www.datacamp.com). The datasets have been uploaded as part of the files on this repository. The 3 datasets were Price, Room Type, and Review datasets and each had 25,209 rows and 3 columns.

## Data Cleaning
Python was the technical skill used in the data cleaning and EDA all through this analysis. All codes were written and run on Jupyter Notebook. All Python library packages that were used include Pandas, Numpy, Matplotlib, Seaborn, Datetime, and Locale.
The following steps were covered in the course of cleaning the 3 datasets that were involved in this analysis:

* **Importing Python Libraries:**

First step on Jupyter Notebook was to import the Python libraries before accessing, cleaning, and transforming the datasets.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Importing_Python_Libraries.png)

---

* **Importing and Loading the Datasets:**

Since there were 3 datasets for this project and they all had different formats, all were imported individually. The first dataset (Price), a csv file was imported using 'pd.read_csv'. 

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Importing_Dataset_1_Price.png)

The second dataset (Room Type) was imported as an excel file due to the '.xlsx' extension. 

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Importing_Dataset_2_Room_Type.png)

Lastly, the third dataset (Review), a tab seperated file, was imported using 'pd.read_csv' but with the inclusion of '\t' as the seperator or delimeter.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Importing_Dataset_3_Review.png)

---

* **Viewing All DataFrames:**

After importing and loading all 3 datasets and using them to create DataFrames, their first 5 rows were viewed in a combined format, using '.head()' to show the first 5 rows, and '\n' to move to a new line after displaying the rows of each DataFrame. For the purpose of this documentation, the DataFrames will be given an alias.

-- **Airbnb Price** alias **Price DF**

-- **Airbnb Room Type** alias **Room Type DF**

-- **Airbnb Review** alias **Review DF**

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Viewing_3_datasets_head.png)

---

* **DataFrames Information:**

This function was carried out to display the columns in all DataFrames, the count of non-null rows, and the data types of all columns. By using the '.info' function, it was possible to get a glimpse of the presense of null values in each of the DataFrames. 

-- **Price DF.info:**

All columns had no null values in their rows.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Info_Dataset_1_Price.png)

-- **Room Type DF.info:**

Null traces were observed in the 'Description' column as the number of non-null count was lesser and did not tally with that of the 'Listing ID' and 'Room Type' columns.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Info_Dataset_2_Room_Type.png)

-- **Review DF.info:**

Similar to the Room Type situation, the 'Host Name' column of the Review DF appeared to have some null values contained in its rows.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Info_Dataset_3_Review.png)

---

* **Accessing All Columns in the DataFrames:**

By using the '.columns' function, all columns of the 3 DataFrames were displayed. From the view, it was clear that all DataFrames had a linking possibility with the 'Listing ID' column.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Column_Checks_All_Datasets.png)

---

* **Rows and Columns Count:**

Total number of rows and columns were displayed using the '.shape' function. This function sums the number of rows and columns and does not specify the presence or absence of null values in the count.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Rows_and_Columns_Numbers_All_Datasets.png)

---

* **Data Type Check:**

To ensure consistency and ease of data manipulation, the data type of all DataFrames were assessed using '.dtypes'.

-- **Price DF.dtypes:**

The data type of the 'Price' column was displayed as 'object' which would affect data manaipulation. For that reason, the column should be cleaned and the data type changed.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Datatype_Dataset_1_Price.png)

-- **Room Type DF.dtypes:**

All data types were accurate and had no issues in the Room Type DF.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Datatype_Dataset_2_Room_Type.png)

-- **Review DF.dtypes:**

From the 'Last Review' column, the entries showed the review date so the data type should be changed from 'object' to 'datetime'.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Datatype_Dataset_3_Review.png)

---

* **Neighbourhood Count (Price DF):**

The '.value_counts' function was used to show the distinct row entries and their count in the 'Neighbourhood' column. 

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Value_Count_Dataset_1_Nbhood.png)

* **Room Type Count (Room Type DF):***

Distinct entries of the 'Room Type' column were also displayed. Due to irregularities of the letters/cases, some information appeared more than once although they had the same meaning. The column needed to be cleaned.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Value_Count_Dataset_2_Room_Type.png)
  
* **Host Name Count (Review DF):**

Host names were displayed, as Michael topped the list with 215 reviews.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Value_Count_Dataset_3_Host_Name.png)

---

* **Copy of Data Frames:**

Creating copies for all DataFrames was done to ensure that nothing tampers with the original data in the DataFrames during the cleaning process.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Copies_All_Datasets.png)

---

* **Null Values Check (Price DF):**

No indication of null values were observed in all columns when the Price DF was checked for null values.  

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Null_Check_Dataset_1_Price.png)

---

* **Null Values Check (Room Type DF):**

'Description' column of the Room Type DF had 10 null values in total when the DataFrame was checked for null values.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Null_Check_Dataset_2_Room_Type.png)

* **Null Values Assessment (Room Type DF):**

The null values in the 'Description' column were further assessed.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Accessing_Null_Dataset_2_Room_Type.png)

* **Null Values Replacement (Room Type DF):**

All null values in the 'Description' column were replaced with 'Not Available' and 'inplace = True' was used to effect the change in the Room Type DF. The null value replacement was successful as the confirmation showed that there were 0 null values.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Replacing_Null_Dataset_2_Room_Type.png)

---

* **Null Values Check (Review DF):**

Upon assessing the Review DF for null values, it was observed that the 'Host Name' column had 8 null values.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Null_Check_Dataset_3_Review.png)

* **Null Values Assessment (Review DF):**

The null values of the 'Host Name' column were further assessed.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Accessing_Null_Dataset_3_Review.png)

* **Null Values Replacement (Review DF):**

All null values in the 'Host Name' column were replaced with 'Absent' and the changes were effected in the Review DF, using 'inplace = True'. Further confirmation showed that there were no more null values in the 'Host Name' column.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Replacing_Null_Dataset_3_Review.png)

---

* **Duplicates Check (All DataFrames):**

After checking all 3 DataFrames for duplicate values, no duplicate was found in any of the DataFrames.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Duplicate_Checks_All_Datasets.png)

---

* **Room Type Column Uniformity (Lower Case):**

From the initial assessment of the 'Room Type' column in the Room Type DF, it was observed that the non-uniformity of the letters resulted in extra entries with the same meaning down the column. All cases were changed to lower case to ensure uniformity so that Python would pick the distinct room types for analysis.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Lower_Case_Room_Type.png)

After unifying the cases, the count of room types was done and the it was seen that there were 3 distinct room types.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Value_Count_New_Dataset_2_Room_Type.png)

---

* **Column String Removal (Price DF):**

Recall that the 'Price' column had some string entries (dollars) which meant that the data type was not float and hence it would be difficult to manipulate the column during analysis. The 'dollars' string was removed from the column.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Column_Split_String_Removal_Dataset_1_Price.png)

After extracting the string, the data type was changed to float for ease of data manipulation.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Datatype_to_Float_Dataset_1_Price.png)

## EDA
This section explored more insights from all DataFrames during the analysis.

* **Summary Statistics (Price DF):**

The count, mean, percentiles, minimum and maximum values of the 'Price' column were assessed.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Summary_Stat_Dataset_1_Price.png)

---

* **Histogram of the Prices:**
  
The histogram displays the frequency of data points in the 'Price' column. It is evident that most of the data points are between $0 - $1,000, and the histogram is right_skewed as majority of the data points are on the left-hand side. 

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Histogram_Dataset_1_Price.png)

---

* **Timeframe Covered in the Analysis:**

Before assessing the timeframe covered in the analysis, the 'Last Review' column was changed from 'object' to 'datetime' for ease of data manipulation.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Timeframe_Datatype_Change_Dataset_3_Review.png)

From the earliest date in the 'Last Review' column, to the most recent date, the time frame was assessed. The earliest date was 01-01-2019 and the most recent date was 09-07-2019.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Timframe_Solution_Dataset_3.png)

---

* **Joining the 3 DataFrames:**

An outer join was done on all 3 DataFrames using 'pd.merge' with the 'Listing ID' column as the major link on which the merge was done.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Joining_All_Datasets.png)

---

* **Comparing the Airbnb Listing Prices to the Private Rental Market:**

This was done to see how the Airbnb listing measures to the private rental market. DataCamp gave a figure from 'Zumper.com' to evaluate the average cost of 1 bedroom apartment in NYC which was given as $3,100.00.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Comparing_Cost_to_Private_Rental.png)

---

* **Price Range by Borough:**

By considering the classification based on boroughs, a new column, 'Borough' was created by spliting the 'Neighbourhood' column by delimeter (,).

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Price_by_m_Borough_Merged_Datasets.png)

---

* **Average Price by Borough:**

The average price of the Airbnb listing was evaluated based on the 5 boroughs.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Avg_Price_Per_Borough_Merged_Datasets.png)

---

* **Summary Statistics by Borough:**

Further statistical analysis was done on the basis of boroughs for the Airbnb price, and this also revealed the minimum and maximum prices per borough.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Summary_Stat_by_Borough_Merged_Datasets.png)

---

* **Categorizing Borough According to Price Range:**

The Airbnb prices were categorized accordinig to specified labels and bins/ranges; 'Budget: $0 - $69', 'Average: $70 - $175', 'Expensive: $176 - $350', 'Extravagent: greater than $350'. Although some boroughs had values greater than $4,000, the ranges assigned to the categories were done on the basis that the histogram of prices was positively skewed and most of the data points were on the left (between $0 - $1,000).

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Categorizing_Borough_by_Price_Range.png)

---

* **Plot of Revenue Generated by Borough:**

At this stage, the prices according to boroughs were compared.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Plot_Code_Borough_Price.png)

The horizonatal bar plot showed that Manhattan led the other boroughs in generated revenue.

![](https://github.com/iprincewill3/NYC-Airbnb-Data-Analysis/blob/main/Plot_Show_Borough_Price.png)

## Conclusion 
* The average price per night for an Airbnb listing is approximately $142.00.
* Manhattan generated the highest revenue ($1,899,255.00) from Airbnb, compared to other boroughs in NYC.
* There were 3 distinct room types; 'entire home/apt', 'private room', and 'shared room'.
* Amongst all host names, Michael had the most reviews (215).
* The timeframe covered in the analysis was between 01-01-2019 and 09-07-2019.
* The least revenue ($22,974.00) by borough came from Staten Island.
* Airbnb monthly listing price ($4,312.41) was more expensive when compared to that of the private rental market ($3,100.00).
* After categorizing the boroughs by price range, extravagant had least offers (despite having the highest price range).

## Recommendation
* The Review DF only had host names and last review (date) columns. Ratings should be included in the future to understand customer satisfaction rate and see ways where the Airbnb services can be improved. 
* More data should be provided that can show more insight as to why boroughs like Staten Island were the least in terms of generated revenue. It could be as a result of low online presence on social media, poor night life in the boroughs or other attractions like game nights or nearness to facilities like the airport that could have made the difference.
* Shows and other social activities should be encouraged in the boroughs that had lesser turnout in revenue to boost income.

