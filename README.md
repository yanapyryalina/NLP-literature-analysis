# NLP Literature Analysis

## Introduction
Reading is great. And with so many amazing books out there also come great movies, reviews, and summaries. Reading those reviews and watching those films often only gives us a picture of what the book is actually like, though. With the power of data science and natural language processing, I am able to bring another dimension to how we understand literature.

For this project, I look at the following eight writings:
- *The Foundation* by Isaac Asimov
- *A Clockwork Orange* by Anthony Burgess
- *Comments to the Society of the Spectacle* by Guy Debord 
- *A Brief History of Time* by Stephen Hawking 
- *For Whom the Bell Tolls* by Ernest Hemingway
- *Carrie* by Stephen King 
- *The Hobbit* by J.R.R. Tolkien
- *Slaughterhouse Five* by Kurt Vonnegut

I chose these writings both out of personal interest and because of their unique subjects, settings, and writing styles. 

## Data Scraping and Cleaning
To collect my data, I went to [archive.org](https://archive.org/) and scraped the above-mentioned books in .txt format using Beautiful Soup and requests python libraries. 

In order to create my corpus and .To create my pandas corpus, I performed two rounds of cleaning - first to delete new lines and second to delete non-author writing like copyright notes. I then performed the third round of cleaning (lowercase, removing punctuation and digits), and created a document-term matrix using CountVectorizer. I also pickled more versions of these data frames to load throughout the different sections of my project.

## Exploratory Data Analysis

### Wordclouds
First, I looked at the writings through most common words in each book. Taking the first 30 most common words and performing more cleaning, I created wordclouds using matplotlib and WordCloud libraries. 

<p align="center">
  <img width="500" src="https://github.com/yanapyryalina/NLP-literature-analysis/blob/master/nlp-lit-analysis-imgs/word-clouds-1.png">
</p>

<p align="center">
  <img width="500" src="https://github.com/yanapyryalina/NLP-literature-analysis/blob/master/nlp-lit-analysis-imgs/word-clouds-2.png">
</p>

### Vocabulary Size
To see the vocabulary size of each author, I calculated by the number of unique words, as well as found the length of the books by calculating the total number of words. To visualize my findings, I created bar graphs and scatter plots using numpy and matplotlib.

![alt text](https://github.com/yanapyryalina/NLP-literature-analysis/blob/master/nlp-lit-analysis-imgs/vocabulary-bar-graphs.png)

<p align="center">
  <img width="700" src="https://github.com/yanapyryalina/NLP-literature-analysis/blob/master/nlp-lit-analysis-imgs/vocabulary-scatter-plot.png">
</p>

## Sentiment Analysis
Due to the complexity of dynamics in literature writings, I chose to approach sentiment analysis from two perspectives - overall book-vs-book sentiment comparison and sentiment over time. 

I started my analysis by calculating sentiment based on the two classical scales - polarity and subjectivity. After finding the sentiment values using TextBlob, I plotted my findings to compare the writings with matplotlib.

<p align="right">
  <img width="800" src="https://github.com/yanapyryalina/NLP-literature-analysis/blob/master/nlp-lit-analysis-imgs/sentiment-analysis-scatter-plot.png">
</p>

To find the sentiment of each book over time, I split each writing into 40 pieces using numpy and graphed the data for each book separately. 40 pieces per writing ended up giving the best amount of detail, maintaining both thoroughness and readability. 

![alt text](https://github.com/yanapyryalina/NLP-literature-analysis/blob/master/nlp-lit-analysis-imgs/sentiment-analysis-over-time.png)


## Topic Modeling
To perform topic modeling, I chose to use Latent Dirichlet Allocation. I found LDA to be a good choice of tool for this project due to the interpretability of topics. Working with large and complex pieces of data like literature works, I wanted to see if I as a reader could pick up latent/hidden topics as a result of my data analysis. 

For this task, I created three LDA models - first based on all parts of speech, second including only nouns, and third using nouns and adjectives. For the last two models, I created noun-filtering and noun&adjective-filtering lambda functions, created two new document-term matrices and transformed them into a sparse matrix and finally a gensim corpus. After trying out various combinations of filters, topics, and passes, I created the final model - a noun&adjective model with 5 topics and 100 passes. The model's results include most comprehensive words (including adjectives), take words from more books, and incorporate a much wider variety of visible topics. 

![alt text](https://github.com/yanapyryalina/NLP-literature-analysis/blob/master/nlp-lit-analysis-imgs/final-model-1.png)

<p align="center">
  <img width="700" src="https://github.com/yanapyryalina/NLP-literature-analysis/blob/master/nlp-lit-analysis-imgs/final-model-2.png">
</p>


## Text Generation
I chose Markov Chains as a starting point for text generation, as I wanted to start my learning process from simpler approaches, as well as to see the extent of the success of this approach when working with larger texts like works of literature. 

To create a Markov Chain function, I used the defaultdict library because it allows to efficiently create a dictionary chain of words from our corpus on the go (in a loop), avoiding KeyErrors. The function creates a zipped list of all of the word pairs and put them in a dictionary format (word : list of connecting words). To generate sentences, I randomly picked a word from the dictionary, and followed its connecting lists of possible words until the specified end of the sentence. 

Surprisingly, Markov Chains resulted in text generator that preserved the writers’ styles very visibly. Here are some of my favorite examples:
- Stephen King: 'Comment. Nobody was overcast and sanitary napkins, chanting, laughing, shrieking of course, forbade her heart..'

- Guy Debord: 'Erasure of the century language of goods is insignificant or in this mystery is genuine.'

- Stephen Hawking: 'Suggests, cosmic censorship hypothesis tells us the inner edge of one ignored the very close.'

- J.R.R. Tolkien: 'Loosened his door, and giving his ring of the balance as if he had baked.'

  - Grandmother, teaching his legs with them hoping against the chill flame, beating wigs bear to.

  - Saucer, and Bilbo had lost the foot of the foot right away.

  - "Try," said a gathering together! There was not forbear to sniff.

  - What about the hobbit? He slashed the current market value"

- Isaac Asimov: 'Sake, as to admit you speak, Hardin. And two; after Emperor would one of Imperial.'

- Ernest Hemingway: 'Material and headed toward Segovia at the cup out and the gipsy’s voice thickening.'

- Kurt Vonnegut: 'Architect. The atmosphere now, big kiss. She had been stolen from the opinion of his.'


## Final Thoughts & Results
Each of the sections of this project revealed findings that were surprising and exciting both for people who have read the books and for those who have not. For example, who knew that Stephen King and Isaac Asimov - writers in completely different styles and genres - have the largest vocabulary out of all these authors? Or that Tolkien's *The Hobbit* is the most sentimental of these books? 

For more findings, check out the Results section of my report in this folder or through this link [here](https://docs.google.com/document/d/1XUBmfaKCUlWnRs6jaWdrXDH8M8Yh0mFkZulmeRgOAFU/edit?usp=sharing).

I believe that there is great value in looking at works of literature from a data science perspective, as it allows to analyze the humanity's most valued views of the world from a new fresh angle that the 21st century is bringing to us. I look forward to expanding this project to analyze works of literature accross more time periods and languages including Russian and French. 

### Credits
Thank you so much to Alice Zhao who made such an amazing PyOhio 2018 conference workshop that inspired this project. 
Check out her workshop [here](https://www.youtube.com/watch?v=xvqsFTUsOmc)

