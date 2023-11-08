# Netflix_movies
<img width="603" alt="Screenshot 2023-11-08 052122" src="https://github.com/Olauryn/Netflix_movies/assets/118401566/624a9871-3733-4d01-bc9e-852162264416">

## PROBLEM STATEMENT
Netflix! What started in 1997 as a DVD rental service has since exploded into one of the largest entertainment and media companies.
Given the large number of movies and series available on the platform, it is a perfect opportunity to flex your exploratory data analysis skills and dive into the entertainment industry.
Our friend has also been brushing up on their Python skills and has taken a first crack at a CSV file containing Netflix data.
They believe that the average duration of movies has been declining. Using your friends initial research, you'll delve into the Netflix data to see if you can determine whether movie lengths are actually getting shorter 
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
