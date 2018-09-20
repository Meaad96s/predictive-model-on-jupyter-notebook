# Predict Voice Disorders and Build Bayes Network Model using Jupyter Notebook

Flow


1. Create an IBM Watson Studio Workspace.
2. Create a Jupyter notebook workplace from the Watson Studio asset.
3. Create a Cloud Object storage to store the data.
4. Jupyter notebook depends on an Apache Spark service.
5. Import data to start building the model


## Prerequisite:
1. Create an IBM Cloud account.
2. Create an instance of Watson Studio from the catalog.

# Steps:
**Login to IBM Cloud and Create Watson Studio Service**
1. Register in [IBM Cloud](https://ibm.biz/BdYmuL).
2. Go to **Catalog**.
3. Search for `watson studio`.
4. Click on the service and then **Create**.
5. On the service page, click on **Get Started**.

**Create a project in IBM Watson platform.**
1. Scrol down the page and click on **(+) New project icon**.
2. Name your project 'Predict loan eligibility'.
3. Click **Create**.
4. In your project page, nagivate to the Assests tab, drag the [samples dataset](https://github.com/Meaad96s/predictive-model-on-jupyter-notebook/blob/master/n_samples.csv) and [targets dataset](https://github.com/Meaad96s/predictive-model-on-jupyter-notebook/blob/master/n_features.csv) files and drop it in the Load sidebar


<p align="center"><img  src="https://user-images.githubusercontent.com/20974667/45819331-b9c80f80-bcec-11e8-8c9b-81389c55cc4c.png">
  

**Create a Notebook Jupyter from the assets tab.**

Language: Python 3.5 with spark
Spark version: Spark 2.3

<p align="center"><img  src="https://user-images.githubusercontent.com/20974667/45819333-b9c80f80-bcec-11e8-9ac5-1f961abde16d.png">

**Press the pen icon to edit the notebook**

<p align="center"><img  src="https://user-images.githubusercontent.com/20974667/45819335-b9c80f80-bcec-11e8-9690-2cc059dc699f.png">

###

**From the left bar, insert the code to import the samples data from data asset**
<p align="center"><img  src="https://user-images.githubusercontent.com/20974667/45819336-b9c80f80-bcec-11e8-9562-a12240dbe17a.png">
  
and change the shape of the dataframe to 
`X=np.reshape(df_data, (226, 12))` 

Then do it again in another Cell to inser the code of importing the targets dataset.
The matrix of the targets dataset is 1D so it must be changed to
`y=np.ravel(df_target)`

**Cross Validation**
you can take the snippet below

>from sklearn.cross_validation import train_test_split
import itertools
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.metrics import confusion_matrix
X_train, X_test, y_train, y_test = train_test_split(df_data, df_target, test_size=0.33, random_state=42)
y_train=np.ravel(y_train)
from sklearn.model_selection import KFold # import KFold
kf = KFold(n_splits=10) # Define the split - into 2 folds 
kf.get_n_splits(X) # returns the number of splitting iterations in the cross-validator

#### So, Now there is each dataset is split to train and test groups.

## References
Watson Studio: Master the art of data science with IBM’s Watson Studio.

## License
GNU General Public License v3.0
