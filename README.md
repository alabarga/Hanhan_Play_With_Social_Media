# Hanhan_Play_With_Social_Media
play with social media and data mining


<b>Semantic Web</b>

* Microformats- Many website embed unified formats in the web, like those resume blocks in LinkedIn, small geo info in many websites like Wiki. This type of blocks have unified class name in HTML and they makes your data extraction life easier.
* Microformats Example - Extract geo data form Wiki: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/microformats_extract_geo.py
* It will be good to see the location you are parsing from google map, here, I'm makin your life easier :)
 * Type `jupyter notebook` in your terminal (after you have installed IPython and Jupyter Notebook)
 * In the opened IPython Notebook in your browser, type all the code in this image: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/Geo_Visualization.png
 * Now you will see the map of that location
* Without codind and find all the embeded microformat in a web page: http://microform.at/

* RDF (Resource Description Framework) - the semantic web's model for defining and enabling exchange of triples (subject, predicate and object of the sentence) 
* <b>FuXi</b> - A powerful logic-reasoning system for the semantic web that uses a technique called Forward Chaining to deduce new information form existing info by starting with s aet of facts, deriving new facts from the knows facts by applying a set of logical rules, and repeating this process till a particular can be approved or diapproved, or there is no more fact to derive.  https://code.google.com/archive/p/fuxi/wikis/Installation_Testing.wiki
* N3 - Simple but powerful syntex that expresses facts and ruels in RDF, FuXi is also using it. https://www.w3.org/DesignIssues/Notation3


* Extract Recipe data: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/microformats_recipe_data.py


*********************************************

<b>Twitter Mining</b>

1. Create a twitter app and get CONSUMER_KEY, CONSUMER_SECRET, ACCESS_TOKEN, ACCESS_TOKEN_SECRET: https://apps.twitter.com/
2. A convenient way to get your own twitter data: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/twitter_oauth1.0.py


*********************************************

<b>Reddit Mining</b>

* Topic Modeling
 * About Spark LDA: https://databricks.com/blog/2015/03/25/topic-modeling-with-lda-mllib-meets-graphx.html
 * Spark LDA MLlib description: http://spark.apache.org/docs/latest/mllib-clustering.html#latent-dirichlet-allocation-lda
 * Spark LDA sample Python code: http://spark.apache.org/docs/latest/api/python/pyspark.mllib.html#pyspark.mllib.clustering.LDA
 * Spark DistributedLDAModel (it has `topDocumentsPerTopic()`, `topTopicsPerDocument()`, `topicDistributions`): http://spark.apache.org/docs/latest/api/scala/index.html#org.apache.spark.mllib.clustering.DistributedLDAModel
 * DistributedLDAModel Scala code:
 
 http://stackoverflow.com/questions/33072449/extract-document-topic-matrix-from-pyspark-lda-model

 http://spark.apache.org/docs/latest/mllib-clustering.html#latent-dirichlet-allocation-lda
 
 * Spark word2vec: http://spark.apache.org/docs/latest/mllib-feature-extraction.html#word2vec
 * My code - tf-idf & LDA modeling: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/reddit_tfidf_LDA.py
 * My code - word2vec & kmeans: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/reddit_word2vec_kmeans.py
 
<b>Note:</b> LDA is a type of clustering too. In my code, so far I think word2vec is more convenient to track origional words and see whether the results make sense. So far, I haven't found a way to convert the numbers generated by Spark HashingTF and Spark LDA into the original words....
-- LDA can be used when you have both training and testing data, just want to to prediction
-- Word2Vec can be used to search for silmilar words, with KMeans, they can help group words into clusters. In my code, I am also generated the histogram, showing the cluster distribution for each post. Using the numbers in histogram, we can do prediction like LDA. For example, in the training data, we have "yes"/"no" as label, we can use LDA or (generated histogram here + predictive model) to predict the label of the test data

 * scikit-learn NMF smaple Python code: http://scikit-learn.org/stable/auto_examples/applications/topics_extraction_with_nmf_lda.html
 * My code: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/reddit_scikit_topic_modeling.py
 * In my code, I am using NMF and LDA respectively to extract top topics. And Python Scikit-Learn will simply give you the top topics! So straightforward!! Especially feel great after struggling doing this with Spark topic modeling algorithms.
 
