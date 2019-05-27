# DQNN_papers
This github repo consist of all the paper I read while in YAHOO! JAPAN and a short summary of each paper for further usages. The purpose of the work was mainly to find a way to model user in a broader perspective. This repo is a private property of the author and Yahoo! JAPAN corporation.


# 1. Patterns of Search: Analyzing and Modeling Web Query
Refinement, Tessa Lau
and Eric Horvitz
http://erichorvitz.com/queryrefine.pdf

# 2. Inferring the Demographics of Search Users
http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.383.839&rep=rep1&type=pdf

They plan to figure out the demographic of an user for instance, age gender based on two source datsets, one is the social dataset consisting of the facebook pages the user has liked and the other one is corresponding serach queries. They wanted to predict demographic but noted that training the model on query session data is not useful as most of the time it is not annotated. So they used a concept of transfer learning. They trained their model on the facebook's my personality dataset which contains the pages likes by a particular user and some demographic information. Then using this model to predict demographic on the query datset.
1. They got the facebook data, which is labelled and query data which is not labelled.
2. They mapped the fb and query data to a same distribution to train an ML model.
3. From FB likes to  a 219 dimensional vector. Every liked page was converted to a query(for example, like page steve jobs was converted to a bing query), then the top 10 results were classified into 219 categories given by the ODP, the categories are for instance, art/sports etc. These 219 vectors were then used in classification.
4. Similar thing was done for the query dataset.
5. Trained a logit model with lasso regularization for age predcition.
6. For gender prediction they used two different binary classifiers.
7. The accuracy for gener classification was almost 85% while for age it was 75% on FB dataset and 80% and 70% respectively on the query dataset
