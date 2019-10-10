## Statistic Learning

### 1. What is statistic learning

#### 1.1 Introduction

Let's get started with a simple case.  Suppose that you're a statistic consultant and hired by a client to provide suggestion on how to improve sales of a particular product. You have the `advertising` data consist of sales of three types of products: `TV`, `radio`, and `newspaper`. Generally, the client want to know whether there is an association between advertising and sales. So your goal is to develop an accurate model that can predict sales on the basis of existing data.



To be more mathematically , above can be written in a formula :

<center> <img src="/Users/caoweiwei/Library/Application Support/typora-user-images/image-20190929143023001.png" alt="image-20190929143023001" style="zoom:50%;" /></center>
In this setting, the advertising budgets are `input variables` while sales input is an `output variable`. The inputs `TV`, `Radio` and `Newspaper` go by different names,  such as `predictors`, `independent variables`, `features` or `variables`. The output variable is often called `reponse` or `dependent variable`. 



More generally, suppose that we observe a quantitative response ***Y*** and ***p*** diﬀerent predictors, ***X<sub>1</sub> , X<sub>2</sub> , . . . , X<sub>p</sub>***.The relationship can be marked in a very general form.

<img src="/Users/caoweiwei/Library/Application Support/typora-user-images/image-20190929144154939.png" alt="image-20190929144154939" style="zoom:50%;" />

Here 𝝐 is a random ***error term***, which is independent of ***X*** and has mean zero, and ***X = (X<sub>1</sub> , X<sub>2</sub> , . . . , X<sub>p</sub> )***. In essence, statistic learning refers to a set of approaches for estimating ***𝘧***. We know that the function ***𝘧***  that connects input and output is but it general unknown. So how to estimate ***𝘧*** based on the observed points is the key in statistic learning.

#### 1.2 Why estimate ***𝘧***

There are two main reasons that we may wish to estimate ***𝘧***: prediction and inference.

##### Prediction

In many situations, a set of inputs 𝙓 are readily available, but the output𝙔 cannot be easily obtained. ***We want to know what is the output 𝙔=𝘧(𝙓) from the a new given input 𝙓.*** We assume $\hat{𝙔}$ is the prediction of 𝙔 :

<img src="/Users/caoweiwei/Library/Application Support/typora-user-images/image-20190929145738912.png" alt="image-20190929145738912" style="zoom:50%;" />

The accuracy of $\hat{𝙔}$  depends on two quantities: the reducible error $\hat{𝘧}$, which we can use techniques for improving the estimate of ***𝘧***; and the second is error term 𝝐, called irreducible error, beacuse it cannot be predicting by using 𝙓. Statistics learning focus on techniques for estimating ***𝘧*** with the aim of minimizing the reducible error. 

##### Inference

We are often insterested in ***how 𝙔 changes as a function of X<sub>1</sub> , X<sub>2</sub> , . . . , X<sub>p</sub>.*** The following questions may be attracted our attention:

- Which features are associated with the response?
- What is the relationship between the response and each feature?
- Can the relationship between 𝙔 and each predictor be adequately summarized using a linear equation, or is the relationship more complicated?

#### 1.3 How Do We Estimate ***𝘧***

Our goal is to apply a statistical learning method to the `training data` in order to estimate the unknown function ***𝘧***. In other words, we want to ﬁnd a function ***$\hat{𝘧}$*** such that ***Y ≈ $\hat{𝘧}$(X)*** for any observation ***(X, Y )***. Broadly speaking, most of statistics learning methods for this task can be characterized as either `parametric` or `non-parametric` .

##### Parametric Methods

Parametric methods involve a two-step model-based approach.

1. Make an assumption about the form of ***𝘧***. For example, one very simple assumption is that ***𝘧*** is linear in ***X***: <img src="/Users/caoweiwei/Library/Application Support/typora-user-images/image-20190929151742197.png" alt="image-20190929151742197" style="zoom:50%;" />
2. Use the training data to ﬁt or train the model. In the case of the linear model, we need to estimate the parameters ***β<sub>0</sub> , β<sub>1</sub> , . . . , β<sub>p</sub>*** .

The advantages of this method is that it reduces the problem of estimating ***𝘧*** down to one of ***estimating a set of parameters***, which is generally much easier to estimate.

The potential disadvantage of a parametric approach is that the model we choose will usually ***not match the true unknown form of 𝘧.*** To address this problem, we can choose ***flexible model*** that requires estimating a greater number of parameters which can lead to a phenomenon known as ***overfitting***.

