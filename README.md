# Model-eos6oli: Soltrannet-Aqueous-Solubility-Model

## eos6oli-Model-Validation
This repository is a model validation for eos6oli.
This repository serves as a comprehensive collection of codes and datasets utilized for validating the eos6oli model. Given the vast number of compounds involved, conducting experimental solubility assessments for each compound would be impractical due to the associated time and cost constraints. This underscores the necessity for predictive models like eos6oli.

The primary objective of the eos6oli model is to predict the aqueous solubility of compounds, a crucial property in drug discovery endeavors. It accomplishes this by taking the SMILES representation of a molecule as input. The model architecture is based on the Molecule Attention Transformer (MAT) framework, a well-established approach documented in scientific literature.

One notable feature of the eos6oli model is its utilization of a self-attention mechanism applied to the molecular SMILES represented in a graph format. This mechanism enhances the model's ability to capture relevant features and dependencies within the molecular structure. Furthermore, the model optimizes prediction efficiency by bypassing the distance matrix calculation step, resulting in faster and more streamlined predictions without compromising accuracy.

## Model Information:
- Eos Model ID: eos6oli
- Slug: soltrannet-aqueous-solubility
- Task: regression
- Input: Compound(canonicalsmiles)
- Output: Experimental value
- Interpretation: Predicted LogS (log of the solubility)


## Repository Ogranization
* notebooks' contains colab notebooks
* data' contains all the datasets
* data/input' contains all inputs
* data/output' contains all outputs generated
* figues' contains all figues generated
* requirements.txt' contains all requirements
  
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
## WEEK 2 - Task 1 - Model Bias
Going through the list of provided models, I choose the eos6oli "SolTraNet" model.

## Step 2 - Github Repository
creating of repository in Github and creating all the necessary files used and results generated.

## Step 3 - Data Pre-Processing
- Selecting dataset of 1000 molecules from ChEMBL database and extract the SMILES.
- Load this dataset into the model bias python notebook.
- Convert the SMILES to standard SMILES using the function in src folder.
- Use the RDKIT package to get the Inchikey representation of the molecules.
- Export the file containing Inchikey and SMILES and save in a CSV file.
- Select a model and run predictions via google colab on [here](https://github.com/ersilia-os/ersilia/blob/master/notebooks/ersilia-on-colab.ipynb).
- Create a scatter plot of the predictions (probability) gotten from the step above to show the model bias.

## Steps to Reproduce The Solutions to These Tasks:

## Step 4 - Model Predictions
* Model Prediction and Analysis
The predictions were executed using the generated eos6oli model, matching the SMILES representations with the actual solubility      values.The analysis involved comparing actual solubility values with model-predicted solubility, visualizing the outcomes through scatter and residual plots for a comprehensive understanding. The predictions revealed that the majority of compounds exhibit solubility values concentrated around -5. Additionally, I utilized Morgan fingerprints generated from SMILES to create a scatterplot that represents solubility values with a threshold of 0.5. The color distribution on this plot signifies areas of varying prediction probabilities: regions in blue indicate prediction probabilities below 0.5, indicating low solubility, while areas in red represent high solubility with prediction probabilities equal to or greater than 0.5.

## Step 6 - Interpretation of Result
According to the information from the eos6oli publication, a soluble compound is defined as having a log S value greater than -4, which corresponds to the compound's ability to form a 100 μM solution. The publication also suggests that the model effectively screens out insoluble compounds.
Upon calculating the logarithm of solubility (base 10), the analysis revealed 998 compounds with Log S values of -10 and only 2 compounds with Log S values greater than -4. Subsequently, when checking if the compounds can form a 100 μM solution, it was found that only the 2 compounds with Log S values greater than -4 are capable of achieving this concentration. This underscores the model's efficacy in identifying soluble compounds as defined by the eos6oli publication and its usefulness in screening out insoluble compounds.

## Step 7 - Conclusion
From the generated predictions, it can be seen that the model is not biased based on the results obtained. The model effectively screened out 998 compounds with low solubility, having Log S values of -10 and an inability to achieve a 100 μM solution. Conversely, only 2 compounds exhibited Log S values greater than -4 and were capable of forming a 100 μM solution. This suggests that the model's predictions align with the criteria defined for soluble compounds in the eos6oli publication, demonstrating its effectiveness in differentiating between soluble and insoluble compounds.

## WEEK 2 - Task 2 - Model Reproducibility
## Step 1 - Installation of the Model

## Step 2 - Selecting Result to Reproduce
Reading through the publication to identify the result that I can reproduce

## Step 3 - Running Predictions with Soltrannet Model
From the publication, github repository which has the installation and usage instructions and data to use was provided.

## Reproductibility Figures
To ensure reproducibility, I cross-referenced the predictions generated by the Soltranet model with the actual solubility values from the Author's results. I then created histogram and bar plots specifically focusing on false discovery rates for compounds with LogS values less than or equal to -5 and -6, as defined in the publication. The outcome of this comparison yielded consistent results, indicating high reproducibility.
Furthermore, I expanded the analysis by utilizing more categorized datasets available on the Soltranet repository to calculate the false discovery rate of insoluble compounds, following the methodology outlined in the publication. Once again, the results matched those from the original study, further confirming the reproducibility of the Soltranet model in identifying insoluble compounds accurately.

## Step 5 - Reproducibility using the Ersilia Model Hub

## Week2_Task3 - External Validation
Step 1 - Sourcing for Dataset with Sufficient Experimental Result

## Step 2 - Cleaning and Standarizing SMILES

## Step 3 - Predictions and Calculating the Metrics
I used the eos6oli model to make predictions on the training dataset and saved the results. Next, I compared these predictions with the experimental values from an external dataset, saving the matches as a CSV file. To validate the model, I calculated the R2 score, which came out to be 0.88. This score indicates that the model successfully captured a substantial portion of the variation in experimental solubility.
# Step 4 - PCA of Morgan Fingerprint
The scatter plot generated from the Principal Component Analysis (PCA) of Morgan fingerprints represents the distribution and clustering of molecules in both the training and validation sets. The plot demonstrates how the molecules are grouped and separated based on their molecular features, as captured by the Morgan fingerprints.
From the scatter plot, it shows there are some overlap between the training and validation sets, indicating that certain molecular characteristics are shared between these sets. However, there are also distinct clusters, suggesting differences in the molecular properties of the molecules in each set.
In summary, the PCA analysis provides valuable insights into the relationships, similaritie and differences between molecules in the dataset, aiding in understanding how the model generalizes and performs across different sets of data.
































### Task 2(Model's Reproducibilty):

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


