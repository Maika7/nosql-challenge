# nosql-challenge
Eat Safe, Love: Food Hygiene Ratings Analysis
This project is part of a data analysis challenge to evaluate food hygiene ratings across establishments in the United Kingdom. The analysis was conducted for a food magazine, Eat Safe, Love, to help journalists and food critics identify noteworthy establishments for their articles.

Table of Contents
Overview
Technologies Used
Dataset
Assignment Breakdown
Part 1: Database and Notebook Setup
Part 2: Database Updates
Part 3: Exploratory Analysis
Results
Usage Instructions
License
Overview
This project evaluates food hygiene ratings provided by the UK Food Standards Agency. The goal is to explore and analyze the dataset to:

Identify establishments with specific hygiene and rating attributes.
Perform geographic proximity analysis.
Answer key questions posed by Eat Safe, Love editors.
The project consists of three parts:

Setting up the database and ensuring the dataset is correctly imported.
Performing updates to reflect new or corrected data.
Conducting exploratory analysis to answer specific questions.
Technologies Used
MongoDB: A NoSQL database for storing and querying the dataset.
Python: For data manipulation and analysis.
pymongo: Python library for MongoDB interactions.
pandas: For data handling and analysis.
pprint: For structured printing of query results.
Jupyter Notebook: For interactive data analysis.
Dataset
The dataset contains hygiene ratings data for various establishments in the UK, including information such as:

Business Name
Business Type
Hygiene Scores
Geolocation (latitude, longitude)
Local Authority Details
The data was provided in a JSON file (establishments.json) and imported into a MongoDB collection named establishments.

WorkFlow Breakdown
Part 1: Database and Notebook Setup
Imported the establishments.json file into MongoDB using the following command:
css
Copy code
mongoimport --db uk_food --collection establishments --file establishments.json --jsonArray
Verified the successful import of the data.
Connected to the uk_food database and assigned the establishments collection to a variable for analysis.

Part 2: Database Updates
Adding a New Establishment:

Added "Penang Flavours" (a halal restaurant in Greenwich) to the database.
Updated its BusinessTypeID field to reflect its correct business type.
Removing Unwanted Data:

Removed all establishments with the LocalAuthorityName of "Dover" from the database.
Data Cleaning:

Converted RatingValue to integers where applicable.
Set non-numeric RatingValue entries (e.g., "Pass") to null.
Ensured latitude and longitude fields were stored as numeric values.
Part 3: Exploratory Analysis
Performed detailed analysis to answer the following questions:

Which establishments have a hygiene score equal to 20?

Filtered and counted matching establishments.
Displayed results in a Pandas DataFrame.
Which establishments in London have a RatingValue greater than or equal to 4?

Used regex to match establishments in London.
Filtered by RatingValue and presented the results.
What are the top 5 establishments near "Penang Flavours" with RatingValue of 5, sorted by hygiene score?

Conducted proximity-based analysis using geolocation data.
Sorted results by hygiene score.
How many establishments in each Local Authority area have a hygiene score of 0?

Used MongoDB's aggregation pipeline to group and sort results.
Displayed the top 10 Local Authority areas with the highest counts.
Results
Key insights derived from the analysis:

Identified establishments with poor hygiene scores for potential follow-up.
Found top-rated establishments near "Penang Flavours" with low hygiene scores.
Highlighted Local Authority areas with the highest counts of hygiene score 0 establishments.
The analysis provides valuable information for Eat Safe, Love editors to decide which establishments to feature or avoid.

Usage Instructions
Clone the Repository:

bash
Copy code
git clone <https://github.com/Maika7/nosql-challenge.git>
cd <"C:\nosql-challenge">
Ensure Dependencies Are Installed:

Copy code
pip install pymongo pandas
Run the Jupyter Notebooks:

Open NoSQL_setup_starter.ipynb to perform database setup and data import.
Open NoSQL_analysis_starter.ipynb for exploratory analysis.
Run MongoDB:

Ensure MongoDB is running on your machine before executing the notebooks:
arduino
Copy code
mongod --dbpath="C:/data/db"
