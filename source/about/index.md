---
title: Hello! Welcome!!!
type: "about"
comments: false
---

I've been thinking, how am I gonna introduce myself? How should people get to know me?  
<!-- more --> 
Many profs and advisors would say: "Write a good resume, put it on **[LinkedIn](https://www.linkedin.com/in/saferfang/)**, then people will know you." 
NAH THATS NOT TRUE.  
Those softwares would probably just trash my resume.  
So if you are a real person but you don't want to spare 5 seconds on my paper, how about 1 second?  
Here:  
![](https://i.imgur.com/H5VF5lE.png)   
Thats it! Thats all about me! A data guy! At least thats what my resume tells me.  
Waht? Not the guy you are looking for? Well, I tried. I'll be better. Thank You.  

Getting a bit curious on how I did this?  
Code myself in **[R](https://en.wikipedia.org/wiki/R_%28programming_language%29)** 😁

```R
# Get all the libraries to dissect myself
library(pdftools)
library(tm)
library(wordcloud)

# Load my resume
text <- pdf_text("Resume.pdf")
resume <- strsplit(text, "\n")
head(resume) # Doesn't look good to you? No worries you wouldn't see it here.

# Convert to a vector source
resume_source <- VectorSource(resume)
# Generate volatile corpora
resume_corpus <- VCorpus(resume_source)

# Create data cleansing function
clean_corpus <- function(corpus, stop_words = c(stopwords('en'))){
  corpus <- tm_map(corpus, removePunctuation)
  corpus <- tm_map(corpus, removeNumbers)
  corpus <- tm_map(corpus, content_transformer(tolower))
  corpus <- tm_map(corpus, removeWords, stop_words)
  corpus <- tm_map(corpus, stripWhitespace)
  return(corpus)
}

# Clean myself, just like those softwares
clean_corp <- clean_corpus(resume_corpus, stop_words = c(stopwords('en'),'clients','aug','business'))

# Construct term document matrix
resume_tdm <- TermDocumentMatrix(clean_corp)

# Generate keyword_count table
resume_m <- as.matrix(resume_tdm)
```

Done with the formating and cleaning, now lets have a look?  

First, barplot:
```R
# Visualize keyword_count
term_frequency <- sort(rowSums(resume_m), decreasing = T)
barplot(term_frequency[1:15], col = '#B2ABD2', las = 2)
```
![](https://i.imgur.com/WEAuNlC.png)  

Then, the wordcloud:  
```R
resume_data <- data.frame(term = names(term_frequency), num = term_frequency) #Data frame for word cloud
wordcloud(resume_data$term, resume_data$num, max.word = 30, colors = c('grey80','darkgoldenrod1','tomato'))
```
![](https://i.imgur.com/H5VF5lE.png)   

Okay, now you know me.
Thank You. Wish you have a nice day!