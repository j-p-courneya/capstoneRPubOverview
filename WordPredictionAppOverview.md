Word Prediction App
========================================================
author: Jean-Paul Courneya
date: 29 May 2018
autosize: true
transition: rotate

Executive Overview
========================================================

The goal of this final assignment was to develop a word prediction app. 

- Students were provided a corpus which served as the basis for developing the algorithm running on the back-end to auto-complete phrases. An exploratory analysis was performed to get a sense of features of the corpus
- An algorithm was developed using a n-Gram probabilistic-language-modeling-based back-off approach which is efficient and accurate
- A data product was then created which uses Shiny running the prediction algorithm that accepts an n-gram and predicts the next word.

Understanding the Corpus
========================================================
- Source of the data
<small> The corpus used for building the model was provided through a collaboration between the course instructors and Swiftkey. The corpus is a collection of blog posts, a list of news articles, and a list of tweets that were downloaded from the [repository] (https://d396qusza40orc.cloudfront.net/dsscapstone/dataset/Coursera-SwiftKey.zip "Swiftkey Dataset") provided in the course.</small>
- Decide on a text processing package for R
<small>Quantitative text analysis in R can be done using a variety of different R packages (baseR, tm, tau, tidytext, openNLP). For this app [Quanteda] (https://quanteda.io/ "Quanteda Homepage") a quantitative text analysis tool for R  which is cross-platform, very robust, and [fast] (https://quanteda.io/performance/ "COMPARING THE PERFORMANCE OF QUANTEDA WITH OTHER R PACKAGES") . Our app required an R package which can create a corpus, tokenize the text, create nGrams, and generate document feature matrices.</small>
- Prepare the text for the language model: <small> Combine the Corpus, remove non-ASCII characters, convert text to lowercase, tokenize the corpus, remove numbers, punctuation, symbols, twitter handles, separators, remove profanity, create n-grams and DFM </small>
Developing the predictictive Algorithm
========================================================


```r
if (candidateIs5gram) {
  score = matched5gramCount / input4gramCount
} else if (candidateIs4gram) {
  score = 0.4 * matched4gramCount / input3gramCount
} else if (candidateIs3gram) {
  score = 0.4 * 0.4 * matched3gramCount / input2gramCount
} else if (candidateIs2gram) {
  score = 0.4 * 0.4 * 0.4 * matched2gramcount / input1gramCount
}
```


Using the App
========================================================
1. Access shiny app here
2. Type your desired phrase into the text box.
3. The application will then try to predict the next word and display it.