<b>To Sum Up: </b>Obviously, if I just want to extract top topics, using scikit-learn is very convenient. But if I want to do predictive modeling, with training and testing data, Spark algorithms are still good choices
 
* Entity/Interaction Extraction

 * My code - top NN entities: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/reddit_NN_entities.py
 * My code - top interactions: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/reddit_interactions.py
 
<b>As you can see,</b>, sinple NLP techniques still plays great role in text analysis. I just extracted the top 50 NN entities, we could already find trends and topics that popular and make sense. When I go deeper into the semantic layer, we can see NNVBNN interactions are already smary enough to make more sense

* Key Words Search
 * 2 methods for key words search: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/reddit_keywords_search.py
 * Reddit posts destribution on cities and countries: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/reddit_distribution.py
 * I think the distribution can bew extended to more interesting level. After running my code you will find that most cuddling new posts are from London, but US is the country that has top 1 number of reddit new posts at this time, the posts amount is far more than any other countries. This can be ectended to culture mapping based on countries, states and time series analysis.

*********************************************

<b>Pokemon Go</b>

It's so popular now, I don't want to play this game, but it will be so much fun to play with its data

* Potential Data Sources
 * https://pokeapi.co/
 * Google+ page: https://plus.google.com/117587995505124458333/posts
 * Yelp, Instagram, Snapchat, Flickr, GitHub, Twitter: https://www.instagram.com/pokemon_go_/

* Yelp Exploration
 * <b>Code Part 1</b>: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/Pokemon_Yelp_Explore_Part1.py
 * FINDING_1: Yelp search could return you very accurate business category when you type a search term, and it's NOT based on simple key words search, since I have checked those returned busienss results, very few of them contain the key words in the search term. The reason I think Yelp search is accurare, is because when I put 'Pokemon' as search team, it returns toy store as the top category, and check their snippet_text, some have mentioned pokemon card game or pokemon center (a game center). But when I put 'Pokemon Go' as the searth term, most of them are restaurant and later when I checked their snippet_text, many of them are Pokemon station
 * FINDING_2: For the same search term, close locations share very similar trends. For example, in my code, I used cities in Great Seattle and Metro Vancouver, they have very similar results, but when I input Los Angeles/New York, they have different trends. Based on this, I am thinking, would the order of categories help find close location, and therefore define culture circle?
 

*********************************************

<b>FOR BUSINESS</b>

-- <b>Yelp</b>
* I really like Yelp business API! So well documented and easy to use! Yelp search and business API are really powerful, when the merchant info is very limited, but based on the list generated by Yelp API, can get lots of insights for further data analysis.
* Search API: https://www.yelp.com/developers/documentation/v2/search_api
* Business API: https://www.yelp.com/developers/documentation/v2/business
* Yelp Python: https://github.com/Yelp/yelp-python
* Manage Yelp API keys: https://www.yelp.com/developers/documentation/v2/authentication
* My code: https://github.com/hanhanwu/Hanhan_Play_With_Social_Media/blob/master/yelp_search_business.py
 * The code here is very simple, but the output is poswerful. You just set the param as the term you want to search, define the location, then you will get a list of business output, the search results are good


*********************************************

<b>Good To Read</b>

Mobile Network Analysis through mitmproxy: http://www.shubhro.com/2014/12/18/reverse-engineering-kayak-mitmproxy/


*********************************************

<b>NOTES</b>

-- Flights API   (It seems that they are all used for commercial purpose, difficult to find free data...)

* Wego
 * http://support.wan.travel/hc/en-us/articles/200300495-API-Overview
 * http://support.wan.travel/hc/en-us/articles/200191669

* FlightAware  (The API Homepage looks so good, but needs your credit card info before getting API key...)
 * http://flightaware.com/commercial/flightxml/
 * World Aorport Database (not free): http://flightaware.com/commercial/data/airports
