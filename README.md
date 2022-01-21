# NFLPicker
This project was created to demonstrate my ability to scrape data from the web, clean the data, and load the data into a cloud database for analytics.

The first tassk here was to extract the data I needed from a reliable source. I found pro-football-reference.com to be a great site to get my data from as everything I needed was neatly organized in tables, and broken down by team and year. They had data avaialable for the years 2018-2021 for each team. To get the this data, I used requests and BeautifulSoup. This made it relatively easy to find the tags in the HTML code that corresponded to the data I was trying to collect. The steps here were as follows:

 - Create a dictionary with key-value pairs for each team and year
 - Use a for loop to iterate over the dictionary to pull from each unique URL (team/year)
 
The next task was to organize the data I was pulling. I used pandas here to create a dataframe for each team/year I was pulling from the website, and cleaned the data as I went. This was done in the same for loop that was used to get the unique URL's created to pull from. These were the steps for this task:
 
 - Define column names
 - Build DF with empty rows and specified columns
 - Fill DF using an embedded for loop to iterate over each row and column in the website's tables
 - Clean the data in the newly created DF's by changing values to make the DF's more readable, dropping unnecessary columns, and adding a "week" column as another label

The final task was loading everything into GCP BigQuery. The intention of going directly to BigQuery is to allow future analytics on the data with SQL, potential for machine learning using BigQueryML, and potential for visualizations. The steps for this task were as follows:

- In same for loop, use "name" to create unique parquet file for each team/year DF, which iterates over values in team dictionary to fill in with previously identified naming scheme. This "name" is also used as the table name in GCP BigQuery, using the same method.
- Connect to BigQuery client
- Write files to BigQuery

After my code ran, I now have a seperate table for each team/year in GCP BigQuery, and can now run SQL for machine learning, visualizations, and further analysis.
