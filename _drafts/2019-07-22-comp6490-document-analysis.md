---
layout: post-mathjax
title: COMP6490 - Document Analysis
---

## Contents

* Information Retrieval
* Machine Learning
* Natural Language Processing
* Information Extraction

## Information Retrieval (IR)

### boolean retrieval

#### information retrieval

* why? information overload.
* collection: a set of documents.
* IR system's goal: retrieve documents with information that is relevant to the use's information need and help the user complete a task.
* key objectives: effectiveness and accuracy.
* IR deals with unstructed data (vs DB).
* IR, statistical understanding of language, handle large scale problems (vs NLP).

#### term-document matrix

* boolean query with expressions AND, OR and NOT.
* boolean model provides all the candidates ranked by relevance.
* incidence matrix and incidence vector, not efficient.

#### inverted index

* inverted index, efficient data structure for boolean retrieval.
    - dictionary: a set of unique terms. e.g. BRUTUS.
    - posting: variable-size array that keeps the list of documents given term. e.g. (1, 8, 12).
* construction:
    1. token sequence, keep list of (token, docID) pairs.
    2. sort tuples by terms and then docID.
    3. multiple term entries in a single document are merged, split into dictionary and posting. add the frequency information.

#### boolean retrieval with inverted index

* linear time retrieval algorithm. 
* answer any query which is a boolean expression.
* good for precise query: match or not.
* limitation: not good for majority of users, often result in too few or too many results.

#### text pre-processing steps

* tokenization, chopping a document into tokens.
* stopwords, remove most common words in a language. e.g. the, a, to, of.
* normalization, keep equivalence class of entries. e.g. U.S.A and USA.
* stemming, turns tokens into stems (not always a real word). e.g. authorize, authorization $\Rightarrow$ authoriz.
* lemmatisation, turns words into lemmas (dicitionary entries).

#### bag of words (BoW) assumption

* not caring about the ordering of tokens in document. a document is a collection of words.
* use BoW assumption throghout IR part.


### ranked retrieval

#### ranked retrieval

* given a query, rank document according to some criterion.
* find $Score(d, q)$, $d:$document. $q:$ query.

#### weighted fields scoring

* field(zone) in document. document is a semi-structured data.
* limit search scope within a certain field.
* basic field index, field index in posting.
* weighted field approach. importance of term is not the same.
* assign different weights to terms based on their location (field).  
    $l$ fields, $g_i$ the weight of field $i$, $\displaystyle\sum_{i = 1}^l g_i.  
    $Score(d,t) = \displaystyle\sum_{i = 1}^l g_i \times s_i$, where $\begin{cases} s_i = 1, &t \text{ is in field } i\\ s_i = 0, &\text{otherwise} \end{cases}$.  
    a score of a quert term range $[0, 1]$.

#### term frequency and inverse document frequency

* term frequency $tf_{t, d}$, the number occurrences of term $t$ in document $d$.  
    $Score_{tf}(d, q) = \displaystyle\sum_{i = 1}^n tf_{t_i, d}$. $q$ is a set of query terms $(t_1, t_2, \cdots, t_m)$.
* every query term has an equal importance.
* document frequency $df_t$, the number of documents in the collection that contain term $t$.
* high frequency $\Rightarrow$ not important. low frequency $\Rightarrow$ important. e.g. stopwords.
* inverse document frequency $id_{f_t} = \log(\frac{N}{df_t})$, $N$ the total number of documents.
* TF-IDF, $tf-idf_{t, d} = tf_{t, d} \times idf_t$.  
    $Score_{tf-idf}(d, q) = \displaystyle\sum_{i = 1}^m tf-idf_{t_i, d}$.

#### variants of TF-IDF

* limitation of tf-idf scoring, heavily relies on the frequency of terms.
* sublinear tf scaling. logarithmically weighted term frequency.  
    $wf_{t, d} = \begin{cases} 1 + \log tf_{t, d}, &\text{if } tf_{t, d} > 0 \\ 0, & \text{otherwise} \end{cases}$.  
    $wf-idf_{t, d} = wf_{t, d} \times idf_t$.
* limitation of tf-idf or wf-idf scoring, prefer longer document.
* normalized term frequency.  
    $ntf_{t, d} = \alpha + (1 - \alpha) \frac{tf_{t, d}}{tf_{max(d)}} \in [0, 1]$, if $tf_{t, d} > 0$.

#### vector space model

* document and query as vectors.
* document similarity in vector space. cosine similarity.  
    $sim(\overrightarrow{d_1}, \overrightarrow{d_2}) = \frac{\overrightarrow{d_1} \cdot \overrightarrow{d_2}}{\mid \overrightarrow{d_1} \mid \times \mid \overrightarrow{d_2} \mid} \in [0, 1]$.
* score function of vector space model.  
    $Score_{vsm}(d, q) = sim(\overrightarrow{d}, \overrightarrow{q})$.

#### relevance feedback

* relevance feedback. ask explicit feedback from user, instead of letting users refine query.
* rocchio algorithm, vector space implementation of feedback algorithm.  
    $\overrightarrow{q_m} = \alpha \overrightarrow{q_0} + \beta \frac{1}{\mid D_r \mid} \displaystyle\sum_{\overrightarrow{d_i} \in D_r} \overrightarrow{d_i} - \gamma \frac{1}{\mid D_{nr} \mid} \displaystyle\sum_{\overrightarrow{d_j} \in D_nr} \overrightarrow{d_j}$.

### tolerant retrieval

#### dictionary data structure

* hashtable.
    * pros: fast $O(1)$.
    * cons: hard to find minor variants, no prefix search, expensive to rehash.
* tree, binary tree (simplest) and B-tree (usual).
    * pros: solve prefix search problem.
    * cons: slow $O(\log M)$. expensive to rebalance.

#### wild-card query

* query processing.
* permuterm index.