##### Non-parametric methods

Non-parametric methods ***seek an estimate of 𝘧*** that gets as close to the data points as possible without being too rough or wiggly. Such approaches can have a major advantage that has ***the potential to accurately ﬁt a wider range of possible shapes for 𝘧.*** But non-parametric approaches do suﬀer from a major disadvantage: ***a very large number of observations*** is required in order to obtain an accurate estimate of  ***𝘧***.

#### 1.4 The Trade-Oﬀ Between Prediction Accuracy and Model Interpretability

There are lost of types of approaches for application, but why would we ever choose to use a more restrictive method instead of a very ﬂexible approach? **That's depends on our goal: prediction or inference**. 

- Prediction Accuracy V.S. Interpretability. In general, as the ﬂexibility of a method increases, its interpretability decreases.
- Good Ft V.S Over-ﬁt or Under-ﬁt. A important question is how do we know when the ﬁt is just right?
- Parsimony V.S Black-box. Sometimes, we prefer a simpler model involving fewer variables but with greatest explanatory power.

#### 1.5 Supervised Versus Unsupervised Learning

Most statistical learning problems fall into one of two categories: ***supervised*** or ***unsupervised***. 

- Supervised. For each observation of the predictor 𝒙<sub>i</sub>, there is  an associated response 𝒚<sub>i</sub>. We wish to ﬁt a model that relates the response to the predictors, with the aim of accurately predicting the response for future observations (prediction) or better understanding the relationship between the response and the predictors (inference).
- Unsupervised. We observe a vector of measurements 𝒙<sub>i</sub> ,but no associated response 𝒚<sub>i</sub> . We seek to understand the relationships between the variables or between the observations.
- Semi-supervised. In a training data set, we have some predictor measurements and a response measurement, and the left data only have predictor measurements but no response measurement.

#### 1.6 Regression Versus Classiﬁcation Problems

Variables can be characterized as either ***quantitative*** or ***qualitative*** (also known as ***categorical***).

- Quantitative variables take on numerical values, and the model refers to quantitative problems named ***regression problems***.
- Qualitative variables take on values in one of *K* diﬀerent classes, or categories, while those involving a qualitative response are often referred to as ***classiﬁcation problems***.

### 2. Assessing Model Accuracy 

It is an important task to decide for any given set of data which method produces the best results. 

#### 2.1 Measuring the Quality of Fit

Suppose we ﬁt a model *$\hat{f}$(x)* to some training data Tr = {(𝒙<sub>i</sub>, 𝒚<sub>i</sub>)}<sub>1</sub><sup>n</sup>, we wish to see how well the model $\hat{f}$ performs. We could compute the ***mean square error(MSE)*** over Tr:

<img src="/Users/caoweiwei/Library/Application Support/typora-user-images/image-20190930123350049.png" alt="image-20190930123350049" style="zoom:50%;" />

The MSE will be ***small*** if the predicted responses are very ***close*** to the true responses.

#### 2.2 The Bias-Variance Trade-Oﬀ

The ***expected test MSE***, for a given value 𝒙<sub>0</sub> , can be decomposed into the sum of three fundamental quantities: the ***variance*** of $\hat{f}$(𝒙<sub>0</sub>), the squared ***bias*** of $\hat{f}$(𝒙<sub>0</sub>) and the variance of the error terms 𝝐: 

<img src="/Users/caoweiwei/Library/Application Support/typora-user-images/image-20190930124410704.png" alt="image-20190930124410704" style="zoom:50%;" />

From this equation, to minimize the expected test error we need to simultaneously achieve ***low variance*** and ***low bias***. As a general rule, as we use more ﬂexible methods, the variance will increase and the bias will decrease.

#### 2.3 The Classiﬁcation Setting

Suppose that we seek to estimate 𝘧 on the basis of training observations {(𝒙<sub>1</sub> , 𝒚<sub>1</sub> ), . . . , (𝒙<sub>𝒏</sub> , 𝒚<sub>𝒏</sub> )}, where now 𝒚<sub>1</sub> , . . . , 𝒚<sub>𝒏</sub> are qualitative. The most common approach for quantifying the accuracy of our estimate $\hat{f}$  is the ***training error rate***:

<img src="/Users/caoweiwei/Library/Application Support/typora-user-images/image-20190930125227251.png" alt="image-20190930125227251" style="zoom:50%;" />

A good classiﬁer is one for which ***the test error is smallest***. Here are some examples: The Bayes Classiﬁer and K-Nearest Neighbors.