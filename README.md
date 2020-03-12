

# Podcast Content Recommender System
![Imgur](https://i.imgur.com/4wCsqh6.png)
___________________________
## Index

- [Introduction](https://github.com/cspalding93/Podcast-Recommender-System#introduction)
- [Data](https://github.com/cspalding93/Podcast-Recommender-System#data)
- [Preprocessing](https://github.com/cspalding93/Podcast-Recommender-System#preprocessing)
- [Developing a Recommendation System](https://github.com/cspalding93/Podcast-Recommender-System#developing-a-recommendation-system)
- [Results Summary](https://github.com/cspalding93/Podcast-Recommender-System#results-summary)
- [Sources](https://github.com/cspalding93/Podcast-Recommender-System#sources)

[Presentation Slides](https://docs.google.com/presentation/d/1Qy40fhh0Euq8YckrmwKK_Z4MhWib4W0FKJwAOCMsefc/edit?usp=sharing)

_________________________
## Introduction  
   
### Recommendation systems and their challenges
Recommendation systems decide on the next ad you see, the next product you should buy, or the next audiobook to put on. In companies such as Netflix, Spotify, and Amazon, the system makes the decision to recommend an item based on the similarity of users. These type of systems are known as *Collaborative-based recommendation systems*. However these user based systems face a particular problem known as “the long tail problem”. The long-tail problem of user engagement is an inherent challenge with collaborative filter recommendations. It is a phenomenon where a majority of the items/products on a platform have little to no user-engagement (see chart below for clarity).

![long tail](https://i.imgur.com/1FAgk81.png)
- Y-axis: the number of plays/views/interactions an item in a database received from users.
- X-axis: the number of items with that specific number of plays/views/interactions from users

In the context of music, the first item is a single song that has the most plays from the platform; as we move across the x-axis, we find more songs with less and less listeners. This hinders the performance of the recommendation system and will drive users off the platform if left unaddressed. This is avoided in *Content-based recommendation systems* as they do not rely on user engagement. Instead, these systems operate on inherent details of the product like descriptions, lyrics, or genres. Pandora, the online personal radio website, creatively works around this by attributing musical characteristics to each song manually, thus giving quantifiable content to each song. But this process requires manual labor which leads to cost with training, office space maintenance, and administrative processes. But not all forms of media require this much extra effort to create a complete picture of the content. For podcasts if you have the transcript, then you have a rich source of content that can be transformed and understood by computers to generate recommendations. For further information on recommendation systems, click [here](https://towardsdatascience.com/introduction-to-recommender-systems-6c66cf15ada).

### Similarity Metrics

The goal of any good recommender system is to [“Help members find content to watch and enjoy to maximize member/user satisfaction and retention"](https://www.slideshare.net/moustaki/some-pitfalls-of-distributed-learning). In order to make a successful recommendation, the system must look in the database and order the podcasts in which are most similar in their transcript. The most widely used metric for this is the cosine similarity.

![cosine similarity](https://i.imgur.com/L7jes3w.png)
- The above photo displays the difference when measuring the Euclidean distance versus the cosine similarity.

A comprehensive look at the cosine similarity can be found [here.](https://www.machinelearningplus.com/nlp/cosine-similarity/)
_________________________
### Data
![description image](https://i.imgur.com/EKTgCG7.png)

Transcript for "This American Life" can be found [here](https://data.world/cjewell/this-american-life-transcripts)

Data set to train the genre modeling can be found [here](https://www.kaggle.com/listennotes/all-podcast-episodes-published-in-december-2017)
(# down here, needs to be an explanation of the data used and why)
_________________________
## Preprocessing
List the steps of preprocessing

_________________________
## Developing a Recommendation System 
(# short summary of the steps taken to process the transcripts)
For “This American Life” data set, the sentences need to be joined together to create a full transcript of every episode. Thankfully that was a very clean dataset. 

The Listennotes dataset required a few extra steps. First, We should drop all genres that are not in the english language. Second, the genres are in a string format with multiple genres separated with a “|”. These need to be split and then transformed into dummy columns. Third, this dataset is very messy and needs to have HTML tags removed. After filtering, check for nulls and drop. This should all result in a cleaned dataset with target dummy columns for their respective genres.

For both datasets, stemming is required as well as punctuation cleaning and setting the text to lowercase. The files should now be ready to be transformed with a TFiDF vectorizer. Once these values are generated, the process of genre modeling and recommendations can begin.

Modeling efforts - At first a neural network was attempted in correctly predicting the genre in question. But the neural network would overfit after 2-5 epochs and would not perform significantly better than the logistic regression models. Logistic regression models were produced for each of the 16 genres in order to narrow in on accuracy instead of producing a 16 multi-class classifier that performed poorly (see graph below). Many podcasts had multiple podcasts within their description, and so classifying episodes for multiple genres reflects the original data.

![results of AI models](https://imgur.com/IVQzB8t)[Imgur](https://i.imgur.com/IVQzB8t.png)

(# make a section about the subjectivity of the recommendations made. Talk about metrics that could be employed after the subjective testing)

Recommendation system - The recommendations will be based off of the cosine similarities between the TFiDF matrix along with the genres that were predicted from the classifiers. 

(# go through each of the BOW transformations and explain them. Then implement the word2vec)
_________________________
## Results Summary

**5 point summary**
1. Recommendation systems are prolific in the economy and face the “long tail” problem
2. This is a recommendation system based off of the transcript of podcast episodes to demonstrate a media that can avoid the “long tail” problem
3. Genre prediction was used to add content to all of the transcripts
4. Recommendation performance is best used in measuring user engagement
5. Reflection: Data quality is a key part of the start of a project 

(# place in something to  show how the recommendation system works)

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
## Sources
(# gotta list these out in full)

- https://www.machinelearningplus.com/nlp/cosine-similarity/
- https://towardsdatascience.com/introduction-to-recommender-systems-6c66cf15ada
- https://www.kaggle.com/ktattan/lda-and-document-similarity
