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
## Public Best LB Score: 0.968
## Private Score: 0.970

-------

## ResNet200D/inference Single Model LB 96.5
https://www.kaggle.com/ammarali32/resnet200d-inference-single-model-lb-96-5




### y_preds = (y_preds1.sigmoid().to('cpu').numpy() + y_preds2.sigmoid().to('cpu').numpy()) / 2
            
      y_preds = 0.6*y_preds1.sigmoid().to('cpu').numpy() + 0.4*y_preds2    LB 0.965   ver3
      y_preds = 0.5*y_preds1.sigmoid().to('cpu').numpy() + 0.5*y_preds2    LB 0.965   ver2      #default
      y_preds = 0.4*y_preds1.sigmoid().to('cpu').numpy() + 0.6*y_preds2    LB 0.965   ver4
      y_preds = 0.2*y_preds1.sigmoid().to('cpu').numpy() + 0.8*y_preds2    LB 0.965   ver5

### BATCH_SIZE = 128  #default

      BATCH_SIZE = 128    LB 0.965   ver2   #default
      BATCH_SIZE = 64     LB 0.965   ver6
      
          
-------

## Ensemble of 2 best public notebooks
https://www.kaggle.com/raghaw/ensemble-of-2-best-public-notebooks


### predictions = (2 * predictions200d + predictions152d) / 3.0

      predictions = 0.9 * predictions200d + 0.1 * predictions152d      LB 0.966   ver6
      predictions = 0.8 * predictions200d + 0.2 * predictions152d      LB 0.966   ver5      --- Best 167 -> 164
      predictions = 0.7 * predictions200d + 0.3 * predictions152d      LB 0.966   ver4               209 -> 167
      predictions = (2 * predictions200d + predictions152d) / 3.0      LB 0.966   ver1      #default
      predictions = 0.6 * predictions200d + 0.4 * predictions152d      LB 0.966   ver2
      predictions = 0.5 * predictions200d + 0.5 * predictions152d      LB 0.966   ver3


### BATCH_SIZE = 128

predictions = 0.8 * predictions200d + 0.2 * predictions152d:

      BATCH_SIZE = 64    LB         ver8
      BATCH_SIZE = 128   LB 0.966   ver5      #default

-------


## Few best public notebook and dataset ensemble
https://www.kaggle.com/kiranchaudharyy/few-best-public-notebook-and-dataset-ensemble


      pred= (pred200d + pred200d_2 + 0.50 *pred152d)/2.5:    LB 0.967   ver1
      
      pred= 0.4*pred200d + 0.4*pred200d_2 + 0.2*pred152d:      LB 0.967   ver2
      pred= 0.5*pred200d + 0.4*pred200d_2 + 0.1*pred152d:      LB 0.967   ver3            207 -> 156
      pred= 0.55*pred200d + 0.4*pred200d_2 + 0.05*pred152d:    LB 0.967   ver4  --- Best  164 -> 163
      pred= 0.60*pred200d + 0.4*pred200d_2 + 0.00*pred152d:    LB 0.967   ver6            162 -> 162
      pred= 0.50*pred200d + 0.45*pred200d_2 + 0.05*pred152d:   LB 0.967   ver7            162 -> 166
      pred= 0.60*pred200d + 0.35*pred200d_2 + 0.05*pred152d:   LB 0.967   ver8            173 -> 174
      pred= 0.65*pred200d + 0.30*pred200d_2 + 0.05*pred152d:   LB 0.967   ver9           
      
   
### predictions200d_2 = inference(models200D_2, test_loader_512, device)

pred= 0.55*pred200d + 0.4*pred200d_2 + 0.05*pred152d:

      pred200d_2 = inference(models200D_2, test_loader_512, device)    LB 0.967   ver4  --- (Best)  164 -> 163
      pred200d_2 = inference(models200D_2, test_loader_640, device)    LB 0.968   ver10
      
      
      ### predictions200d = inference(models200D, test_loader_640, device)
      ### #predictions200d = inference(models200D, test_loader_512, device)
      
      ### #predictions200d_2 = inference(models200D_2, test_loader_512, device)
      ### predictions200d_2 = inference(models200D_2, test_loader_640, device)
      
      ### #predictions152d = inference(models152D, test_loader_640, device)
      ### predictions152d = inference(models152D, test_loader_512, device)


### predictions200d = inference(models200D, test_loader_640, device)
### predictions200d_2 = inference(models200D_2, test_loader_640, device)
### predictions152d = inference(models152D, test_loader_640, device)  

      pred= 0.45*pred200d + 0.5*pred200d_2 + 0.05*pred152d:     LB 0.968   ver19



### predictions200d = inference(models200D, test_loader_640, device)
### predictions200d_2 = inference(models200D_2, test_loader_640, device)
### predictions152d = inference(models152D, test_loader_512, device)          

      pred= 0.55*pred200d + 0.4*pred200d_2 + 0.05*pred152d:     LB 0.968   ver12
      pred= 0.5*pred200d + 0.45*pred200d_2 + 0.05*pred152d:     LB 0.968   ver15
      pred= 0.45*pred200d + 0.5*pred200d_2 + 0.05*pred152d:     LB 0.968   ver14  --- (Best)  138 -> 133
      pred= 0.4*pred200d + 0.55*pred200d_2 + 0.05*pred152d:     LB 0.968   ver16
          
      pred = 0.45*pred200d + 0.45*pred200d_2 + 0.1*pred152d      LB 0.968   ver17
      pred = 0.5*pred200d + 0.5*pred200d_2 + 0.0*pred152d        LB 0.968   ver18

      pred = 0.44*pred200d + 0.51*pred200d_2 + 0.05*pred152d     LB 0.968   ver26
      pred = 0.46*pred200d + 0.49*pred200d_2 + 0.05*pred152d     LB 0.968   ver25

### BATCH_SIZE = 128

pred= 0.45*pred200d + 0.5*pred200d_2 + 0.05*pred152d:

      BATCH_SIZE = 8     LB 0.968        ver24
      BATCH_SIZE = 16    LB 0.968        ver22
      BATCH_SIZE = 32    LB 0.968        ver21
      BATCH_SIZE = 128   LB 0.968        ver14  --- (Best)
      BATCH_SIZE = 256   LB error        ver23
      BATCH_SIZE = 512   LB error        ver20


y_preds2 = model(images.flip(-1))

      y_preds2 = model(images.flip(-1))   LB 0.968       ver14
      y_preds2 = model(images.flip(1))    LB 0.959       ver27
      y_preds2 = model(images.flip(0))    LB 0.925       ver29
                


### y_preds = (y_preds1.sigmoid().to('cpu').numpy() + y_preds2.sigmoid().to('cpu').numpy()) / 2

      y_preds=0.5*y_preds1.sigmoid().to('cpu').numpy() + 0.5*y_preds2.sigmoid().to('cpu').numpy()
      
      y_preds=0.2*y_preds1.sigmoid().to('cpu').numpy() + 0.8*y_preds2.sigmoid().to('cpu').numpy()   LB 968       ver28
      y_preds=0.7*y_preds1.sigmoid().to('cpu').numpy() + 0.3*y_preds2.sigmoid().to('cpu').numpy()   LB 968       ver30 ---Best
      y_preds=0.9*y_preds1.sigmoid().to('cpu').numpy() + 0.1*y_preds2.sigmoid().to('cpu').numpy()   LB 968       ver31 
      
-------






