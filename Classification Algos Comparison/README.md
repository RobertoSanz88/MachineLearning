# Classification Algorithms Comparison
In Python language with Jupiter Notebooks environment

**Algorithms used in Classification**   
1. [KNN](#id1)
2. [Decision Tree](#id2)
3. [Support Vector Machines](#id3)
4. [Logistic Regression](#id4)
5. [Random Forest](#id5)
6. [XGBoost](#id6)

**Datasets used .csv**
- Drug200
- Cell-samples
- telecust1000t
- ChurnData
- Handwritten digits MNIST dataset
  + 60.000 samples for training
  + 10.000 samples for test
  
**Results**
- Drugs
  + SVM is the best (97,5%) followed by Decision Tree and Random Forest
- Cancer cells
  + KNN is the best (100%) followed by the rest except for LR that lays below
- Telecom Customers
  + KNN is the best (43%) followed by Logistic Regression and SVM
- Telecom Churn
  + XGBoost is the best (87,5%) followed by the rest except for KNN that lays below
- MNIST Dataset
  + SVM is the best (97,92%) KNN the second best (97%)
  + It is not bad compared to what you can get with a Neural Network 
    - NN with 1 layer of 512 neurons -> 98,6%
    - A deep NN such as LeNet5: CNN 6 +Pooling +CNN 16 +Pooling +Dense 120 +Dense 84 -> 99,43%
    - Ref: https://medium.com/analytics-vidhya/dense-or-convolutional-part-1-c75c59c5b4ad
    
