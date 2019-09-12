---
title: "Titanic : Machine Learning from Disaster Kaggle"
date: 2019-09-12
tags: [deep learning , machine learning]
header:
    image: "/images/ab.jpg"
excerpt: "Predict whether the passenger will survive titanic disaster or not"
---

Problem Definition: From a given training set of samples listing passengers who
survived or did not survive the Titanic disaster, How accurately we can predict the survival rate of the samples in test set ? 
Acquire Data: As the data is given on Kaggle Website , I just downloaded the data .
Different types of features (Categorical, Numerical) were present in the data .
Types of Features
Categorical
Numerical
Mixed
Nominal Survived
Sex
Ordinal Pclass Continuous Age Fair
Discrete SibSp Parch
Ticket Cabin Names
Embarked
Exploratory Data Analysis:

These were some early insights after initial analysis.
Total passengers were 891 and greater than 75% did not traveled with parents or
children. About 30% had siblings and/or spouse abroad. Less than 1 % were paying as high
as $512. And less than 1 percent were within age range 65-80.Cabin , Age , Embarked
features contained null values. Ticket feature had high ratio (22%) of duplicate values
(unique=681)

After doing analysis by visualization , I observed following things .
I observed most passengers in Pclass = 1 survived and Pclass = 3 did not survived.
significant correlation (>0.5) among Pclass=1 and Survived . females had very high survival
rate at 74% with Exception in Embarked=C where males had higher survival rate. Infants and
old passengers had high survival rate and Large number of people 15-25 year olds did not
survive. Higher fare paying passengers had better survival and Port of embarkation correlates
with survival rates
Wrangling:
After collecting several assumptions and decisions regarding our datasets and solution
requirements, I did some cleaning and wrangling .

As ticket feature was providing no information , so I dropped it.
Null values were filled with their median and mode values respective features.
Feature engineering :
Feature engineering plays a vital role in improving our results . I made several features but
found that some of them were useful .
Feature Description
has_cabin True: if cabin value is avaliable
Fam_size Family size feature was created by adding
Parch and SibSp
Title Title was extracted from names
Is _Alone 0 : When Fam_size =1
Age*Class Multiply Age and Pclass
Fare_Per_Person Fare/Fam_size+1
Sex_target_enc Mean encoding of Sex
E_freq Frequency encoding of Embarked
Non-Numerical Values were converted to numerical values as many libraries could only deal
with numerical values. In the end feature looked like this.
Model used and Results :
I used following algorithms t o get results .
Logistic Regression Extra Tree
Random forest Xgboost
Decision Tree Adaboost
Decison Tree was underfitting the data while Xgboost and Adaboost was overfiting. The best
accuracy of 0.803 was achieved using Extra Tree. This model placed me among top 11
percent on the leader board. Verify
