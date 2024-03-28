## eos6oli-Model-Validation

This repository is a model validation for eos6oli.
This repository serves as a comprehensive collection of codes and datasets utilized for validating the eos6oli model. Given the vast number of compounds involved, conducting experimental solubility assessments for each compound would be impractical due to the associated time and cost constraints. This underscores the necessity for predictive models like eos6oli.

The primary objective of the eos6oli model is to predict the aqueous solubility of compounds, a crucial property in drug discovery endeavors. It accomplishes this by taking the SMILES representation of a molecule as input. The model architecture is based on the Molecule Attention Transformer (MAT) framework, a well-established approach documented in scientific literature.

One notable feature of the eos6oli model is its utilization of a self-attention mechanism applied to the molecular SMILES represented in a graph format. This mechanism enhances the model's ability to capture relevant features and dependencies within the molecular structure. Furthermore, the model optimizes prediction efficiency by bypassing the distance matrix calculation step, resulting in faster and more streamlined predictions without compromising accuracy.


## Model Characteristics
* Input: Compound
* Input shape:
* SingleTask: Regression
* Output: Experimental value
* Output shape: Single (Predicted log of solubility of the compound)

## Repository Ogranization
* '/notebooks' contains colab notebooks
* '/data' contains all the datasets
* '/data/input' contains all inputs
* '/data/output' contains all outputs generated
* '/figues' contains all figues generated
* '/requirements.txt' contains all requirements
  
## Task Process 
![image](https://github.com/enejepromise/Ersilia--SolTraNet)

## Ersilia environment setup

Ubuntu 20.04 with Python 3.7

1. Install miniconda3
2. Install GitHub CLI
3. Install and activate Git LFS from Conda using:
	- `conda install git-lfs -c conda-forge`
	- `git-lfs install`
4. Install Ersilia using:
	- `conda create -n ersilia python=3.7`
	- `conda activate ersilia`
	- `python -m pip install isaura==0.1`
	- `git clone https://github.com/ersilia-os/ersilia.git`
	- `cd ersilia`
	- `pip install -e .`
5. Test the selected model to be sure it works.
	- `ersilia -v fetch model_name`
	- `ersilia serve model_name`
	- `ersilia -v api run -i "CCCC"`

## Steps

- Select dataset of 1000 molecules from ChEMBL database and extract the SMILES.
- Load this dataset into the model bias python notebook.
- Convert the SMILES to standard SMILES using the function in src folder.
- Use the RDKIT package to get the Inchikey representation of the molecules.
- Export the file containing Inchikey and SMILES and save in a CSV file.
- Select a model and run predictions via google colab on [here](https://github.com/ersilia-os/ersilia/blob/master/notebooks/ersilia-on-colab.ipynb).
- Create a scatter plot of the predictions (probability) gotten from the step above to show the model bias.



## Task 1
* After reviewing the available models, I choose to work with eos6oli model.
* Subsequently, all necessary files were created and organized within the repository.
* The eos6oli model was downloaded, fetched, and then served from the selected model.
* Additionally, the molecules required for training and testing the model were downloaded.
* Dataset Exploration
  An in-depth exploration of the dataset was conducted to ensure the validity of the molecules' SMILES representation, leveraging the     rdkit library.
* A random selection of 1000 entries from the dataset was saved into a CSV file for further analysis.
* Model Prediction and Analysis
  The predictions were executed using the generated eos6oli model, matching the SMILES representations with the actual solubility         values.
  Analysis was conducted by comparing the actual solubility values against the model-predicted solubility, visualizing the results        through scatter and residual plots for comprehensive insights.

## Task 2
After thoroughly reviewing the publication, I identified a result that I could replicate using the SC2 dataset mentioned in the study.

Following the guidelines provided in the publication's GitHub repository, I installed all necessary dependencies, including the Python package for the model. I utilized the SC2 dataset available in the GitHub repository referenced in the publication.

Using the rdkit library, I validated the SMILES representations in the SC2 dataset to ensure accuracy. To validate reproducibility, I analyzed and recreated the predictions generated by the Soltranet model, aligning them with the actual solubility values. This analysis was further supported by creating a histogram, mirroring the methodology described in the publication.

In Model Reproducibility, I utilized the SC2 dataset to make predictions using the Ersilia model. I saved the output and then proceeded to compare these results with the dataset. I replicated a histogram and sensitivity analysis based on these results. Interestingly, the outcomes from both the Ersilia model and the author's model were identical.

## SolTraNet Dependencies
* RDKit
* PyTorch
* Numpy
* Pathlib

## Reference 
* [Soltranet](https://github.com/gnina/SolTranNet)
* [Soltranet Datasets and Figures Generations Repository](https://github.com/francoep/SolTranNet_paper)
* [Ersilia Google Colab Guide](https://github.com/ersilia-os/ersilia/blob/master/notebooks/ersilia-on-colab.ipynb)


