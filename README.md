# DQNN_papers
This github repo consist of all the papers I read while in YAHOO! JAPAN and a short summary of each paper for further usages. The purpose of the work is mainly to find a way to model user in a broader perspective. This repo is a private property of the author and Yahoo! JAPAN corporation. 

Copyright © 2019 Yahoo!JAPAN. All Rights Reserved.


# 1. Neural Demographic Prediction using Search Query
https://dl.acm.org/citation.cfm?id=3291034

The basic idea of the paper is to model user based on his/her demographic for better personalize search experience.They employ a deep learning based approach to classify the user into certain demographic aspects given his/her search history. They learn the user representation using his query over a time, and then classify him/her based on demographics such as gender or age. They have three main structures inside their model, a word encoder a query encoder and a classifier.
1. They take individual words of a query and learn its embedding through standard NLP methodologies like word2vec to learn a 200 dimensional vector representation of a word.
2. The they pass it through a convolution layer to capture the local context of every word in the query.
3. Then they pass it through an attention model. This constitutes the word encoder.
4. The output of attention network is feeded again to a CNN layer to capture the context of queries.
5. Then it is passed through an attention network.
6. Since all the previous queries have some importance while deciding the demographic, they use an attention model to capture that importance.
7. In the end they pass it to a classifier.

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

# 3. Implicit User Modeling for Personalized Search
http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.61.918&rep=rep1&type=pdf
Their model tried to model user behaviour, particularly their intents as a function of time. They plan to do it, solely on the basis of the query search data of the user over a time. The computation will be done on the client side hence reduces the burden on the servers. So basically they plan to rank the results shown for a particular query in a more personalized manner. For example "java map" could mean two entirely different things for a programmer and a traveller. Also a programmer can become a traveller too, so the results shown must update dynamically according to the present user model.
1. They deisgned a decision theoretic model which has 3 tasks to do at every point of time.
2. User model updating: Monitor any useful evidence from the user regarding
his/her information need and update the user model as soon as such
evidence is available.
3. Improving search results: Rerank immediately all the documents that the user has not yet seen, as soon
as the user model is updated.
4. The user model m assumes to come from a distribution M. And corresponding to every request q, an action a has to be done such that it maxmizes the probability of "viewing/clicking" the data, or an action which has maximum relevancy for the user.
5. So basically the task is to minimizes the loss which is L(q,a,m) and is function of the query, action taken and the user model at a particular time.
6. As mentioned earlier, the updates on the user model "m" is dynamic and after every query it gets updates.

# 4. Text Classification Research with Attention-based Recurrent Neural Networks, C. Du, L. Huang
In this paper they propose a classification model for classifying texts using the concept of attention on top of an RNN like structure. The attention model is followed by a classifier, which gives output as a softmax function.
1. They use Bidirectional LSTM after an embedding as an usual setting to learn the context of a sequence of characater or a senetence to be precise.
2. On top of that they use attention model, which outputs weights or priority to a gives section of sequence.
3. This structure is followed by a softmax classifier
4. The loss function used is a negative of log-liklihood with an L2 regularizer.

# 5. Convolutional Neural Networks for Sentence Classification
https://arxiv.org/pdf/1408.5882.pdf
This paper tries to show the power of CNNs in tasks such as text classification under the usual setting of CNN. After learning embedding using standard techniques like word2veq from a vocabulary table, a sequence of words is represented as a matrix or an image in 2D form. For example, representation of a word becomes a row and you stack representation(word2veq) below the representation of previous word's representation to make a 2D matrix or image like structure. 
For eg, 
i     ------[a1,a2,......,an]
don't ------[b1,b2,......,bn]
like  ------[c1,c2,......,cn]
food  ------[d1,d2,......,dn]
The structure is used with usual padding wherever needed.
1. Learn the embedding using standard embedding techniques.
2. Representation sequence as a 2@ matrix or image
3. Use kernels for calculating convolution as ususal
4. Make a dense layer
5. Then classify using a softmax layer

# 6. Attention-Based Bidirectional Long Short-Term Memory Networks for Relation Classification
This paper is similar to the paper mentioned in [4]. The architecture, the model and the approach is exactly same. I don't know how both of the papers got published. The only difference is the task on which the model is used.




