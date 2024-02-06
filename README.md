# Predicting mTOR Chemical Inhibitors - Drug Discovery

The main purpose of the project was to use the chembl databas, focusing on IC50 bioactivity, to ascertain whether a given molecule effectively inhibits the mTOR complex. Using the Chembl database, a list of compounds interacting with mTOR was curated and their stuctures were translated into chemical descriptors encompassing both Lipinski and Mordred descriptors. A machine learning pipeline was developed to predict the inhibitory effect of a certain compound on the mTOR complex. With LazyPredict, the most accurate machine learning model was obtrained and was futher optimized to provide a testabe framework for drug discovery. 


## Installing and Executing

Installing the packages

```
pip install -r requirements.txt
```

To execute the code, please go through each notebook from 1-5

## Results and Visualizations

Using the [ChEMBL database API](https://github.com/chembl/chembl_webresource_client), the IC50 of chemicals interacting (binding assay) with mTOR were collected and assigned a value based on whether the effect is active (high inhibition potential or low IC50), intermediary or inactive (low inhibition or high IC). 

![Image Alt text](/figs/ChEMBLTable.png)


Then, the structure of the chemicals were converted to [molecular descriptors](https://www.sciencedirect.com/topics/medicine-and-dentistry/molecular-descriptor) which are mathematical representations of molecules' properties, used to quantitatively describe the physical and chemical information of the molecules. For this purpose, [Lipinski descriptors](https://www.sciencedirect.com/topics/pharmacology-toxicology-and-pharmaceutical-science/lipinskis-rule-of-five) and [Mordred desrciptors](https://jcheminf.biomedcentral.com/articles/10.1186/s13321-018-0258-y) were obtain with custom calculations and the use of the rdkit and mordred libraries. The below plot shows the relationship between lipophilicity (logP) and the Molecular Weight (MV) of the active, intermediate and inactive compounds.

![Image Alt text](/figs/MVvsLogP.png)

Lastly, LazyPredictor was used to iteratively check which machine learning method would provide the best results in predicting the IC50 of a compound from the molecular descriptors. The AdaBoostRegression was on top of the list with a RMSE value of 0.55. Shown below is the extent of prediction accuracy of the test dataset, predictions of the compounds the model has not seen before.

![Image Alt text](/figs/PredictedvsExperimentalTest.png)

