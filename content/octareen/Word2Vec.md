#undigested

- [[Natural Language Processing]]
	- [[Embeddings]]



# What
![](word2vec_cs224n.png)


"Word2vec is a method to efficiently create word [[embeddings]]"
- Uses [[Distributional Semantics]], a distributed rather than localist representation that captures the notion of similarity in the vector itself.
- Trained word vectors are called *word [[Embeddings]]*

Although we know that the vector represents the word, we don't know what each dimension of the vector represents. 
Each dimension reveals something about the relationship between different word vectors. 
Each vector is of size $[vocab_length, 1]$.

## [[Cosine similarity]]

# Why
Machines use vectors to represent data all the time anyway. So let's use vectors to represent words as well. The added benefit with vectors is that it is easy to see and calculate how close two vectors are to each other, or in other words, how similar they are to each other.

## Word [[Embeddings]]
![](w2v1.png)
Similar words have similar values in certain dimensions.
<!--ID: 1625799979936-->


![](w2v2.png)
Analogies between words are also captured by these word embeddings. 

## Going from a word word model to a [[Language Models | language model]]
 We use mainly either of the following architectures to produce a [[Distributional Semantics | distributed representation]] of words -
 1. [[Skipgrams]]
 2. [[Continuous Bag-of-Words | CBOW]]
	 - To increase efficiency - [[negative sampling]]
<!--ID: 1625799979953-->



## Training
### The prediction function
The [[Probability]] we're calculating is $$P(W_{t+j}| W_t;\theta)$$
which is *the probability of predicting context words given a center word*
<!--ID: 1625799979969-->


There's one kind of vector for *center words (c)* and there's a different kind of vector for *context words (o)*

![](word2vec_cs224n3.png)

So the way we'd calculate it is -
![](word2vec_cs224n4.png)
 
- **Parameters $\theta$ are the contents of the vectors $u,v$**
- The exp is to make positives more positive
- [[dot product]] on top calculates how close 2 words are - basically one of the [[distance metrics]].
- We use [[softmax]], why? 

#### Summarising
![](word2vec_cs224n5.png)
<!--ID: 1625799979986-->


We need to optimise and minimise the function by iterating through values for the vectors. These are the parameters of the model.
And every word has 2 vectors, one as *center* and one as *context*.


### The [[loss function]]
![](word2vec_cs224n2.png)
<!--ID: 1625799980002-->


Uses concepts of [[Likelihoods | log likelihood]] and [[Naive Bayes]] and [[Laplacian Smoothing]]

### [[Optimisation]]
after a bunch of differentiating, we get the slope
![](word2vec_cs224n6.png)
<!--ID: 1625799980018-->


- The observed rep of the context word minus what the model thinks the context should look like (which is the expectation $p(x|c)$)
	- $p(x|c)$ - the weighted average of the rep of each word multiplied by the probability of it in the current model. 
- Therefore that's the difference between actual and expected context word.

- ****


#### Computation
![](word2vec_cs224n7.png)
<!--ID: 1625799980034-->


## Also read about - 
- [[BioVectors]]
- [[Intelligent Word Embedding]]
- 








#todo
- [ ] If not vectors, what else could you use to represent words? How would you capture similarity of two words?
- [ ] Does the [[Vector Space]]then represent the vocabulary? What would the subspaces represent?
- [ ] Is there a way of knowing what each dimension of a word vector represents? How would this be helpful?
> What if two words are orthogonal, what would it mean?
- [ ] Corpora to corpora, will the same dimensions of a word embedding reflect different things? Rather, would a word be defined by different vectors depending on the corpus? Yes, no?
- [ ] Assume/I guess the dimensions of the vector are reflective of the relationship between words in the corpus. English is a highly context-based language. As #JRFirth Firth said, *"_You shall know a word by the company it keeps_"*. Therefore, the dimensions of a word vector tell is associated with the company it keeps. Would Word2Vecs work for languages like sanskrit. Rather, what can the [[Grammatical structure of Sanskrit]] add to this discussion?
- [ ] How is a word2vec defined?
- [ ] Analogies between words are also captured by these word embeddings. But how does this work? 
>         - *king - man  + woman = queen* --> man:king::woman:queen. Similar to tall:tallest::long:longest.
- [ ] When would you use skipgrams, when CBOW?
- [ ] How does Word2Vec preserve semantic and syntactic relationships?
- [ ] In the objective function, why log, why over *T*, why negative sign?
> Words like *that, and, because* occur pretty often, so won't they be predicted more often than is accurate?


------
- [Visual guide to Word2Vec - Jay Alammar](https://jalammar.github.io/illustrated-word2vec/)
- [CS224N - Lecture 1](https://www.youtube.com/watch?v=8rXD5-xhemo&t=2674s)
	- Last part of this lecture deals with properly calculating gradient descent by taking partial derivatives with respect to context and center words. Important to work out.


  

> Communication through time and through space and organisms

-   The scope of human language is sooper huge. It's not simply a formal language.
-   Language serves the informaion function, social function, etc etc
-   Human computer network, networking language is human language
-   Development of language was HUGE. And then writing.
-   Human language is super slow though.So we make a bunch of assumptions
-   What is _meaning_?
-   What's the limitation of a dictionary, or WordNet. Synonym sets?
-   One-hot vectors
-   But one-hot vectors are huuuuuge. Also do not convey the relationship between words, or shed any light on context
-   word similarity tables? Oh but their huuugr.
-   So rep of word must also have info about its relationship with other words
-   Firth You shall know a word by the company it keeps
-   The way of defining stuff in sanskrit - everything it is not (?)
-   Localist to distributed rep
-   Vector spaces! Amd PCA. Elaborate on this? Is there meaning in diff dim and directions of vector space

## 

Word2Vec

-   Corpus is
-   What words come up in the context of _word_?
-   **_Words in the contexto f other words_**

# 

Questions

1.  Cosine similarity and dot product, what's the difference?
2.  In a word3vec, what does each dimension stand for?
3.  How are these word2vecs defined?
4.  This awesome thing about analogies needs more attention -  
    
    ![](app://local/home/padmapriya/Notes/Images/link1.png?1622860480472)
    
5.  The conceptual parent of word embeddings: the neural language model - **_elaborate, justify_**
6.  Word models (word2vec) to language models (something you use for autocorrect and applications like that)
7.  What exactly is an _embedding`_