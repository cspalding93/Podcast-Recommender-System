

# Podcast Content Recommender System
[Slides](https://docs.google.com/presentation/d/1Qy40fhh0Euq8YckrmwKK_Z4MhWib4W0FKJwAOCMsefc/edit?usp=sharing)

![Imgur](https://i.imgur.com/4wCsqh6)

5 point summary
_________________________
1. Recommendation systems are prolific in the economy and face the “long tail” problem
2. This is a recommendation system based off of the transcript of podcast episodes to demonstrate a media that can avoid the “long tail” problem
3. Genre prediction was used to add content to all of the transcripts
4. Recommendation performance is best used in measuring user engagement
5. Reflection: Data quality is a key part of the start of a project 
_________________________
## Introduction

The goal of any good recommender system is to [“Help members find content to watch and enjoy to maximize member user satisfaction and retention"](https://www.slideshare.net/moustaki/some-pitfalls-of-distributed-learning). 
   
Recommendation systems decide on what ad you see, what product you should buy next, or which audiobook should be listened to next. In some such as Netflix, Spotify, and Amazon, the system makes the decision to recommend an item based on the similarity of users. However these user based systems face a particular problem known as “the long tail problem”. 

![Imgur](https://imgur.com/1FAgk81)

The long-tail problem of user engagement presents itself as a challenge with collaborative filter recommendations. Pandora, the online personal radio website, creatively works around this by attributing musical characteristics to each song manually, thus giving quantifiable content to each song. As an example to show how effective a content based recommendation can be, I build a recommendation system that uses the transcripts of podcasts to make suggestions. 
_________________________
### Data
![description image](https://imgur.com/EKTgCG7)
Transcript for "This American Life" can be found [here](https://data.world/cjewell/this-american-life-transcripts)

Data set to train the genre modeling can be found [here](https://www.kaggle.com/listennotes/all-podcast-episodes-published-in-december-2017)

_________________________
### Preprocessing 
For “This American Life” data set, the sentences need to be joined together to create a full transcript of every episode. Thankfully that was a very clean dataset. 

The Listennotes dataset required a few extra steps. First, We should drop all genres that are not in the english language. Second, the genres are in a string format with multiple genres separated with a “|”. These need to be split and then transformed into dummy columns. Third, this dataset is very messy and needs to have HTML tags removed. After filtering, check for nulls and drop. This should all result in a cleaned dataset with target dummy columns for their respective genres.

For both datasets, stemming is required as well as punctuation cleaning and setting the text to lowercase. The files should now be ready to be transformed with a TFiDF vectorizer. Once these values are generated, the process of genre modeling and recommendations can begin.

Modeling efforts - At first a neural network was attempted in correctly predicting the genre in question. But the neural network would overfit after 2-5 epochs and would not perform significantly better than the logistic regression models. Logistic regression models were produced for each of the 16 genres in order to narrow in on accuracy instead of producing a 16 multi-class classifier that performed poorly (see graph below). Many podcasts had multiple podcasts within their description, and so classifying episodes for multiple genres reflects the original data.

![Imgur](https://imgur.com/IVQzB8t)

Recommendation system - The recommendations will be based off of the cosine similarities between the TFiDF matrix along with the genres that were predicted from the classifiers. 
_________________________
### Reflective Summary

Measuring the success of the recommendation system is typically in a measurement of user engagement or sales. Since this is a personal project, these metrics are not possible to find. However, on the surface, the recommendation system appears to be doing a great job on picking up on common themes amongst the podcasts. If this were to go into production, the most important questions to answer would to be the following:

- Would this retain users?
 - This system creates an opportunity to connect users to a multitude of podcasts that they may not have been exposed to before simply because it was not in line with users similar to them. I suspect that that would indeed lead to longer engagement. 
- Is this a cost effective solution?
 - Maybe: If transcripts are immediately available for all the podcasts, then yes. This would be an effective system to implement for a new podcast host with low user engagement. If not, then the cost of transcribing these transcripts needs to be considered before running straight to this sort of service.

There are noticeable flaws in this project that became evident as I matured as a data scientist. The main two that I found in this project are:

- The data quality of the Listennote’s dataset is not very good. If only I understood this concept at the start of this project. This low-quality data made the process of modeling the genres almost impossible and ate most of the time on the project. 
- The storage of a large recommendation system is key to the project and should be considered before writing the code. 
 
These reflections are, of course, from a data scientist early in his career. But thankfully I have come quite far and am proud to create a recommendation system that fulfills the original goal. 
_________________________
