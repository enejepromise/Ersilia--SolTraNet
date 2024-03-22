## eos6oli-Model-Validation
This is Ersilia's week 2 Task for Outreachy Summer 2024 contribution. This repository is a model validation for eos6oli.

## Model Abstract
Accurate prediction of aqueous solubility has been a challenge in drug recovery. 
This model will be used to solve the challenge of getting accurate prediction of aqueous solubility in drug recovery,
SolTraNet will be used, a molecule attention transformer to predict aqueous solubility from a molecule's SMILES representation.

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
1.  Choosing a model from the list of provided models from Ersilia Mdoel hub. I choose model eos6oli, understanding what the      model is all about and the appraoch the publication used.
2.  Creating all the files for the repository
3.  Downloading, fetching and serving the model Bias to ensure that it is working.
4.  I explored the dataset from CheMbl, and checked if the molecules had valid SMILES representation and up to the required       1000 molecules using rdkit library.
5.  Predictions were made
## Task 2

## SolTraNet Dependencies
. RDKit
. PyTorch
. Numpy
. Pathlib
## Reference 
Soltranet PDF Link: file:///C:/Users/user/Downloads/eos6oli.pdf
Soltanet gihub repo: https://github.com/gnina/SolTranNet


