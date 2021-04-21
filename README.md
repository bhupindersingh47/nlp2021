# NLP (Text Mining) Project Repository - Ryerson University [Winter 2021] 

# Group 12 

# Title: Topic Modelling and Search with Top2Vec   

#### Members' Names:  
          Bhupinder Singh  
          Richa Sharma

#### Emails:  
          bhupinder1.singh@ryerson.ca  
          richa4.sharma@ryerson.ca 

  
## Dataset URL:  
https://www.kaggle.com/dangelov/covid19top2vec  
***Please note that the data files are larger than 1GB, therefore GitHub does not allow to upload them.  
I have provided the URL to the dataset herein.***  

## Note:  
***Please note that the main project file is NLP_Final_Project_Top2Vec_BhupinderSingh_RichaSharma.ipynb***  
***The file Top2Vec_Training_&_Application_[secondary_notebook].ipynb contains additional implementation details for pre-processing the huge dataset and for training the model with different parameters.***  

## Note:  
The latest version of Top2Vec is 1.0.24. However, in the process of running the code,  
I ran into many errors with numerous versions of the library.  
I then installed every version of Top2Vec backwards.  
1.0.6 is the version that is running correctly without any errors.  

## Note:  
Please check ***src*** folder for Top2Vec source code.  

## Introduction:  
### Problem Description:  
Topic Modeling is used for discovering latent semantic structure, usually referred to as topics, in a large collection of documents. Traditional topic modeling methods are Latent Dirichlet Allocation (LDA) and Probabilistic Latent Semantic Analysis (PLSA), which have several weaknesses despite their popularity. Top2Vec, the proposed model in the research paper that we studied, addresses these weaknesses and finds topics that are significantly more informative and representative of the corpus than the ones generated by traditional models.
  
### Context of the Problem:  
Organizing, searching and summarizing huge corpora of text is a significant problem statement in NLP. Topic Modeling is a type of statistical modeling that is used to discover the hidden semantic structure present in documents. These discovered topics can then be used to find high level summaries of a large collection of documents, search for documents of interest, and group similar documents together.  

In simple terms, Topic Modeling is a method for unsupervised classification of documents, like clustering on numeric data, which finds some natural groups of items (topics), even when we are not sure what we are looking for. The most widely used topic modeling method is Latent Dirichlet Allocation (LDA). The big idea behind LDA is the following: each document can be described by a distribution of topics and each topic can be described by a distribution of words. The aim of LDA is to find topics a document belongs to, based on the words in it.  

LDA and PLSA discretize the continuous topic space into an assumed number of topics (say t), and then model documents as mixtures of those t topics. This is one of the greatest weakness of these models, as the number of topics t or the way to estimate it is rarely known, especially for very large or unfamiliar datasets.  

Additionally, each topic produced by these methods is a distribution of word probabilities. As such, the highest probability words in a topic are usually words such as the, and, it and other common words in the language. These common words, also called stop-words, often need to be filtered out in order to make topics interpretable, and extract the informative topic words. Finding the set of stop-words that must be removed is not a trivial problem since it is both language and corpus specific.  

Also, these methods use bag-of-words (BOW) representation of documents as input which ignores the ordering and semantics of words. They also employ techniques like Stemming and Lemmatization, which do not recognize the similarity of words like big and large, which do not share a word stem.  

This brings us to the problem statement: how to address and overcome these weaknesses and build a better model for discovering topics. The approaches and solutions offered by Top2Vec are discussed and presented in subsequent sections.  

### Limitation About other Approaches:  
As discussed in detail in the Context section above, traditional topic modeling methods LDA & PLSA require the number of topics to be known, custom stop-word lists, stemming, and lemmatization, and rely on a bag-of-words representation of documents, which is less than ideal.  

### Solution:  
Top2Vec uses a Distributed Representations of Topics, employing the doc2vec model and its Distributed Bag of Words (DBOW) architecture, to learn jointly embedded document and word vectors. Following this, it performs Dimensionality Reduction, using the UMAP algorithm (Uniform Manifold Approximation and Projection) to help find dense areas. Clustering of documents is then undertaken using HDBSCAN (Hierarchical Density-Based Spatial Clustering of Applications with Noise). For each dense area, a numeric representation of the topic (topic vector) is then obtained by taking the arithmetic mean of all the document vectors in the same cluster. And finally, each document is assigned a topic number based on the nearest topic vector to its document vector.  
