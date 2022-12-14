# Newswire-Analysis
![image](https://user-images.githubusercontent.com/43926813/207499689-4f4f0ee7-3563-46eb-9b94-9b117abfc1a9.png)


Analyzing and Classifying Newswires 

The objective of my project is to develop and use algorithms that can automatically group together news articles that have a similar meaning after being educated on collections of texts from newswires in a dataset.
I intend to use the concepts we learnt in class (INFO202) to build topic clusters and analyze the sentiments based on the word embeddings in the newswires. The concepts used here are categorization, tokenization, forming hierarchical structures, and semantic similarities with word embeddings. This can assist in directing us to develop a tidy and disciplined organization system for gathering and arranging massive amounts of text information. These word level embeddings, in my opinion, may be used to organize the topics in news articles to tackle the spread of misinformation. Additionally, I have applied the concept of grounded coding to assign codes (top 5 topics) to 40 documents from the dataset and compare them to the one generated by the LDA model using the Inter-Annotator Agreement.

# Implementation Steps:

1. Data Gathering: 
I made use of the open source data available on Reuters-Dataset (https://archive.ics.uci.edu/ml/datasets/Reuters-21578+Text+Categorization+Collection) where a large collection of news articles is maintained. The documents were assembled and indexed with categories by personnel from Reuters Ltd.

2. Preprocessing: 
Data cleaning, Exploratory Data Analysis: Based on my preliminary idea by looking at the dataset, I will be conducting 1 and 2 level data cleaning for the acquired data, preprocessing to remove superfluous terms and suppress some words, altering various versions of the same word, and finally discarding words with illegal characters.The same set of texts has been put through a preprocessor function of the text, to standardize the different forms of the words using Stemmer, and Lemmatizer. Moreover, the same has been processed through the removal of stopwords like is, am are which don't add much value to the meaning of the text.

3. Bag of Words:
The wrangled set of texts has been processed to the word dictionary of NLTK having an extensive English Words dictionary. Using these texts, I generated embeddings by deploying the Bag of Words model. For comparison, I have also implemented generating the embeddings using tf-idf scores based on term frequency and inverse document frequency, which we can toggle when running the downstream process.


4. LDA: 
For the current pipeline, Bag of Words is used as the underlying technique for embeddings and the model of LDA, which is an unsupervised learning method based on the probabilities of the words in the texts is used on 7769 text documents of editorials.
Further, I have generated 10 topics from a collection of 7769 documents to enable ease of understanding the same.
Using the topic words from each of the 10 topics, I formulated tags for the categories being represented in the news articles.

5. Grounded Coding and IAA score
Using the same set of codes, I have done grounded coding on a set of 30 documents as attached in the excel file to produce the Inter Annotator Agreement Evaluation report to benchmark whether the system is good enough over human-driven evaluation systems using the Kappa score.

6. Visualizing : I intend to use a relevant visualizing generator API pyLDAvis to simplify the visualization of any vector having many dimensions and convert it into human understandable visualizations.

# Instructions to run the project

1. Download the News_Analysis.ipynb and open it on Jupyter Notebooks or Google colab.
2. We first download and run all the dependencies of NLTK so if you have the dependencies installed, you can comment out the code in the first 3 code blocks. Next, the Reuters dataset present in the nltk corpus is imported and cleaned.
4. The entire code can be run using a single .ipynb file. The visualizations generated are exported to the BOW_visualizations.html 

# Visualizations and Interpretations

1. Below is the pyLDAvis generated topic clusters according to the documents dataset. <br>
By deploying the LDA model, I have used pyLDAvis for visualizing the topic clusters identified by the top 2 principal components. This visualization is exported as an HTML file and is present under the visualizations folder. These clusters are represented on a plot that places them according to their relative intertopic distance by calculating the multidimensional scaled distance. There is a slider to adjust the relevance matrix, that decides the closeness of the displayed words to a particular topic cluster center. Hovering over the topic cluster, we can also see the top 30 relevant words in that topic which is displayed as a bar plot and the relative frequency of the word with the total frequency in document collection.
![Recording 2022-12-13 at 19 46 38](https://user-images.githubusercontent.com/43926813/207500628-775404e6-82ce-4051-9914-52dbb637d9be.gif)

2. Displayed below is the word cloud for each topic, the most frequently used words within the cluster are displayed in their relative font sizes. The most frequently used word has the biggest font size and as the frequency decreases the font size also decreases. This word cloud helped me identify the main theme of each cluster and assign the topic names to the LDA model.

![word_cloud](https://user-images.githubusercontent.com/43926813/207500179-d0c083f1-d9b3-437c-b287-b17d3d82039e.png)

3. I have also generated bar plots for identifying the percentage of the most frequently observed terms within 6 documents. This was useful to select the relevant topics within those documents as I was looking to avoid overlaps when selecting the topics for grounded coding.

![Topic_Percent](https://user-images.githubusercontent.com/43926813/207500230-86b9f10a-29ef-4092-91d8-4e4ee0f2d1ce.png)

![distribution_words](https://user-images.githubusercontent.com/43926813/207500239-87adea2e-bb74-4f4e-8508-85df1ade650a.png)
