---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

title: Enhanced Spam Detection Using Machine Learning
layout: page
sidebar:
  nav: section-nav
---
## Introduction/Background

In the 21st century, email remains a crucial communication tool, yet its utility is undermined by the challenge of spam. Our project will leverage machine learning to enhance spam detection, drawing upon the “Email Spam Detection Dataset (Classification)” from Kaggle. Similar endeavors in data-driven domains have emphasized the importance of applying analytical approaches for discerning patterns within vast datasets [1]. By applying cutting-edge machine learning techniques, this research aims to significantly improve the accuracy of spam detection [2], ensuring email remains a secure and efficient medium for communication [3].

Dataset Link: Kaggle Email Spam Detection Dataset [4]

## Problem Definition

### Problem
With the increasing importance of email in our daily lives for school and work, the amount of spam has also increased. Whether it be dangerous phishing emails or commercial promotions, people often miss important emails in this digital deluge. We aim to filter out spam to maximize relevant emails seen.

### Motivation
There are several motivators to create an accurate spam detector. Spam filters enhance security by removing a potential attack vector for hackers. Spam detection also improves productivity since people can spend less time determining if an email is valuable.

## Methods

### Data Preprocessing
For data preprocessing, we used the Bag of Words algorithm to quantify the data encoded in the emails. We encoded 'ham' as 0, and 'spam' as 1. We tweaked some of the parameters like removing 'Stop words' and varying the vocabularly size in different models. We decided not to proceed with N-grams or TF-IDF encodings because firstly they wouldn't give any significant improvement in accuracies based on our research and NLP is slighly out of scope of this class. We prioritized experimenting with various classical ML algirthms and CNN networks using Pytorch and Tensorflow.

### Model selection
For the midterm portion of the project, we used Naive Bayes to analyze the email data. This algorithm classified our information as either "ham" (a real email) or "spam." We chose this algorithm for our email spam detection project because of its proven efficiency and effectiveness in handling large datasets, its ability to work well with text data through the application of conditional probability, and its fast computation time, making it an ideal solution for accurately classifying emails as spam or ham.

For the final portion of the project we trained and tested the dataset on additional 3 models: Random Forests, custom CNN and Resnet18 models. We chose Random Forests model because it is a more powerful model than Naive Bayes and is generally a good choice for classification tasks as well as because we covered Random Forests in depth in class and we curous how it would perform on the spam/ham dataset. We then decided to experiment with Deep Learning models , particularly CNNs. We chose CNNs over fully connected counterparts because the former have better sample complexity and perform better on smaller dataset (we considered out dataset with roughly 5000 entries a small one ). The custom CNN model is naive CNN implementation with just 1 convolutional layer and Resnet18 is larger multi-layer CNN model. We chose these models also to see how the size will affect the model convergence on our dataset (under-fitting if too small or overfitting if the model is too large) and which of the 2 CNN models will perform better. 



## Results and Discussion

### Mitdterm report part
Overall, the Naive Bayes model did a good job of classifying the data we input. More specifically, it does a great job of identifying the hams in the dataset with high accuracy. On the other hand, it is only able to correctly classify the spam about half of the time (see the confusion matrix in `main.ipynb` and precision score below). We will try to fix this problem with different models in the final project, but we believe this problem could also be due to the lack of "spam" data in the dataset. If the latter is true, we could look into finding a new dataset for the project.


### Final Report part
We used 80/20 train/test split for the model training and testing for all of the models. We also specified specified a random seed to ensure the dataset is split the same way into training and testing sets to ensure better and consistent comparison across different models. For preprocessing methods we generally experimented a little by removing 'stop words' and capping the dimensionality (or vocab size). The former reduced the model perfomance during Naive Bayes testing and we decided not to proceed using it and the later didn't have significant effects on the models perfomance overall. <br>
All models training, testing and vizualizations can be also viewed in the project folder in 4 respective jupyter notebooks. 

### Random Forests results
After struggling with improving precision with Naive Bayes we decided to proceed with Random Forests and the results exceededed expectations. We initialized a RandomForestClassifier model with default settings from sklearn.ensemble library and trained the model. During the evalation the model reached a precision of 100% and accuracy of 97.94%. So there were no false positives during testing - all the ham messages were classfied correctly as spam. The sensitivity (or recall) reduced from 94.%2 to 84.14% comparing to Naive Bayes. Yet, since the drop in recall was much smaller than increase in precision the overall f1-score significantly improved from 68.42% to 91.39%.

