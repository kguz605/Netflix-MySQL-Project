# Netflix-MySQL-Project
  Exploring a Netflix data set from Kaggle

#Understand the data that's in the netflix table
#Type of content: Movie vs TV Show, Country the show or movie is from etc;

SELECT *
FROM netflix
LIMIT 5;

#How many rows in this table?
#8788 rows

SELECT COUNT(*)
FROM netflix;

#How many tv shows in this table?
#2673 TV Shows in this table

SELECT COUNT(type ) AS Total_TV_SHOWS
FROM netflix
WHERE type = 'TV Show';

#How many movies in this table?
#6115 Movies in this table

SELECT COUNT(type) AS Total_Movies
FROM netflix
WHERE type = 'Movie';

#There are more movies than tv shows on Netflix


#A count of TV shows per country
#The United States has the most tv shows on Netflix
#Top 5 countries with the most TV Shows on Netflix: US,(Unidentified),UK,Japan,South Korea

SELECT country, COUNT(type) AS Total_TV_Shows
FROM netflix
WHERE type = 'TV Show' 
GROUP BY country 
ORDER BY Total_TV_Shows DESC
LIMIT 5;



#A count of Movies per Country
#US has the most movies on Netflix
#Top 5 countries with the most movies on Netflix: US, INDIA, N/A, UK, cANADA

SELECT country, COUNT(type) AS Total_Movies
FROM netflix
WHERE type = 'Movie'
GROUP BY country 
ORDER BY Total_Movies DESC
LIMIT 5;


#TV Shows on Netflix with more than 1 season

SELECT title, duration
FROM netflix
WHERE type = 'TV Show'
	AND duration > '1 Season';
    
#882 shows on netflix with more than 1 season

SELECT COUNT(title)
FROM netflix
WHERE type = 'TV Show'
	AND duration > '1 Season';
    
#All movies on Netflix that were release in 2020

SELECT title
FROM netflix
WHERE type = 'Movie'
	AND release_year = 2020;

#The movie on neflix with the earliest release date
#1942 was the earliest release date for a movie on Netflix

SELECT MIN(release_year)
FROM netflix
WHERE type = 'Movie';

#The movies were Prelude to War and Battle of Midway

SELECT title, release_year
FROM netflix
WHERE release_year = 1942
	AND type = 'Movie';

#The movie on neflix with the most recent release date
#2021

SELECT MAX(release_year)
FROM netflix
WHERE type = 'Movie';

#Which movies on Netflix were released in 2021

SELECT title, release_year, listed_in, description
FROM netflix
WHERE release_year = 2021
	AND type = 'Movie';

#275 movies released in 2021    

SELECT COUNT(release_year)
FROM netflix
WHERE release_year = 2021
	AND type = 'Movie';

#List of Action movies released in 2021

SELECT title, listed_in
FROM netflix
WHERE release_year = 2021
	AND type = 'Movie'
    AND listed_in LIKE '%Action%';
    

#How many of the movies were action  

#37 movies
SELECT COUNT(title)
FROM netflix
WHERE release_year = 2021
	AND type = 'Movie'
    AND listed_in LIKE '%Action%';


#A Count of directors per country

SELECT country, COUNT(director ) AS Total_Directors
FROM netflix
GROUP BY country
ORDER BY Total_Directors DESC;


    

