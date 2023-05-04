---
layout: post
title: My first data challenge.
---
As part of a technical interview workshop with Erd&#246;s Institute, this morning I did a data challenge to present at the problem session tomorrow.  The details and instructions are in the pdf file in my [SpaceshipTitanicDataChallenge repository](https://github.com/wh33les/SpaceshipTitanicDataChallenge).  I gave myself 3 hours to do it, and barely got through cleaning the data.  Toward the end of the 3 hours, I realized and learned some things I could've done to get further along, but I just ran out of time.  But it was interesting putting my Python abilities to the test in a timed setting.  I don't think I know Python as well as I thought I did.  Or maybe I already had a realistic idea of how proficient I am -- my application for the boot camp TA position was near perfect, in my opinion, but it also took 6 hours to complete (and Matt doesn't know that).  Now I want to try more data challenges to see if I can get better.

To summarize the challenge, I was given passenger data from a spaceship trip of migrants going to one of three habitable planets.  Along the way, the spaceship ran into a spacetime anomaly and almost half of the passengers were transported to an alternate dimension.  The goal was to predict which passengers were transported.  I was given a train file with 2/3 of the pasengers' data, including whether or not they were transported, and the remaining data was in a test file, without information about whether or not they were transported.

It wasn't hard to figure out which algorithm to choose to solve the problem, since I only know two: PCA and $k$-nearest neighbors.  Luckily $k$-nearest neighbors is a classification algorithm so I chose that.  The only problem was that several of the variables were categorical.  When I ran the `info` function on the train data the data type for the categorical columns was object.  I read online that changing object data to categorical data reduces memory.  I also thought making this change would give numerical categories for each data point and then I would be able to run the $k$nn algorithm and see what happens.

Along the way I noticed there was missing data.  Matt did a lecture during the last boot camp about how to fill in missing data.  The process is called **imputation**.  I filled in most of the categorical features' data with the most frequent observation, the numerical data with the mean, and a couple of other features with "Unknown".  I guess I thought it was possible that "Unknown" could be an observation correlated with whether or not a passenger was transferred.  At this point I ran into a pesky error filling in those columns with the most frequent observation.  I used the code Matt used in his lecture, but I kept getting an error, even though when I used the same code for the other columns it worked fine.  I ended up replacing the code
```
for column in ["HomePlanet", "CryoSleep", "Destination", "VIP"]:
    cleaned_train_data.loc[cleaned_train_data[column].isna(), column] = cleaned_train_data[column].mode()
    cleaned_train_data[column].fillna(cleaned_train_data[column].mode()[0], inplace=True) 
    # code found at https://stackoverflow.com/questions/40619445/how-to-replace-na-values-with-mode-of-a-dataframe-column-in-python

```
with&colon; 
```
for column in ["HomePlanet", "CryoSleep", "Destination", "VIP"]:
    cleaned_train_data[column].fillna(cleaned_train_data[column].mode()[0], inplace=True) 
    # code found at https://stackoverflow.com/questions/40619445/how-to-replace-na-values-with-mode-of-a-dataframe-column-in-python
```
