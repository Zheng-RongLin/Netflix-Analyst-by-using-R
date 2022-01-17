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