### Custom CNN model
After experiencing notable success with simpler models, we ventured into more advanced neural network architectures by implementing a Convolutional Neural Network (CNN) using the Keras framework for this project. We designed the CNN architecture to specifically address the challenges of our dataset, initializing it with convolutional and pooling layers to enhance feature extraction. The model was compiled with the Adam optimizer, leveraging its adaptive learning rate capabilities, and we utilized categorical cross-entropy as the loss function to cater to our multi-class classification task. During training, we observed a steady increase in model performance metrics: the precision achieved was 98.54%, with an accuracy of 98.92%, and an F1-score of 95.74%. These metrics indicate a well-balanced model with a strong capability to generalize, as evidenced by minimal overfitting of the validation data. We fine-tuned the model further by adjusting the number of filters and kernel size, which resulted in an optimized balance between recall and precision, ensuring robust performance across various classes.

### Resnet18 results
After getting great results with a simple custom CNN model we wondered if a more complex multi-layer CNN model will give better results. We also decided to use Pytorch instread of Tensorflow for model training and evaluation to compare those 2 most popular DL frameworks. We chose  Resnet18 based on professor Roozbahani's recommendation. Running ahead we trained the model on both pretrained and non-pretrained weights and it didn't give any difference. We slightly adjusted the Resnet18 default input and output layer to account for the dimensionality of custom dataset. We also converted capped dataset dimensionality to nearest square number and reshape from 1D to 2D to be compatible with 2D convolutional filters in Resnet18. We chose binary cross entropy for the loss function and experimented with both stochastic gradient descent and Adam optimizers during training which didn't yield significant differences (SGD was a bit more stable though and gave more consistent training vs validation loss charts), but Adam was little faster during training. Since the model was much larger than the custom CNN model, it took significantly longer time to train with approximately a little over one minute for each epoch using cpu. We trained on 10 epochs same as for custom CNN model and batch size of 64. We used learning rate of 0.001 during trainig and tried to optimize it but it didn't yield significant improvements. After a bit of experimentaiton we got similar, but slightly worse results across all metrics comparing to those of a custom CNN model. We concluded that due to relatively small size of our dataset a larger model doesn't provide any advantage and on the contrary might underfit the model which could explain slighly worse results. 

### Conclusion
Despite ongoing progress in Machine Learning and Deep Learning technologies research and improvement of spam detection remains a relevenat topic. Not only researches create more sophisticated models but also the spammers find and target vulnerabilities of those new models. Furthermore, a bottleneck in spam detection research is lack of publicly available high quality spam/ham data. Most researchers use the same (or similar pre-processed versions) of relatively small (~5500 entires) publicly aviable dataset [4]. While lack of spam data slows down the overall progress in the area, it allowed us to compare our results to those published relevant papers.

Almeida et all in their work "Towards SMS Spam Filtering: Results under a New Dataset" did an extensive testing of various algorithms (predominantly classical machine learning algorithms without DL) on the same dataset as we did [2]. They achieved best accuracies with Logistic regression and SVM models (97.64 and 97.59 respectively), which we intend to experiment with in future. They have achieved higher accuracy than us of 91.95% vs 89.24% using Naive Bayes model. However, we achieved a higher accuracy of 97.94% vs 95.36%  using Random Forests. It is important to note that they used a special tokenizer for Naive Bayes, something that we didn't do. However, our higher accuracy for Random Forests could be explained by a different train/test split of dataset. We did 80/20 split while Almeida et all did a 30/70 split, a significantly smaller amount of training data. 

### Metrics
#### Confusion matrix
Confusion matrix components need to be calculated for our other metrics, so it makes sense to use this metric as well. The raw TP and FP numbers will help us evaluate our models. Our primary expectation from the confusion matrix is to have nearly 0 FPs.
#### Accuracy
Accuarcy is most intiutive metrics when it comes to evaluating the classfication model. It is essentially number of correct predictions over total number of predicitons or (TP + TN) / (TP + TN + FP + FN). Based on related papers and results for similar problmes we aim to achieve accuracy of at least 95%.
#### Precision
Precision is the ratio of the TPs to the total TPs and FPs in a test sample. Maximizing precision will prevent real emails from being misclassified as spam. We aim to achieve a precision greater than 0.99.

