---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
# Project: Enhanced Spam Detection Using Machine Learning

## Introduction/Background

In the 21st century, email remains a crucial communication tool, yet its utility is undermined by the inescapable challenge of spam. Our project embarks on leveraging machine learning to enhance spam detection, drawing upon the "Email Spam Detection Dataset (Classification)" from Kaggle. Similar endeavors in data-driven domains have emphasized the importance of applying analytical approaches for discerning patterns within vast datasets [1]. By applying cutting-edge machine learning techniques, this research aims to significantly improve the accuracy of spam detection [2], ensuring email remains a secure and efficient medium for digital communication [3]. 

Dataset Link: [Kaggle Email Spam Detection Dataset](https://www.kaggle.com/datasets/shantanudhakadd/email-spam-detection-dataset-classification)

## Problem Definition

### Problem 
With the increasing important of email in our daily lives for school and work, the amount of spam mail has also increased. Whether it be dangerous fishing emails or local stores trying to promote their business, people are often missing important emails in the flood of these promotions. We aim to filter out spam mail to make sure that as many important and relevant emails as possible are seen.

### Motivation 
There are several motivators to create an accurate email spam detector. Security enhancement to decrease the chances that someone can hack into personal or company data is one of many factors. Another factor is productivity improvment by spending less time looking through emails and determining if they are valuable or not.

...

## Results and Discussion
When classifying emails as spam or not spam, it is essential to reduce false positives to an absolute minimum. No one wants an email with a high-paying job offer getting sent to spam. With this priority in mind, we have selected several machine-learning metrics that will allow us to minimize false positives while also detecting as many true positives as possible.

### Precision 
Precision is the ratio of true positives to the total number of examples classified as positive in a test sample. Maximizing precision will prevent human-created emails from being misclassified as spam.

### F-beta 
While precision is vital, we also want to detect as many instances of spam as possible. The F-beta metric combines precision and recall together in a weighted average. A beta value less than 1 weights precision more strongly than recall, while a beta value greater than 1 does the opposite. By setting our beta to less than 1, say to 0.5, we can minimize false positives while rewarding true positives.

### Confusion matrix 
Alongside precision and F-beta, it will be useful to generate a full confusion matrix. The components of the confusion matrix already need to be calculated to calculate our other metrics, so it makes sense to use this metric as well. Seeing the raw numbers of true positives and false positives will be especially useful when evaluating our models.

For our project, there are several metric targets that we would like to achieve. Due to the strong negative impact of false positives in our problem domain, we are aiming for a precision greater than 0.99. This would require close to zero false positives in our confusion matrix. A good F-beta score is harder to define as it depends on the weighting used as well as the inherent difficulty of the problem. We will attempt to achieve an F-beta of 0.8 as this seems to be a decent rule-of-thumb value.


## References

[1] J. Goodman, G. Cormack, and D. Heckerman, "Spam and the Ongoing Battle for the Inbox," Communications of the ACM, vol. 50, no. 2, pp. 24-33, Feb. 2007.

[2] T. Almeida, J. Gómez Hidalgo, and A. Yamakami, "Towards SMS Spam Filtering: Results under a New Dataset," International Journal of Information Security Science, vol. 2, no. 1, pp. 1-18, 2013.

[3] S. Kiritchenko, S. Matwin, "Email Classification with Co-Training," in Proceedings of the 2006 Conference on Privacy, Security and Trust, Markham, Ontario, Canada, 2006, pp. 1-8.
