# Netflix_movies
<img width="603" alt="Screenshot 2023-11-08 052122" src="https://github.com/Olauryn/Netflix_movies/assets/118401566/624a9871-3733-4d01-bc9e-852162264416">

## PROBLEM STATEMENT
Netflix! What started in 1997 as a DVD rental service has since exploded into one of the largest entertainment and media companies.
Using the Netflix data explore the dataset to see if you can see whether movie durations are getting shorter. 
and explain some of the contributing factors, if any.

### ABOUT DATATSET
The data
netflix_data.csv

Column:	Description

show_id: The ID of the show

type: Type of show

title: Title of the show

director: Director of the show

cast: Cast of the show

country: Country of origin

date_added:	Date added to Netflix

release_year:	Year of Netflix release

duration:	Duration of the show in minutes

description:	Description of the show

genre:	Show genre


## QUESTIONS

### SOLUTION

**pandas and matplotlib**
import pandas as pd
import matplotlib.pyplot as plt


**Load netflix csv data**

netflix_df = pd.read_csv("netflix_data.csv")

**Filter data to remove TV shows**

netflix_subset = netflix_df[netflix_df["type"] != "TV Show"]

**Investigate the Netflix movie data, keeping only the columns "title", "country", "genre", "release_year", "duration"**

netflix_movies = netflix_subset[['title', 'country', 'genre', 'release_year', 'duration']]

**filter netflix_movies to find the movies shorter than 60 minutes**

short_movies = netflix_movies[netflix_movies["duration"] < 60]

**Using a for loop and if/elif statements, iterate through the rows of netflix_movies and assign colors of your choice to four genre groups**

colors = []

for lab, row in netflix_movies.iterrows():

    if row["genre"] == "Children":
    
        colors.append("purple")
        
    elif row["genre"] == "Documentaries":
    
        colors.append("Green")
        
    elif row["genre"] == "Standup":
    
        colors.append("Black")
        
    else:
    
        colors.append("Others")
        
**create a scatter plot**

fig = plt.figure(figsize=(12, 8))  

plt.scatter("release_year", "duration", data=netflix_movies)  

plt.xlabel("Release year")

plt.ylabel("Duration (min)")

plt.title("Movie Duration by Year of Release")

plt.show()

<img width="513" alt="Screenshot 2023-11-08 052150" src="https://github.com/Olauryn/Netflix_movies/assets/118401566/d279c52e-fba1-443f-9fc5-3c7f162d65d1">




answer = "maybe"

From the scatter plot, it is not certain if the average movies duration has declinedn or not as we have clusters below and above the 60 minutes duration