#### Sensitivity (Recall)
Sensitivity (or recall) is the ratio of the TPs to the total TPs and FNs in a test sample. Maximizing sensitivity will prevent spam emails being misclassified as real emails. We aim to achieve sensitivity of at least 95%.

#### F-1 score
Precision is vital, but recall is important as well. The F-1 score metric combines precision and recall together and is a widely used metric in classification tasks. A good F-1 score is hard to define in advance, but we aim to achieve at least 0.8.

#### Results table
<table>
  <tr>
    <th></th>
    <th>Accuracy</th>
    <th>F-1 score</th>
    <th>Precision</th>
    <th>Sensitivity</th>
  </tr>
  <tr>
    <th>Naive Bayes</th>
    <td>0.8924</td>
    <td>0.6842</td>
    <td>0.5372</td>
    <td>0.942</td>
  </tr>
  <tr>
    <th>Random Forests</th>
    <td>0.9794</td>
    <td>0.9139</td>
    <td>1.0</td>
    <td>0.8414</td>
  </tr>
  <tr>
    <th>Resnet18</th>
    <td>0.9816</td>
    <td>0.9259</td>
    <td>0.9398</td>
    <td>0.9124</td>
  </tr>
  <tr>
    <th>CNN</th>
    <td>0.9892</td>
    <td>0.9574</td>
    <td>0.9854</td>
    <td>0.9310</td>
  </tr>
</table>

### Visualizations
#### Dataset Composition
<img src="assets/comp.png" />

#### Random Forest
<img style="width: 80%;" src="assets/rf_conf.png" />

#### Naive Bayes
<img style="width: 80%;" src="assets/nb_conf.png" />

#### ResNet18
<img style="width: 48%;" src="assets/rn_loss.png" />
<img style="width: 48%;" src="assets/rn_acc.png" />
<img style="width: 80%;" src="assets/rn_conf.png" />

#### CNN
<img style="width: 48%;" src="assets/cnn_loss.png" />
<img style="width: 48%;" src="assets/cnn_acc.png" />
<img style="width: 80%;" src="assets/cnn_conf.png" />

### Next steps
Things to try next to improve model: <br>
1) Train and test the dataset on SVM model <br>
2) Train and test the dataset on Logistic regression model <br>
3) For deeplearning use learning rate auto-optimization technique that seem to avaiable online. <br>
4) Experiment with 'Lion' optimizer that relatively recently came out: https://github.com/lucidrains/lion-pytorch <br>
5) Experiment with ensemble deep learning to combine predictions of several different models. <br>
6) Integrate the model to an email app to see how it will perform in real world settings. <br>


## References

[1] J. Goodman, G. Cormack, and D. Heckerman, "Spam and the Ongoing Battle for the Inbox," Communications of the ACM, vol. 50, no. 2, pp. 24-33, Feb. 2007.

[2] T. Almeida, J. Gómez Hidalgo, and A. Yamakami, "Towards SMS Spam Filtering: Results under a New Dataset," International Journal of Information Security Science, vol. 2, no. 1, pp. 1-18, 2013.

[3] S. Kiritchenko, S. Matwin, "Email Classification with Co-Training," in Proceedings of the 2006 Conference on Privacy, Security and Trust, Markham, Ontario, Canada, 2006, pp. 1-8.

[4] Email Spam Detection Dataset (classification), https://www.kaggle.com/datasets/shantanudhakadd/email-spam-detection-dataset-classification/data

## Contributions
<table>
    <tr>
        <td>Name</td>
        <td>Final Contributions</td>
    </tr>
    <tr>
        <td>Sergei Novikov</td>
        <td>Resnet18 & RandomForests implementation</td>
    <tr>
    <tr>
        <td>Nicholas Bowers</td>
        <td>Fixed website setup, preprocessing</td>
    <tr>
    <tr>
        <td>Carrington Kelsey</td>
        <td>CNN model, slides, project README</td>
    <tr>
    <tr>
        <td>Yash Desai</td>
        <td>Introduction and references section</td>
    <tr>
    <tr>
        <td>Nicholas Skiouris</td>
        <td>Introduction and references section</td>
    <tr>
</table>

<img src="gantt.png" />
