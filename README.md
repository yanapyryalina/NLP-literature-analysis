# NLP Literature Analysis

## Introduction
Reading is great. And with so many amazing books out there also come great movies, reviews, and summaries. Reading those reviews and watching those films often only gives us a picture of what the book is actually like, though. With the power of data science and natural language processing, I am able to bring another dimension to how we understand literature.

For this project, I look at the following eight writings:
- The Foundation by Isaac Asimov
- A Clockwork Orange by Anthony Burgess
- Comments to the Society of the Spectacle by Guy Debord 
- A Brief History of Time by Stephen Hawking 
- For Whom the Bell Tolls by Ernest Hemingway
- Carrie by Stephen King 
- The Hobbit by J.R.R. Tolkien
- Slaughterhouse Five by Kurt Vonnegut

I chose these writings both out of personal interest and because of their unique subjects, settings, and writing styles. 

## Data Scraping and Cleaning
To collect my data, I went to [archive.org](https://archive.org/) and scraped the above-mentioned books in .txt format using Beautiful Soup and requests python libraries. 

In order to create my corpus and .To create my pandas corpus, I performed two rounds of cleaning - first to delete new lines and second to delete non-author writing like copyright notes. I then performed the third round of cleaning (lowercase, removing punctuation and digits), and created a document-term matrix using CountVectorizer. I also pickled more versions of these data frames to load throughout the different sections of my project.

## Exploratory Data Analysis

### Wordclouds
First, I looked at the writings through most common words in each book. Taking the first 30 most common words and performing more cleaning, I created wordclouds using matplotlib and WordCloud libraries. 
(insert picture of wordclouds)


### Vocabulary size
I also looked at the vocabulary size of each author, calculated by the number of unique words. I also calculated the length of the book (total words), and 
