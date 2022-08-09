# What to watch next?
### Eclipse_Rodeo
**Team Members:**
- Ethan Price
- Delgertsetseg Nyamsuren
- Kirsten Larson

**Proposal:**

  Throughout the pandemic, many people filled their freetime with streaming content from Netflix, Amazon Prime and Hulu. After two plus years, people want to know -- What to watch next? Using data sources from Kaggle, we want to know which streaming service produces the best original content, which actor(s) to seek out, which long running shows are the best, and what genre is the most popular.

**Initial questions:** 
1. Which director with 4 or more movies has the highest average rating?
2. Is there a correlation between number of seasons for a TV show and IMDb score?
3. Is there a correlation between movie run times and IMDb score?
4. Which streaming service is most catered towards adults? Which is best for children?
5. Do older movies have higher IMDb scores than newer movies?



**Initial Data Source:**
- Kaggle - HBO Max TV Shows and Movies by Victor Soeiro
  https://www.kaggle.com/datasets/victorsoeiro/hbo-max-tv-shows-and-movies

- Kaggle - Netflix TV Shows and Movies by Victor Soeiro
  https://www.kaggle.com/datasets/victorsoeiro/netflix-tv-shows-and-movies?select=titles.csv

- Kaggle - Hulu TV Shows and Movies by Victor Soeiro
  https://www.kaggle.com/datasets/victorsoeiro/hulu-tv-shows-and-movies?select=titles.csv

- OMDb API
  https://www.omdbapi.com/

**Specialist:**
- pandas guru - ***Degi***
- matplotlib  expert - ***Kirsten***
- API enthusiast - ?
- github power user - ***Ethan***
- statistician extraordinaire - ***Kirsten***
- master of ceremonies - ***Ethan***
- project management specialist - **shared**

### Analysis & Discussion

Once we began digging into the datasets we had found, we quickly realized that they were lacking information specifically regarding each streaming service's original content. There was no way for us to pick out only the original movies and shows from each service without grabbing every single one and putting it in a dataframe by hand. This forced us to return to the drawing board and come up with a new question.

After making that change, we decided to take a closer look at what information our datasets provided and see if we could accurately answer our remaining questions. Upon further examination, we found that it was going to be very difficult to answer our second and fifth questions. For our second question, "Which actor has the highest average rating?", we found there were multiple actors listed within each movie and each actor shared the same IMDb score associated with the film. So the results for the actor with the highest average rating would not be a valid representation since each actor was rated the same for each movie they were a part of. As for our fifth question, "What genre has the highest rating across all streaming services? (Movies)", once we examined the genre column of our datasets, we quickly realized what a mess it was. Most, if not all movies were listed within multiple genres. To solve that problem, we thought we could group each movie with the first genre associated with it. However, this also became an issue because the firs genre listed was not always the best genre to represent the film and would cause our results to be an inaccurate representation of the data. So after scrapping those two questions as well, we looked for possible relationships and connections we could make with our data and ultimately landed on these five questions:

**Revised quesions:**

1. Which director with 4 or more movies has the highest average rating?
2. Is there a correlation between number of seasons for a TV show and IMDb score?
3. Is there a correlation between movie run times and IMDb score?
4. Which streaming service is most catered towards adults? Which is best for children?
5. Do older movies have higher IMDb scores than newer movies?

**Question 1:**
   To solve this question, we first took our dataset that contained every movie from each streaming service and pulled out just the rows that had a director listed under the "role" column. This isolated the data to just directors and from there we could trim the data to just list the directors' names and their average IMDb scores for all of their films. From there, we listed the total count of films each director had across Netflix, Hulu, and HBO. We also decided to set a minimum total of four films per director to trim the data and remove any outliers that may have very high scores but just one movie. This left us with about 50 directors which we plotted on a bargraph along with their average IMDb scores, resulting in this:

  !(/Output/director_score.png)

  After generating that graph, we wanted to try and answer the question that is our project's namesake, "What to watch next?" So with Akira Kurosawa having the highest average rating within our streaming services, we wanted to plot his movies and their IMDb scores to see which is considered the best and help us choose what we should watch next:

  !(/Output/kurosawa_score.png)

  Based off of this data, the answer for what we should watch next would be Akira Kurosawa's Seven Samurai.

**Question 2:** 
  For this question, we wanted to see if longer running shows were rated higher than shows that only lasted a few seasons. To answer this we decided to generate a scatter plot that listed the number of seasons for a show on one axis and the the IMDb score on the other. This is the plot we created:

  !(/Output/seasons_vs_score.png)

  As you can see, the regression line is almost completely flat and the r value was calculated to be 0.01 meaning there is almost no correlation between the number of seasons a show has and its IMDb score.

**Question 3:**
  Our third question focused on the length of movies and their IMDb score. We wanted to see if people tended to rate movies poorly if they were too long or too short. We were also curious if there were a "sweet spot" where a general movie length produced above average ratings frequently. So, we created another scatter plot. This time we had the movies' runtime in minutes on one axis and the IMDb score on the other. Here is the resulting plot:

  !(/Output/runtime_vs_score.png)

  The results from this graph differ from the previous one in that the regression line has more of an incline, which would be associated with a positive corelation. However, the incline is not very steep and the calculated r value is only 0.14. This represents a weak positive correlation and you cannot say with certainty that longer movies score better overall.

**Question 4:** 
  For our fourth question, we wanted to find out if any of the streaming services content was more so catered for adults or if any were catered towards children based on the frequency of the content's age ratings. To do this, we took the data from each individual streaming service and divided it into two data frames to seperate movies and shows. From there, we created grouped bar graphs to display the number of movies and shows with each rating for every streaming service, shown here:

  !(/Output/movie_ratings_vs_service.png)
  !(/Output/tv_ratings_vs_service.png)

  Looking at the movie graph, you can see that each streaming service has very similar distribution ratios for each rating. Netflix and HBO are nearly identical for each rating, while Hulu has less movies than the other two. 

  The show graph differs somewhat from the movie graph. There is more variance between the three streaming services with the amount of shows within each rating category. Netflix leads the three services in total amount of shows offered, while HBO is lacking on variety and has much less to offer. 

  As for identifying if one streaming service is more so catered to adults, ....

**Question 5:**
  Finally, with our last question we wanted to look at how "old" movies compared to "new" movies. To go about this, we first had to define what qualified a movie to be old. We ultimately settled on movies with a release year before 2005 as being old since this was the most even two way split of our data. Next, we created some scatter plots, one containing all movies, one with movies released from 1921-2004, and one with movies from 2005-2022:

  !(/Output/year_vs_score.png)
  !(/Output/old_release_vs_score.png)
  !(/Output/new_release_vs_score.png)

  All three plots show a negative correlation for IMDb scores compared to release year, although the correlation is very weak. This is likely attributed to two things, 1. the shear volume of modern movies outweighing older movies and their variance of scores bringing the average down, and 2. streaming services aren't likely to add unpopular and poorly rated old movies to their platform so the frequent high scores of old movies doesn't represent all movies from those times accurately.