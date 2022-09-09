![](ben-david1.png)
![](ben-david2.png)

***About input and output spaces***
![](cbmm_slt3.png)

True risk
![](ben-david3.png)
- D stands for probability of incurring an error

So, what is the best learner strategy?

### Philosophy
![](cbmm1.png)


# Another approach
So consider a bunch of data you've got. You want to describe it. But not simply describe what you see, but go beyond what you've collected. 
![](cbmm_slt1.png)

Therefore, find a *function/hypothesis*

When you look at this (particular) training data, two misconceptions -
		- number of data points in the training data
		- input dimension can be many more than one
		
### What we have
1. Probability distribution
2. Loss function, also risk/cost

What we're trying to do is minimise the expectation of the loss with respect to the pairs x and y, or the integration of the function with respect to the distribution.
$\rho$, the distribution, is fixed but unknown. That is the problem.
So all you have is these pairs from the distribution. Therefore, we'll only ever have an imperfect approximate solution.

> A. What is expectation, what does is have to do with integration?
![](cbmm_slt2.png)

What can you say about the distribution $\rho$?
- It can be decomposed to a marginal and conditional distribution
- Why is this important? That is what seperates the input from the output, the *x* from the *y*
- Therefore, the relation between input and output is not deterministic
> B. What is marginal and conditional distribution? Does this have anything to do with IID?
> What if samples are not independant? Non-iid sample?

![](cbmm_slt4.png)
> C. What's conditional distribution, gaussian noise, regression etc etc? So when we're trying to reduce error, are we just getting rid of *noise*? ***Important***
> Noise introduces that aspect of uncertainty to the problem (how exactly?)

