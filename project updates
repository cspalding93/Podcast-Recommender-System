# Podcast-Recommender-System
________________________
## About this project:
This project is currently in development and will be on-going in jupyter notebooks. The below is an outline of where my thoughts are with the project. This is not a final nor formal README file; nor are my files marked up nor organized as I would in a final production. for those investigating my GitHub, please feel free to read below as a sort of rough outline on my project. 
________________________

## UPDATES (12/6):
The first version of the recommender is possible on a personal system with the RAM available, otherwise a cloud computing system will be required. The next step is to publish a flask application that will allow for a better demo of the recommender. Most recent recommender is in the "Final Recommender.ipynb" notebook. The final write up will be published on 12/8 with visuals. Some CSV files are not able to be uploaded due to the size restriction of GitHub. File paths will need to be adjusted for recreation if cloaned.

(11/24)
Recommender based on the content is functional within a jupyter notebook. Production of a genre classifier was paused this week to focus my time on further reading on LSTR-CNNs for text classifications. 

(11/17)
Logistic regression models have been made to classify if a podcast is of a certain type of genre. Their accuracy scores are between 70% and 80%. This is initial fitting via gridsearching to find ranges of parameters that should be used for TFiDFVectorizor. The max features for many of the LR models are within 400 features with ngram range at (1,1). Sixteen models were made in 4 hours.
________________________
# Problem Statement:
Collaborative filtering dominates markets where content is not possible for analysis. But with little to no user engagement information, a content based recommender can perform in place of a collaborative filter recommender

Checkpoint:

The current data sets that I believe to be most useful:
- Collected transcripts for all “This American Life”
  - Episode title is the index
  - Has transcriptions in the text column
- Dataset of all episodes released on ListenNotes Dec 2017
  - Episode description
  - Podcast title
  - Episode title
  - Episode length in seconds
  - Podcast category
  - Language of the podcast
  - 95k+ English podcasts (no duplicates)
- 7 audio files from a relatively unknown podcast that my friend professionally does for his work
  - Purely mp3 format
  - Each of them are about 20 minutes in length


My initial instincts say that I should start doing two things
- Find open source transcription APIs, 
  - connect and set up as many as I can get
  - Transcribe one audio file and find the best performing one
  - Throw all of the audio files through the chosen transcription API
- Make a genres dummy column for all of the genres that are identified in the Dec ‘17 csv
  - Make multiple Logistic Regressions that will classify if the episode can fall under that genre.
    - Multiple LRs are needed as a podcast episode can fall under multiple genres 
  - “This American Life” episodes into the possible categories that the episode could be. (this would feed information into the recommender system because not all of)

Then I should make a data frame for the recommender system by doing the following:
- Concat th TAL df and the Dec ‘17 dataframe. 
- Try a recommender both with and without the time length of the podcast episode. 
- Then use the transcripts, see what is being recommended
