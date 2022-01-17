# Netflix-Analyst-by-using-R
#Introduction
#Streaming services have grown over the last few years. It seems everyone is getting into the streaming business. From Netflix to Hulu, each streaming services #offering a collection of original programming and shows/movies that they have bought rights too.There is a wide range of services available, but how should #consumers choose?Let’s start with the features of Netflix.
#Data
#The dataset used in Netflix can be found in Kaggle .
#It shows you TV shows and movies release year and release date onto the streaming service.
#Analysis & Visualization
This dataset is a CSV files. I would import data into Rstudio where it was processed, analyzed and visualized.
#Movies always more than TV show
#On Netflix there are more than 6,000 movies and 2,000 TV shows.
library(tidyverse) 
library(forcats)
library(janeaustenr)
library(tidytext)
library(reshape2)
library(lubridate)

netflix<-read_csv("../input/netflix-shows/netflix_titles.csv")
summary(netflix)

netflix%>%
group_by(show_id)%>%
count()%>%
filter(n>1)

ctr<-ctr_tibble%>%
group_by(country_name)%>%
count()%>%
filter(!is.na(country_name))


ctr%>%
filter(n>100 && country_name != '')%>%
ggplot(aes(n, reorder(country_name, FUN=median, n), fill= n>1000))+
geom_bar(stat='identity', show.legend = F)+
labs(
x='Numbers of movies on Netflix',
y='Country name',
title='US and India make the most movies on Netflix')

netflix %>%  
separate_rows(country,sep=', ') %>%  
filter(country=='South Korea'& release_year<="2021-02-01" & release_year>="2000-01-01") %>%  
group_by(release_year,type) %>%  
summarize(counts=n()) %>%  
group_by(type) %>%  
mutate(cummul=cumsum(counts)) %>%  
ggplot(aes(x=release_year,y=cummul,color=type))+  
geom_line(size=1)+  
labs(x='release_year', y='n', title = 'Relesed Movies & TV Shows of South Korea')
