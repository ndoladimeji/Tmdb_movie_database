> **Note**: I worked with the _movie dataset_. This dataset contains information about 10,000 movies collected from The Movie Database (TMDb), including user ratings and revenue. I renamed the dataset as "movies_db.csv".


# Project: Investigate a Dataset - [TMDb movie data]

## Table of Contents
<ul>
<li><a href="#intro">Introduction</a></li>
<li><a href="#wrangling">Data Wrangling</a></li>
<li><a href="#eda">Exploratory Data Analysis</a></li>
<li><a href="#conclusions">Conclusions</a></li>
</ul>


<a id='intro'></a>
## Introduction

### Dataset Description 

> The movie dataset contains information about 10,000 movies collected from The Movie Database (TMDb), including columns: 
 1   id:                    movie id, unique to individual movie
 2   imdb_id:               movie id provided by the imdb database, unique to individual movie 
 3   popularity:            popularity of the movie described in figures
 4   budget:                budget proposed for the movie making 
 5   revenue:               revenue generated from selling the movie 
 6   original_title:        title given to the movie
 7   cast:                  list of movie actors and actresses 
 8   homepage:              movie homepage
 9   director:              director of the movie
 10  tagline:               movie tagline
 11  keywords:              movie keywords (hashtags)
 12  overview:              overview of the movie
 13  runtime:               the length of the film plus the length of the ending credits 
 14  genres:                genre the movie belongs to
 15  production_companies:  company producing the movie
 16  release_date:          date movie was released
 17  vote_count:            count of votes casted for movie 
 18  vote_average:          average of votes casted for movie
 19  release_year:          year movie was released 
 20  budget_adj:            the budget of the associated movie in terms of 2010 dollars, accounting for inflation over time
 21  revenue_adj:           the revenue of the associated movie in terms of 2010 dollars, accounting for inflation over time
 
 + Certain columns, like ‘cast’ and ‘genres’, contain multiple values separated by pipe (|) characters
 + There are some odd characters in the ‘cast’ column
 + The final two columns ending with “_adj” show the budget and revenue of the associated movie in terms of 2010 dollars, accounting for inflation over time.


### Question(s) for Analysis
> + What is the most popular genre?
> + What is the Distribution of the runtime across all movies?
> + What is the Relationship between vote count and popularity?
> + Does popularity contributes to high vote average?


<a id='wrangling'></a>
## Data Wrangling
> Load dataset and explore with pandas built-in functions
> Check the rows with zeroes: Some columns minimum is zero according to df.info()
- Data collection for revenue_adj, budget_adj, revenue, budget was stopped at an early point, more than half of the dataset have no values for these columns. To avoid bias and misrepresentation of data, drop these columns._
- The imdb_id, genres, director, production_companies columns have some null values, drop them.

### Data Cleaning
- Drop the columns: cast, tagline, homepage, overview, director, production companies, and keywords. They make our data crowdy, and they contain information not needed for the analysis.
- _Data collection for revenue_adj, budget_adj, revenue, budget was stopped at an early point, more than half of the dataset have no values for these columns. To avoid bias and misrepresentation of data, drop these columns._
- The imdb_id, genres, director, production_companies columns have some null values, drop them.
-  Format the release date to pandas date_time format. The date-time object is easier to work with.
- Create a column for broad categories of genres. This is to reduce bulkiness in the analysis. The genres are not uniform because they are based on user inputs. Then group according to the first word in the genre column.


<a id='eda'></a>
## Exploratory Data Analysis

### Research Question 1 (What is the most popular genre?)


![image](https://user-images.githubusercontent.com/103776681/184548678-ae33cedc-b5ad-4598-8cdf-3ee2df33e0d9.png)
The most popular genre is adventure (tallest bar), followed by science fiction. This analysis is based on the broad categorization by using the first words in the genre column.


### Research Question 2  (What is the Relationship between popularity and high vote average?)


![image](https://user-images.githubusercontent.com/103776681/184548717-e03f02f6-17eb-48a2-9cb5-24cb2e9fcaf9.png)
This best line of fit for the scatter plot above is a vertical straight line. This means no relationship between popularity and vote average.


### Research Question 3 (What is the Relationship between vote count and popularity?)


![image](https://user-images.githubusercontent.com/103776681/184548746-2911dcb3-764f-4ba4-87ee-1ff112c94bf8.png)
The best line of fit for the above plot has a positive slope (slanted to the right). This means a positive linear relationship between popularity and vote count. That is the more popular a movie is, the higher the vote count.


### Research Question 4 (What is the distribution of runtime across all movies?)


![image](https://user-images.githubusercontent.com/103776681/184548817-95a7fd88-7bc1-4b2d-86c6-db728ebadfc7.png)
Most movies have runtime above 150 (tallest bar in the middle), few below 150, rarely above 200 (shortest bar).


<a id='conclusions'></a>
## Conclusions
> Question(s) for Analysis again
> + What is the most popular genre?

The most popular genre is adventure, followed by science fiction. This analysis is based on the broad categorization by using the first words in the genre column.

> + What is the Distribution of the runtime across all movies?

Most movies have runtime above 150, few below 150, rarely above 200.

> + What is the Relationship between vote count and popularity?

There is a positive linear relationship between popularity and vote count, as depicted on the plot. That means the more popular a movie is, the higher the vote count.

> + Does popularity contributes to high vote average?

There is no relationship between popularity and vote average, as depicted on the plot.

## Limitations

> The first word in the genres column might not be exact representation of the movie category. Hence, specific options for genres should be created for users to select from.
> More than half of the dataset has no information on revenue, revenue adjustment, budget, budget adjustment. This actually limited analysis on movie budgets and revenues.


## Reference
> Not applicable
