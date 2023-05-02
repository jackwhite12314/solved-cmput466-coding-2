Download Link: https://assignmentchef.com/product/solved-cmput466-coding-2
<br>
<strong>Problem 1</strong>

Download: <a href="https://drive.google.com/file/d/1_tul2tTn1MpHGfOb29DeJFQXm76s70Ln/view?usp=sharing">Codebase</a>

In this problem, you are asked to apply linear regression and logistics regression for binary classification. In particular, this problem shows that linear regression is a bad model for classification problems.

We consider a binary classification problem, where the input is a two-dimensional vector and the output is

{0,1}. In other words, . Specifically, we would train our classifiers on the following two datasets:

<strong>Dataset A:</strong>

In this dataset, positive samples are generated by a bivariate normal distribution , where . Negative samples are generated by another , where

. The covariance is the same as the positive samples.

We have 400 samples in total, where 200 are positive and 200 are negative. The dataset is plotted in the left panel below.

<strong>Dataset B: </strong>We now construct a new dataset by shifting <strong>half </strong>of the positive (blue) samples to the <strong>upper right </strong>as shown in the right panel. In other words, the positive samples are generated by

with equal probability, where <a href="https://www.codecogs.com/eqnedit.php?latex=%5Cmu_1%5E%7B%5Cprime%3D(3.2%2C%203.2)%20#0">.</a>

Dataset A                                                                          Dataset B

<strong>Questions:</strong>

For each of Dataset A or Dataset B:

<ul>

 <li>Train a classifier by thresholding a linear regression model. In other words, treat the target 0/1 labels as real numbers, and classify a sample as positive if the predicted value is greater than or equal to 0.5.</li>

 <li>Train a logistic regression classifier on the same data.</li>

</ul>

<strong>Submission </strong>(four numbers and four plots)<strong>:</strong>

Report the following four numbers

<ol>

 <li>Training accuracy of <strong>linear </strong>regression on <strong>Dataset A</strong></li>

 <li>Training accuracy of <strong>logistic </strong>regression on <strong>Dataset A </strong> Training accuracy of <strong>linear </strong>regression on <strong>Dataset B</strong></li>

 <li>Training accuracy of <strong>logistic </strong>regression on <strong>Dataset B</strong></li>

</ol>

and plot four decision boundaries. Please make clear which classifier is applied in the plot.

<strong>Problem 2 </strong>

Download: <a href="https://drive.google.com/file/d/18yjr1Tm5bgSShvoM8CjbDW-sTpi7pYTn/view?usp=sharing">Codebase</a>

In this coding problem, we will implement the softmax regression for multi-class classification using the <a href="http://yann.lecun.com/exdb/mnist/">MNIST </a><a href="http://yann.lecun.com/exdb/mnist/">dataset</a>.

<h1>Dataset</h1>

First, download the datasets from the link above. You need to unzip the .gz file by either double clicking or some command like gunzip -k file.gz

The dataset contains 60K training samples, and 10K test samples. Again, we split 10K from the training samples for validation. In other words, we have 50K training samples, 10K validation samples, and 10K test samples. The target label is among {0, 1, …, 9}.

<h1>Algorithm</h1>

We will implement stochastic gradient descent (SGD) for cross-entroy loss of softmax as the learning algorithm. The measure of success will be the accuracy (i.e., the fraction of correct predictions).

<table>

 <tbody>

  <tr>

   <td width="50"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

The general framework for this coding assignment is the same as SGD for linear regression, so you may re-use most of the code. However, you shall change the computation of output, the loss function, the measure of success, and the gradient whenever needed.

<h1>Implementation trick</h1>

For softmax classification, you may encounter numerical overflow if you just follow the equation mentioned in the lecture.

The observation is that the exp function increases very fast with its input, and very soon exp(z) will give NAN (not a number).

The trick is to subtract every  by the maximum value .

In other words, we compute

, where , and then we have

Note that the gradient is computed with y, and since subtracting a constant before softmax doesn’t affect y, it doesn’t affect the gradient either.

<h1>[40 marks]</h1>

<strong>Without changing the the default hyperparameters</strong>, we report three numbers:

<ol>

 <li>The number of epoch that yields the best validation performance, 2. The validation performance (accuracy) in that epoch, and</li>

 <li>The test performance (accuracy) in that epoch.</li>

</ol>

and two plots:

<ol>

 <li>The learning curve of the training cross-entropy loss, and</li>

 <li>The learning curve of the validation accuracy.</li>

</ol>

<h1>[10 marks]</h1>

Ask one meaningful scientific question yourself, design your experimental protocol, present results, and draw a conclusion.

<strong>Note:</strong>

A <em>scientific question </em>means that we can give a verifiable hypothesis that can be either confirmed or declined.

<u>Example of a scientific question: </u>Is the learned classifier for this dataset better than majority guess?

Your hypothesis could be either yes or no, and it can be verified by experiments.

<u>Example of a non-scientific question: </u>Does the learned classifier become better if I have super-power? My hypothesis could be either yes or no, but cannot be verified by any experiment. I don’t know what superpower is, and I can say yes, or I can also say no. Neither is wrong, nor even correct.

A <em>meaningful </em>scientific question means that you’ll learn something from the experiment. Of course, what is meaningful itself is subjective. In terms of this coding assignment, the scientific question is considered meaningful as long as the student would learn something, or verify some results we mentioned in lectures. <u>Example of a meaningful scientific question: </u>How does linear regression perform for classification for this dataset? Doing this experiment will give us first-hand experience on why we shall not use regression models to do classification. But you <strong>cannot </strong>ask this question as the solution. You need to ask your own scientific question that interests you and/or inspires others.

<u>Example of a not-so-meaningful scientific question:  Is the learned classifier for this dataset better than </u>majority guess? Ok, this question is considered scientific, but too trivial for us, although it is not necessarily trivial for those who don’t know machine learning at all. [Again this shows the subjectivity of evaluating the significance of science.]