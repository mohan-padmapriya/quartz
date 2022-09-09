
So, you've got a bunch of tweets. You've got them split as positive and negative. People have had to do this sorting until now. You'd like to train a machine to do it. 


# Level 0: [[Logistic Regression]]
You have tweets, you have labels. You've got to train the weights in the machine.
## Preprocessing
Brief overview:
1. Import libraries (nltk), datasets and load and store tweets as strings in a list
2. Preprocessing involves -  
	1. Tokenizing the string
	2. Lowercasing
	3. Removing stop words and punctuation
	4. Stemming/Lemmatising
Now you have a list of words

## Steps
6. Get a frequency dictionary mapping each (word, sentiment) pair to its frequency. Function takes labels and tweets as input
```
def build_freqs(tweets, ys):
    """Build frequencies.
    Input:
        tweets: a list of tweets
        ys: an m x 1 array with the sentiment label of each tweet
            (either 0 or 1)
    Output:
        freqs: a dictionary mapping each (word, sentiment) pair to its
        frequency
    """
    # Convert np array to list since zip needs an iterable.
    # The squeeze is necessary or the list ends up with one element.
    # Also note that this is just a NOP if ys is already a list.
    yslist = np.squeeze(ys).tolist()

    # Start with an empty dictionary and populate it by looping over all tweets
    # and over all processed words in each tweet.
    freqs = {}
    for y, tweet in zip(yslist, tweets):
        for word in process_tweet(tweet):
            pair = (word, y)
            if pair in freqs:
                freqs[pair] += 1
            else:
                freqs[pair] = 1

    return freqs
```
Output: Dictionary of the form: {('happy', 1.0): 300, ('sad', 1.0): 0}


Now you have a frequency dictionary with all words and their frequencies for positive and negative frequencies

Essentially, your freq dictionary decides whether the word is positive or negative.

8. Convert preproccesed tweet lists into feature vectors with a bias. (Why the bias?)
Each tweet gets a feature vector

Feature vector: Bias, no of times word appears in positive tweets class, no. of times it appears in negative tweet

![Frequency Extraction](freq_ex.png) 

Example
Input tweet and freq dictionary. Loop through each word in each tweet. 
Eg: I am sad and upset
Start with *sad*  (*I, am* are stop words)
From freq dictionary, get freq for *'sad' with positive connotation*, append to 2nd column
Do same for *'sad' with negative connotation*, append to 3nd column
Then for *upset*

![Frequency Extraction](sent-anal2.png) 

Get matrix X by stacking all these feature vectors on top of one another

9. Run gradient descent by initialising weights, providing X and Y (labels for training). 
Get cost, and **updated weights**

10. Run sigmoid on test data using X (stacked feature vectors) and updated weights. You'll get predictions for *y*, a between 0 and 1. 
11. Construct list $\hat y$ with 0s and 1s, (round off y_pred values). THIS IS THE CLASSIFICATION, ANALYSED SENTIMENT. 
12. Compute accuracy by comparing $\hat y$  and test_y.

- Final sentiment classification given by whether 
--> How to error analysis?
--> Cost vs error what?



# Level 1: [[Naive Bayes]]
Basically this:

![](NB1.png)
Sample space for this is still pretty big. To narrow down sample space -
[[Conditional Probability]]
![](NB2.png)

$$\therefore P(X|Y) = \frac{P(Y|X). P(X)}{P(Y)} $$

## Procedure
1. Preprocess
2. Build a frequency dictionary

Concepts to keep in mind:
### 1. Laplacian Smoothing
- ![](lpsmooth.png)
- Probability of words that aren't in the corpus becomes 0. In order to avoid that, laplacian smoothing.
### 2. Log Prior
- Given a random word, what probability that it is positive vs negative?
- Ratio of total positive tweets to negative tweets
- For balanced data, log prior is 0 $logP - logN$
- ![](lp.png)

### 3. Log likelihood
- ![](pnw.png)
- ![](ll.png)

- ![](lambda123.png)
3. Write a program to calculate log prior and log likelihood (which is a dictionary full of words and their lambda value) 
4. Predict whether a tweet is negative or positive. Input log prior, log likelihood, tweets-
![](nb4.png)

5. Train, test, check error (error is the average of the absolute values of the differences between y_hats and test_y), and accuracy (1 - error)
6. Positive value indicates positive sentiment, vice versa


--> Can set threshhold for better results


# Level 2: [[Neural Networks]]
## Preprocessing data
1. Preprocess tweets
2.  Create Vocab which is a dictionary that assigns a value for each word in each tweet. Include Padding (0), Unknown (1), and EOS (2) tags.
3. 
