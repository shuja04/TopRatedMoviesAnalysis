# Top Rated Movies Analysis

Project Description:

This project analyzes and visualizes a dataset of top-rated movies using MySQL for data handling and Power BI for visualization. It includes data cleaning, exploration, and insightful visualizations.

## Dataset
The dataset contains the following columns:
- **Popularity**: A measure of the movie's popularity.
- **Release Date**: The date the movie was released.
- **Title**: The title of the movie.
- **Vote Average**: The average rating of the movie (1 to 10).

## Technologies Used
- MySQL for data processing
- Power BI for data visualization

## Data Import Instructions
1. Create a database in MySQL.
2. Create database project_movies;
3. Use project_movies;
4. Import the dataset using: Table Data Import Wizard.

## Analysis Steps
1. Data cleaning and handling of missing values.
2. SQL queries to extract insights.
3. Visualization in Power BI.

## Data validation on mySQL:

use project_movies;

select * from movies
order by popularity desc;


-- 1. Missing Values Check <br />
    SELECT <br />
    COUNT(*) AS total_movies, <br />
    SUM(CASE WHEN popularity IS NULL THEN 1 ELSE 0 END) AS missing_popularity, <br />
    SUM(CASE WHEN release_date IS NULL THEN 1 ELSE 0 END) AS missing_release_date, <br />
    SUM(CASE WHEN title IS NULL THEN 1 ELSE 0 END) AS missing_title, <br />
    SUM(CASE WHEN vote_average IS NULL THEN 1 ELSE 0 END) AS missing_vote_average <br />
FROM movies;

-- 2. Basic Statistics

SELECT <br />
    COUNT(*) AS total_movies,<br />
    AVG(vote_average) AS average_vote,<br />
    MAX(vote_average) AS highest_vote,<br />
    MIN(vote_average) AS lowest_vote<br />
FROM movies;

-- 3. changing data types

alter table movies <br />
add column dates date;
<br />
update movies set dates = str_to_date(release_date, '%m/%d/%Y');<br />

alter table movies <br />
drop column dates;
<br />
select * from movies;
<br />
alter table movies change dates release_date date;


-- 4. Trends Over Time

SELECT <br />
    year(release_date) as release_year,<br />
    AVG(vote_average) AS average_rating<br />
FROM movies<br />
GROUP BY release_year<br />
ORDER BY release_year;<br />

-- 5. Most Popular Movies

select popularity, title, vote_average from movies order by popularity desc limit 10;

## Visualizations

1. New Card used for Total Number of Movies and Average Votes.
   - Created Measures for the above two components.
  
2. Created Table for the entire list of Movies, their Popularity and Votes average.

3. Created Clustered Bar Chart for Top 10 Most Popular Movies.

4. Created Line Chart for Average Ratings Over Years.

5. Added Slicers for the time period measured in years.

   
## Conclusion
This project demonstrates the use of SQL and Power BI for data analysis and visualization, providing valuable insights into movie trends and ratings.

![image](https://github.com/user-attachments/assets/9859617c-65fb-4371-9b03-7529a0817321)




