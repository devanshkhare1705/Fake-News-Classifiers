# Fake-News-Classifiers

# Project Overview
This project aims to use machine learning to predict if an article describes real or fake news based on the words in its headline.

# Technical Implementation
This project uses decision trees to predict if an article contains real or fake news based on the words in its headline. The dataset comprises 1298 “fake news” headlines, sourced from https://www.kaggle.com/mrisdal/fake-news/data, and 1968 “real” news headlines, sourced from https://www.kaggle.com/therohk/million-headlines. The two sets are available in the clean_real.txt and clean_fake.txt. The 'train_test_split' method from 'sklearn' library was used to sort them into training, validation, and test datasets.

Decision trees were used as the approach for prediction in this case. The best parallel for them is a game of '20 Questions' (aka: 'Guess Who'). Just like human players ask questions sequentially to narrow down the answer space to one person, the trees in this case ask for the presence of words in the given headline to predict whether the answer label is fake. 

The fitting process focuses on structuring the tree so that the most informative words are searched for first; this is similar to how humans front-load those questions that eliminate as many options as possible. 'sklearn' methods were used to create and fit the trees in this case. Two different criteria were considered to for the loss to get optimal performance: 'Entropy' and 'Gini Coefficient' loss. 'Tree depth' was treated as a second hyperparameter to optimize for speed and performance. 

# Project Results
The best model in this project had a test accuracy of 77.96%, with a max depth of 100 nodes and the loss set to 'Gini Coefficient'. This feels relatively impressive - I'm not confident that every human can predict the truth of articles with 78% accuracy just based on their headlines. I believe the model's performance can be further improved by:

1. Adding other metadata such as the news source to the training dataset. The metadata could be added as a token to the input through helper functions.
2. Adding more training examples and increasing the maximum depth of the tree. We have to be mindful that more depth will increase inference time of these classifiers though, affecting their usability.

# Future Applications
These models could serve two purposes in the real world:
1) For readers - Is the news article reliable for forming opinions and taking decisions?
2) For publishers - Does the article come across as fake news based on its headline?

The models would work best when they're focused on more specific domains (e.g., exclusively one news topic or agency), since their inference time gets really high with large datasets. For more general news detection applications, architectures could also be set up where the article is routed to one of several independent decision trees based on its background.
