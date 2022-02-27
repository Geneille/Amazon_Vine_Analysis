# Amazon_Vine_Analysis

## Overview and Objective

A lot of information, also know as "Big Data", is available regarding consumer shopping habits and preferences. In addition, information is also available regarding the product, including product reviews by the consumer or hired groups (who are paid a fee to use and review the product). The reviews from the hired groups may or may not be bias.

Amazon offers a service, referred to as Amazon Vine program, that allows manufacturers and publishers to receive reviews for their products often written by members of the paid Amazon Vine program. However, not all products/sub categories of products fall into the program.


After randomly selecting an Amazon Review dataset, the two goals of this project were:

* to perform the ETL process to extract and transform the data from the dataset, connect to an AWS RDS instance, and load the transformed data into pgAdmin. 
* use PySpark to determine if there is any bias toward favorable reviews from Vine members in the selected dataset.

## Analysis 

The general steps followed to complete the aim were:

1. A data set was selected from Amazon Review datasets.
    * For this analysis the dataset selected was "Digital Video Games"
2. A new database was created with Amazon RDS. 
3. The databse was linked to pgAdmin via the Amazon RDS server.
4. A query was written in pgAdmin to create 4 tables to hold the extracted data from the amazon dataset.
5. Using Google Colab Notebook, code was written to: extract the data from the datset into a DataFrame; transform the DataFrame into four separate DataFrames that match the table schema in pgAdmin; and load the transformed data into the appropriate tables. 
6. Queries were then written in pgAdmin to confirm that the data was uploaded.
7. The vine_table data was then used to analyze and summarize the review data for the digital video games dataset selected. This was done using pyspark in Google Colab Notebook.


## Results 

The following images shows the loaded data into the different tables after the ETL process. 

Figure 1: The customers_table

Figure 2: The products_table

Figure 3: The review_id_table

Figure 4: The vine_table 

The review data in the vine_table was then further analyzed. Figure 5 below shows the vine_table dataframe. The table was filtered as needed to make deductions regarding review bias by the Vine program. 

1. How many Vine reviews and non-Vine reviews were there? 

    * From the dataset selected all the data was non-Vine reviews. Figure 6 shows the empty dataframe for the vine reviews. Figure 7 shows the summary count.



2. How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?

    * Of the 1685 helful reviews, 631 that had a five star rating, all of which were non-vine revews (100%). As mentioned above, for this dataset none was vine reviewed (0%). Figure 7 shows the summary output from pyspark. 

## Summary

Digitial video games was not part of the Vine program (unpaid), therefore there is no positivity bias. In general however, (say for example considering another dataset), if the calculated data showed that the percent for the 5 star review that was paid was much greater than the unpaid 5 star review then this would be a case where perphaps there is positivity bias.

An alternate analysis that can be used with the dataset could be to utilize verified_purchase and run the same analysis with this data instead of the vine data and see the percent outcomes.