#### More about input spaces:
- When you have a distribution, depending on how the distribution looks, you're more likely to sample points from a certain area compared to other areas
- ![](cbmm-dist-sampling.png)
--> **Since dist is heavy at the centre, you're more lileky to sample points from there. Which doesn't give you a picture of what the true function is like (true function is the graph on the top, so by sampling only stuff in the middle, you don't get a proper sense of the function)**

**Papayas are 2D vectors that exist in a 2D space. Take a random 2D vectoe from the dist. Is it going to be a papaya? No. Papayas occupy some region in the 2D space. Additionally, not all features may be independant of each other; colour might be dependant on softness. Therefore, we may reduce dimensions.**

**Or is it a distribution of papayas itself, with real papayas occupying some region?**
(Same thing?)
> What are support of the marginal and the marginal distribution?1
- 
## [[Empirical Risk Minimisation]]
Why?
- Dunno anything about *f* or the distribution, but I do know the sample. If I find something that works well on the sample, then it's good enough. Therefore ERM:
![](ERM.png)
Therefore empirical error
Fraction of points on which *h* errors

> 1. How is it different from the [[Loss function]]? How is it different from true risk?
> ![](ERMvsloss.png)
> For every decision you make (for every $f(x)$ you choose and are revealed the *y*), the loss function tells you the price you're going to pay
> 2. Why do we assume f? What's realisability got to do with that?
> 3. If we confirm existence of *f*, aren't we confirming softness and colour are definitely predictors of taste? What implications?
> 4. In order to obtain a case of 0 empirical risk, to pick a h with 0 error, rule -
![](ben-david4.png)

But if this is the rule, and turns out all papayas in the world are actually tasty, then you'd still be predicting not tasty for papayas that are not in the training data. (Because according to the rule, N for otherwise). Therefore not a good model. 

***This is overfitting***
(drumroll, super important)

> 5. Why aren't there any contradicting elements in the sample? (same softness, same colour cannot give one tasty one not tasty)

## [[Overfitting]]
> Why is ERM prone to overfitting?


- Similar to what the pigeons did in the pigeon superstition problem. In that case, what was necessary was *prior knowledge*

***Under-fitting --> high bias, low variance (less features)***
***Overfitting --> low bias, high variance (more features)***
- *Underfitting, or high bias, is when the form of our hypothesis function h maps poorly to the trend of the data. It is usually caused by a function that is too simple or uses too few features. At the other extreme, overfitting, or high variance, is caused by a hypothesis function that fits the available data but does not generalize well to predict new data. It is usually caused by a complicated function that creates a lot of unnecessary curves and angles unrelated to the data.*

**Solution (generally)**
![](overfit-sol.png)
 Note: Feature vector is the x vector. Therefore features = inputs. Theta is the parameter vector, basically the weights.
--> *To guard against overfitting, we introduce some prior knowledge, which is inductive bias*

> 5.5 How to implement inductive bias? Relationship between inductive bias and overfitting

## [[Inductive bias]]
> *Inductive reasoning is the process of learning general principles on the basis of specific instances — in other words, it’s what any machine learning algorithm does when it produces a prediction for any unseen test instance on the basis of a finite number of training instances. Inductive bias describes the tendency for a system to prefer a certain set of generalizations over others that are equally consistent with the observed data.*
>  *Inductive bias is absolutely essential to machine learning (and human learning, for that matter). Without inductive bias, a learner can’t generalize from observed examples to new examples better than random guessing.*

**Examples**
![](ibias.png)


Good tasting papayas live within this rectangle. 
![](ben-david5.png)

That rectangle exists. Many such do. Each represents an *h*. Therefore, there's one that represents *f* also.
> 6. So if you're within the boundaries, then it's definitely tasty. But then doesn't that involve some amount of correlation vs causation? Also can't there be contradictory points outside that rectangle? 
> 7. Isn't rectangle a rather inconvenient shape? What if more than 2 features, how does this span into more dimensions?
> 8. *H* is a subset of all possible predictors that map *X*-->*Y*. Why not just set of all? (Therefore only some rectangles considered)

![](ben-david6.png)

Rather than minimising empirical loss over all possible predictors, it is trying to find a predictor in *h*, with a minimum empirical loss.
![](ben-david7.png)

> 9. What about *prior knowledge*? Is the way *H* is chosen making use of *prior knowledge?* How is subset *H* chosen?
> 10. Do we choose *H* such that *f* exists in *H*? Is that the criteria?


#### Theorem:
Let *X* be any set, $Y = {0,1}$, and let H be a finite set of functions from X to Y
Assume:
The training sample S is generated by some probability distribution D over X and labeled by some $f \in$ H and the elements of S are picked i.i.d 
Then, $ERM_H$ is guaranteed to come up with an h that has small true loss given sufficiently large sample S. 
 > Why should S be sufficiently large?

> Hypothesis testing in statistics is coming up with a theory without looking at the data. Here, we're arriving at the hypthothesis by looking at and learning from the data.


Proof:
![](ben-david8.png)
![](ben-david9.png)
D with square brackets is probability. $S|_{x}$ is S restricted to x, which means we're picking only x-es, not y-s. We need to prove that the probability of this event, of choosing an x from a bad sample, is small.
![](ben-david10.png)
Therefore, simply upperbound
(line 1: there exists a bad h; line 2: the bad h I selected. There could be sets in which there exists bad h but I *didn't* select. Therefore what I selected is a subset of M)
![](ben-david11.png)

> 11. What are the dimensions of M? Simply a set of all xi's?
> 12. Is there any overlap in Ss?
> 13. Has $D^m$ got anything to do with  M?
> 13.5. What does upperbounding probability got to do with union bound?

Using from probability,
1. Union bound
2. Prob of independent events

![](ben-david12.png)
![](ben-david13.png)
> 14. What is the relation between H and H_B?
![](ben-david14.png)

> 15. Why $(1 - \epsilon)^m$
	> (prob that h is wrong is at least epsilon. Therefore prob that h is right is 1-epsilon. For m tuples, raise to power m)

> 16. Independent events but do samples overlap?



![](ben-david15.png)
$= |H|e^(-\epsilon m)$ because $(1 - \epsilon)^m$ approaches 0 at an exponential rate (larger the m, the better. Therefore bigger the sample size, the better)
Completes proof!

But remember assumptions: 
	1. $ERM_h$ is finite
	2. Realisibility (f exists in h)
	
	
## Summarise this entire thing
Lecture 3 (00:00 to 00:27)

Why this works-
***Law of large numbers***

[[Learnability]]