# Kaggle-Prj-RANZCR-CLiP-Catheter-Line-Position
Kaggle-RANZCR-CLiP-Catheter-Line-Position


## End Date (Final Submission Deadline): 
Mar 15th, 2021 11:59 PM UTC

## Goal
In this competition, you’ll detect the presence and position of catheters and lines on chest x-rays. 

Use machine learning to train and test your model on 40,000 images to categorize a tube that is poorly placed.

The dataset has been labelled with a set of definitions to ensure consistency with labelling. 

The normal category includes lines that were appropriately positioned and did not require repositioning. 

The borderline category includes lines that would ideally require some repositioning but would in most cases still function adequately in their current position. 

The abnormal category included lines that required immediate repositioning.

-------

## Evaluation

Submissions are evaluated on area under the ROC curve between the predicted probability and the observed target.

To calculate the final score, AUC is calculated for each of the 11 labels, then averaged. 

The score is then the average of the individual AUCs of each predicted column.


### Receiver operating characteristic: ROC
https://en.wikipedia.org/wiki/Receiver_operating_characteristic



-------

## Submission File

For each ID in the test set, you must predict a probability for all target variables. The file should contain a header and have the following format:

StudyInstanceUID,ETT - Abnormal,ETT - Borderline,ETT - Normal,NGT - Abnormal,NGT - Borderline,NGT - Incompletely Imaged,NGT - Normal,CVC - Abnormal,CVC - Borderline,CVC - Normal,Swan Ganz Catheter Present


## Columns
- StudyInstanceUID - unique ID for each image

- ETT - Abnormal - endotracheal tube placement abnormal

- ETT - Borderline - endotracheal tube placement borderline abnormal

- ETT - Normal - endotracheal tube placement normal

- NGT - Abnormal - nasogastric tube placement abnormal

- NGT - Borderline - nasogastric tube placement borderline abnormal

- NGT - Incompletely Imaged - nasogastric tube placement inconclusive due to imaging

- NGT - Normal - nasogastric tube placement borderline normal

- CVC - Abnormal - central venous catheter placement abnormal

- CVC - Borderline - central venous catheter placement borderline abnormal

- CVC - Normal - central venous catheter placement normal

- Swan Ganz Catheter Present

- PatientID - unique ID for each patient in the dataset

-------

# Paper-1

## ChestX-ray8: Hospital-scale Chest X-ray Database and Benchmarks on Weakly-Supervised Classification and Localization of Common Thorax Diseases
https://arxiv.org/pdf/1705.02315.pdf

-------

# Paper-2


## Bag of Tricks for Image Classification with Convolutional Neural Networks
https://arxiv.org/pdf/1812.01187.pdf


## Deep Residual Learning for Image Recognition
https://arxiv.org/pdf/1512.03385.pdf

## Caffe: Convolutional Architecture for Fast Feature Embedding
https://arxiv.org/pdf/1408.5093.pdf

-------

# Progress
## Public Best LB Score: 0.965
## Private Score: 

-------

## ResNet200D/inference Single Model LB 96.5
https://www.kaggle.com/ammarali32/resnet200d-inference-single-model-lb-96-5




### y_preds = (y_preds1.sigmoid().to('cpu').numpy() + y_preds2.sigmoid().to('cpu').numpy()) / 2
            
      y_preds = 0.6*y_preds1.sigmoid().to('cpu').numpy() + 0.4*y_preds2    LB 0.965   ver3
      y_preds = 0.5*y_preds1.sigmoid().to('cpu').numpy() + 0.5*y_preds2    LB 0.965   ver2
      y_preds = 0.4*y_preds1.sigmoid().to('cpu').numpy() + 0.6*y_preds2    LB 0.965   ver4
      y_preds = 0.2*y_preds1.sigmoid().to('cpu').numpy() + 0.8*y_preds2    LB 0.965   ver5



-------



