## eos6oli-Model-Validation
This is Ersilia's week 2 Task for Outreachy Summer 2024 contribution. This repository is a model validation for eos6oli.
This repository serves as a comprehensive collection of codes and datasets utilized for validating the eos6oli model. Given the vast number of compounds involved, conducting experimental solubility assessments for each compound would be impractical due to the associated time and cost constraints. This underscores the necessity for predictive models like eos6oli.

The primary objective of the eos6oli model is to predict the aqueous solubility of compounds, a crucial property in drug discovery endeavors. It accomplishes this by taking the SMILES representation of a molecule as input. The model architecture is based on the Molecule Attention Transformer (MAT) framework, a well-established approach documented in scientific literature.

One notable feature of the eos6oli model is its utilization of a self-attention mechanism applied to the molecular SMILES represented in a graph format. This mechanism enhances the model's ability to capture relevant features and dependencies within the molecular structure. Furthermore, the model optimizes prediction efficiency by bypassing the distance matrix calculation step, resulting in faster and more streamlined predictions without compromising accuracy.


## Model Characteristics
.  Input: Compound
.  Input shape: Single
.  Task: Regression
.  Output: Experimental value
.  Output shape: Single (Predicted log of solubility of the compound)

## Repository Ogranization
.  '/notebooks' contains all colab notebooks used
.  '/data' contains all the datasets
.  '/data/input' contains all inputs
.  '/data/output' contains all outputs generated
.  '/figues' contains all figues generated
.  '/requirements.txt' contains all requirements
## Task 1

## Task 1
### 1
Going through the models provided, choosing the eos6oli.
### 2
creating all the files for the repository
### 3
Download, fetch and served the model in [Model_Bias1](/notebooks/Model_Bias1.ipynb) . To ensure it was working smoothly, I ran predictions for this sample [dataset](/data/input/eml_canonical.csv). I saved the predictions [result](/data/output/eos6oli_output.csv).
### 4
I downloaded molecules used from Harvard Dataverse because I needed a dataset that has actual or experimentally determined solubility values to compare my predictions with.On Harvard Dataverse, I searched for Aqsoldb a manually curated reference dataset of compounds with their acqous solubility values.I downloaded the [dataset](/data/input/curated-solubility-dataset.csv).
#### Exploring the dataset
I explored the dataset, ensured the molecules had valid SMILES representation using rdkit library, and saved random 1000 entries into a csv [file](/data/input/1000molecules.csv) to be used.
### 5
I ran predictions with the model, generated an [output](/data/output/1000predictions.csv) and I tried to match it with the actual solubility values using the SMILES [here](/data/output/predictions.csv). The model predicts the solubility. I made a scatter and residual plots of the actual solubility vs the predicted solubility [plots](/figures/1000molecules) of the predictions. With the scatter plot forming a diagonal line and the residual plot being centred around 0 and the mean absolute error at 0.82, it suggests that the model is not bias.

## Task 2

## SolTraNet Dependencies
. RDKit
. PyTorch
. Numpy
. Pathlib
## Reference 
Soltranet PDF Link: file:///C:/Users/user/Downloads/eos6oli.pdf
Soltanet gihub repo: https://github.com/gnina/SolTranNet


