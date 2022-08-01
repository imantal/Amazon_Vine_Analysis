# Amazon_Vine_Analysis
## Overview of the Analysis
The purpose of this project was to analyze Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers to receive reviews for their products. Companies pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.
For this project, first, PySpark was used to perform the ETL process to extract the dataset, transform the data, connect to an AWS Relational Database (RDS) instance, and load the transformed data into pgAdmin. Next, Pandas was used to determine if there is any bias toward favorable reviews from Vine members in the dataset. 

## Extract, Transform and Load the Data
From almost 50 available datasets, the one that contained about 15 million reviews for wireless products was selected. PySpark and the cloud-based notebook, Colab were used to get access to the dataset and convert it into a dataframe shown below. Four tables, each containing different set of data extracted from the dataset were created for further analyses as shown below: customer table, product table, review table and vine table. The created tables were then loaded into the AWS RDS Postgress tables.

![image](https://user-images.githubusercontent.com/103223944/182052127-bf3bec2c-611d-4409-97ef-ace596038a33.png)

![image](https://user-images.githubusercontent.com/103223944/182052186-be88d976-a7ac-44ff-8fae-83e742ef9739.png)

![image](https://user-images.githubusercontent.com/103223944/182052195-90ad2d8c-8156-4d35-97a9-04acd65c8fd9.png)

![image](https://user-images.githubusercontent.com/103223944/182052229-f68c132c-0f20-42b0-a3c4-a098afdc1173.png)

![image](https://user-images.githubusercontent.com/103223944/182052236-9ec6bc60-4808-48b1-a18a-860933aab510.png)

## Analysis of the Customer Reviews
Once the dataframes were uploaded to the AWS Postgress database, pgAdmin was used to review the tables and export the vine table as a CSV file so it could be used for further analysis. Pandas is used to analyze the data and determine if there was any bias toward favorable reviews from Vine members in the dataset. First, the vine table was filtered to retrieve all the rows where the total votes count was equal to or greater than 20 to pick reviews that were more likely to be helpful. Second, the data was further filtered to retrieve all the rows where the number of helpful votes divided by total votes was equal to or greater than 50%. Third, the data was again filtered to retrieve all the rows where a review was written as part of the Vine program (paid). Fourth, similarly, the data was filtered to retrieve all the rows where the review was not part of the Vine program (unpaid) and finally, the total number of reviews, the number of 5-star reviews, and the percentage of 5-star reviews for the two types of review (paid vs unpaid) were determined. The following snapshots show the final tables for the paid and unpaid reviews along with the total number of reviews, 5-star reviews and the percentage of the 5-star reviews for each category.

![image](https://user-images.githubusercontent.com/103223944/182052277-276466a9-74ae-4446-9f13-122c79550a00.png)

![image](https://user-images.githubusercontent.com/103223944/182052292-3ad8e01a-5e31-4eee-a677-9123f91e05a9.png)

![image](https://user-images.githubusercontent.com/103223944/182052304-8f7abe3b-46e6-43ee-a84b-4c735e620a8a.png)

## Sumamry
The summary of the data analysis is presented in the table below. It is noted that the percentage of the 5-star reviews is about 10% larger for the unpaid reviews compared to paid reviews and therefore there is no bias toward favorable reviews from the Vine members (paid reviews) in the dataset. Similar analysis could be performed for the 4- and 3-star reviews to have a more complete picture of the paid and unpaid reviews.  Additionally, similar analysis could be done for sub-categories of wireless products to evaluate the paid and unpaid reviews for each category. 

![image](https://user-images.githubusercontent.com/103223944/182052038-8c7f7236-10e5-4987-8b27-d8cab1e59a3c.png)

