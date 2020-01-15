# Podcast Content Recommender System
_________________________
### Abstract

The long-tail problem of user engagement presents itself as a challenge with collaborative filter recommendations. Podcasts are a content rich source that requires only a transcript for analysis. The Recommender System uses the transcript of podcasts in order to make a recommendation for the user. The genre models are created to feed additional content for the recommendations to be based on. 

_________________________
## Project Introduction
Recommender systems are used across all markets in order to drive sales and maintain repeat customers. Amazon is often one of the first examples of a company that knows how to implement a recommender system, but recommenders are used amongst almost any company look to retain user engagement or sell more products. For an example on how important a recommender system is to a company: Back in 2009, [Netflix](https://en.wikipedia.org/wiki/Netflix_Prize) awarded a small group of programmers and data scientists a million dollar grand prize for improvement on their recommender system based on user ratings. The final product was an improvement by 10% more predictive power of who would watch a recommended item. Recommenders effect not just what is being presented, but how it is presented in the application. The goal of any good recommender system is to “Help members find content to watch and enjoy to maximize member [user](https://www.slideshare.net/moustaki/some-pitfalls-of-distributed-learning) satisfaction and retention” (quoted). As recommender systems continue to play an essential roles in our economy I attempt to create a content based recommender system to demonstrate a work-around for low user engagement scenarios. 
_________________________
### Data

Data set to train the genre modeling can be found [here](https://www.kaggle.com/listennotes/all-podcast-episodes-published-in-december-2017)

Transcripst for "This American Life" can be found [here](https://data.world/cjewell/this-american-life-transcripts)

All text was set to lower case and contractions were transformed into their uncontracted forms. 
_________________________
### Process
With a clean dataset, The transcrips of the podcasts episodes are transformed with a TFiDF vectorizor with the episode title set to the index. With the TFiDF matrix, a cosine similarity metrix is producable for all episodes. The cosine similarity is a common metric when attempting to find the most similar document in a corpus. A function allows for easy filtering of the cosine similarity matrix. A function calls a column in the matrix which then sorts for the top X number of similar episodes and produces the index, which, as a reminder, was labeled with the podcast episode title. For the genre modeling; the dataset of podcasts from December of 2017 is cleaned of its HTML tags and uses descriptions with their title as a form of description for the genre models. At first a neural network was attempted in correctly predicting the genre in question. But the neural network would overfit after 2-5 epochs and would not perform significantly better than the logistic regression models, and so logistic regression models were produced for each of the 16 genres in order to narrow in on accuracy instead of producing a 16 multi-class classifier that would perform extremely poorly. Once each of the models is produced, the transcript TFiDF vectorizor is fed through the model and added to the dataset prior to the cosine similarity matrix.
_________________________
### Summary
A content based recommender is a relatively robust form of a recommender system and is most effective in audio or text media. Content based will not out perform a collaborative filter recommendation but is a starting place for many new applications and ecommerce sites. One challenge that presents itself to the recommender system is they are often expensive in term of memory. Many cosin similarity matrices will be unable to be transformed back into a sparse matrix, and there fom require cloud storage to produce and interact with the recommendation function.
_________________________

