##Multi-class Classification
========================================

***Implemented one-vs-all logistic regression to recognize hand-written digits.***

This is programming assignment in Machine Learning course by Andrew Ng.  
The course info can be found here https://www.coursera.org/learn/machine-learning/home/info.  
The details of this assignment is described in ex3.pdf.  

The codes are written by Octave.  
For further info of Octave please see http://www.gnu.org/software/octave/

Automated handwritten digit recognition is widely used today - from recognizing zip codes (postal codes)
on mail envelopes to recognizing amounts written on bank checks.

There are 5000 training examples in ex3data1.mat, where each training
example is a 20 pixel by 20 pixel grayscale image of the digit. Each pixel is
represented by a floating point number indicating the grayscale intensity at
that location. The 20 by 20 grid of pixels is "unrolled" into a 400-dimensional
vector. Each of these training examples becomes a single row in the data
matrix X. This gives a 5000 by 400 matrix X where every row is a training
example for a handwritten digit image.

The second part of the training set is a 5000-dimensional vector y that
contains labels for the training set.To make things more compatible with
Octave/MATLAB indexing, where there is no zero index, so mapped
the digit zero to the value ten. Therefore, a "0" digit is labeled as "10", while
the digits "1" to "9" are labeled as "1" to "9" in their natural order.

![1](https://cloud.githubusercontent.com/assets/15040734/21624471/31db885a-d22d-11e6-8439-5c6fd5c79125.png)

I used a multiple one-vs-all logistic regression models to build a
multi-class classifier. Since there are 10 classes,I needed to train 10
separate logistic regression classifiers. To make this training effecient, it was ensured
that the code is well vectorized. In this section,I implemented a vectorized version of 
logistic regression that does not employ any for loops.

**Regularized Cost Function:**

![2](https://cloud.githubusercontent.com/assets/15040734/21624476/365c0fee-d22d-11e6-8bc0-ad4f310659be.png)

***NOTE: Theta_0 is not be regularized which is used for the bias term.***

**The Partial derivative of regularized logistic regression cost for Theta_j is defined as:**

![3](https://cloud.githubusercontent.com/assets/15040734/21624479/394f1480-d22d-11e6-8900-457f77e51a8e.png)


I implemented one-vs-all classification by
training multiple regularized logistic regression classifiers, one for each of
the K classes in the dataset. In the handwritten digits dataset,
K = 10, but my code works for any value of K.


After training the one-vs-all classifier,I then used it to predict the
digit contained in a given image. For each input, I computed the
"probability" that it belongs to each class using the trained logistic regression
classifiers. The one-vs-all prediction function picks the class for which the
corresponding logistic regression classifier outputs the highest probability and
return the class label (1, 2,..., or K) as the prediction for the input example.

## the training set accuracy is about 94.9% (i.e., it classifies 94.9% of the examples in the training set correctly).

This set include the following functions:

ex3.m - Octave/MATLAB script that steps you through part 1

ex3data1.mat - Training set of hand-written digits

submit.m - Submission script that sends your solutions to our servers

displayData.m - Function to help visualize the dataset

fmincg.m - Function minimization routine (similar to fminunc)

sigmoid.m - Sigmoid function

[?] lrCostFunction.m - Logistic regression cost function

[?] oneVsAll.m - Train a one-vs-all multi-class classifier

[?] predictOneVsAll.m - Predict using a one-vs-all multi-class classifier

? indicates files completed by me

