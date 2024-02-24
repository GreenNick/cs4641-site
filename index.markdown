---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
# Project: Enhanced Spam Detection Using Machine Learning

## Introduction/Background

In the 21st century, email remains a crucial communication tool, yet its utility is undermined by the challenge of spam. Our project will leverage machine learning to enhance spam detection, drawing upon the “Email Spam Detection Dataset (Classification)” from Kaggle. Similar endeavors in data-driven domains have emphasized the importance of applying analytical approaches for discerning patterns within vast datasets [1]. By applying cutting-edge machine learning techniques, this research aims to significantly improve the accuracy of spam detection [2], ensuring email remains a secure and efficient medium for communication [3].

Dataset Link: Kaggle Email Spam Detection Dataset

## Problem Definition

### Problem
With the increasing importance of email in our daily lives for school and work, the amount of spam has also increased. Whether it be dangerous phishing emails or commercial promotions, people often miss important emails in this digital deluge. We aim to filter out spam to maximize relevant emails seen.

### Motivation
There are several motivators to create an accurate spam detector. Spam filters enhance security by removing a potential attack vector for hackers. Spam detection also improves productivity since people can spend less time determining if an email is valuable.

## Methods

### Data Preprocessing
There are several methods to encode text, which can then be inputted into our models. Text representation techniques include one-hot encoding, bag-of-words, N-grams, and others. We will start with the bag-of-words method, an intuitive method with extensive library support. We can use the CountVectorizer from sklearn for this. We will try N-gram encoding as well to compare results.

### Model selection
There are various ML algorithms and DL models such as CNN that detect spam well. We will focus on classical supervised ML algorithms for our project: Naive Bayes, Support Vector Machines, and Random Forest. GaussianNB is one example of the class from sklearn we can use for Naive Bayes.

## Results and Discussion
When detecting spam, it is essential to reduce false positives. No one wants an email with a job offer getting sent to spam. With this in mind, we have selected metrics that will allow us to minimize false positives while detecting as many true positives as possible.

### Metrics
#### Precision
Precision is the ratio of the TPs to the total TPs and FPs in a test sample. Maximizing precision will prevent real emails from being misclassified as spam. We aim to achieve a precision greater than 0.99.

#### F-beta
Precision is vital, but recall is important as well. The F-beta metric combines precision and recall together in a weighted average. By setting our beta to less than 1, we can prioritize minimizing FPs while still rewarding TPs. A good F-beta score is hard to define in advance, but we aim to achieve at least 0.8.

#### Confusion matrix
Confusion matrix components need to be calculated for our other metrics, so it makes sense to use this metric as well. The raw TP and FP numbers will help us evaluate our models. Our primary expectation from the confusion matrix is to have nearly 0 FPs.

## References

[1] J. Goodman, G. Cormack, and D. Heckerman, "Spam and the Ongoing Battle for the Inbox," Communications of the ACM, vol. 50, no. 2, pp. 24-33, Feb. 2007.

[2] T. Almeida, J. Gómez Hidalgo, and A. Yamakami, "Towards SMS Spam Filtering: Results under a New Dataset," International Journal of Information Security Science, vol. 2, no. 1, pp. 1-18, 2013.

[3] S. Kiritchenko, S. Matwin, "Email Classification with Co-Training," in Proceedings of the 2006 Conference on Privacy, Security and Trust, Markham, Ontario, Canada, 2006, pp. 1-8.

### Contributions
<table>
    <tr>
        <td>Name</td>
        <td>Proposal Contributions</td>
    </tr>
    <tr>
        <td>Sergei Novikov</td>
        <td>Methods and respective slides in presentation</td>
    <tr>
    <tr>
        <td>Nicholas Bowers</td>
        <td>Website setup, Results & Discussion and respective slides in presentation</td>
    <tr>
    <tr>
        <td>Carrington Kelsey</td>
        <td>Intro and References and respective slides in presentation</td>
    <tr>
    <tr>
        <td>Yash Desai</td>
        <td>Introduction and references section</td>
    <tr>
    <tr>
        <td>Nicholas Skiouris</td>
        <td>Results and dicussions section</td>
    <tr>
</table>

<img src="gantt.png" />
