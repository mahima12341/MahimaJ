<img width="612" alt="component1" src="https://github.com/ML4CEA/CEATestingModel/assets/62965045/97a9a691-fb77-465d-a55c-ae974ba6d99a">
<img width="612" alt="component2" src="https://github.com/ML4CEA/CEATestingModel/assets/62965045/1c151c67-651f-4632-a218-1bd481a85f03">

# Big component
**Name**: Userinterface\
**What it does**: This is the interface that interacts with the user (Clinician/ Physician) to get the input values of the features for the prediction model\
**Inputs**: Feature values\  
**Outputs**: Likelihood (prediction outcomes)

## Subcomponent 1
**Name**: AuthenticateInputValues\
**What it does**: Authenticate the feature input keyed in by the user and prompt the user to input the feature information in a certain format if incorrect\
**Inputs**: Feature values  
**Outputs**: Boolean and if output is false send an alert to the user to re-enter values
 
## Subcomponent 2:
**Name**: PredictionBlock\
**What it does**: Provides prediction for the given values by the user input using the lasso model from the training and validation step.\
**Inputs**: Feature values in the correct format  
**Output**: Predicted CEA test value obtained from the model.

# Big Component:
**Name**: Model training and validation\
**What it does**: Train lasso on the clean dataset and evaluate the performance of the model on the validation dataset to ascertain the features that best predict patient visits.\
**Inputs**: Electronic records data frame  
**Output**: Pickle object that contains the feature weights of the robust model 

## Subcomponent 1: 
**Name**: TrainModel\
**What it does**: Train Lasso on the train dataset\
**Inputs**: Training dataset that is a data frame consisting of individual patient records with patient and physician characteristics  
**Outputs**: Trained model with feature weights

## Subcomponent 2:
**Name**: Evaluation\
**What it does**: Evaluate the model on the validation set and evaluate it using AUC\
**Inputs**: Model features from the training module and validation data frame  
**Outputs**: AUC metric for lasso

# Big Component
**Name**: Data processing\ 
**What it does**: Cleaning the data frame in order to train and validate up to two different models\
**Inputs**: Raw data frame  
**Output**: Clean data frame

