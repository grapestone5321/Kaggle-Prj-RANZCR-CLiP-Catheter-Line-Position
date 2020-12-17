# Kaggle-RANZCR-CLiP-Catheter-Line-Position
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

## Submission File

For each ID in the test set, you must predict a probability for all target variables. The file should contain a header and have the following format:

StudyInstanceUID,ETT - Abnormal,ETT - Borderline,ETT - Normal,NGT - Abnormal,NGT - Borderline,NGT - Incompletely Imaged,NGT - Normal,CVC - Abnormal,CVC - Borderline,CVC - Normal,Swan Ganz Catheter Present


