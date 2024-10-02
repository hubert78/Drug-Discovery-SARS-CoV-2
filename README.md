### Project Overview
This computational drug discovery project focuses on drug repositioning, specifically identifying existing chemical compounds that can be repurposed to treat diseases. My target molecule in this case is the Replicase polyprotein 1ab of the SARS-CoV-2 virus, a key viral protein responsible for its replication. The primary objective of this project is to leverage machine learning and deep learning techniques to predict and generate new chemical compounds with potent activity, using IC50 values as a benchmark for drug efficacy.
### Dataset
I utilized the ChEMBL database to download chemical compounds known to target the Replicase polyprotein 1ab. The dataset includes molecular properties, IC50 values (which represent the concentration of a compound needed to inhibit a biological process by 50%), and other molecular descriptors essential for drug efficacy analysis.
### Project Structure
This project is organized into three Jupyter notebooks:
#### 1. Exploratory and Statistical Analysis
In the first notebook, I perform exploratory data analysis (EDA) and compute important molecular properties of the chemical compounds. A key focus is on evaluating the Lipinski Rule of 5, which assesses drug-likeness by setting thresholds for:
* Molecular weight (< 500 Da)
* LogP (measure of hydrophobicity, < 5)
* Hydrogen bond donors (< 5)
* Hydrogen bond acceptors (< 10)
These rules help predict if a compound has properties that make it a likely oral drug candidate.
#### 2. Model Selection for IC50 Prediction
The second notebook computes PaDEL molecular fingerprints of the compounds. This is a set of molecular descriptors used to encode the chemical properties of compounds. Then in order to predict the IC50, I applied Lazypredict, an automated machine learning library, to evaluate multiple regression models for predicting the IC50 of the compounds. After testing several models, RandomForestRegressor emerged as the top performer, and I fine-tuned the hyperparameters to optimize its accuracy, achieving a Mean Squared Error (MSE) of 0.71.  Given that -log10(IC50) ranged from a minimum of 3.37 to 10.89, with a mean of 5.99, this suggested that an MSE of 0.71 was pretty good, and that the model was making relatively small errors on average in its predictions. This model was then used to predict the IC50 of new compounds generated later in the project.
#### 3. Generative Adversarial Neural Network (GANN) for New Compound Generation
The third notebook focuses on building a Generative Adversarial Neural Network (GANN) to generate novel molecular structures targeting the Replicase polyprotein 1ab. After generating new compounds, I used the previously trained RandomForestRegressor to predict their IC50 values. Encouragingly, the GANN-generated compounds exhibited IC50 values that are as low as 831M, which is comparable to some of the best known drug candidates against SARS-CoV-2
### Key Accomplishments
* Performed detailed exploratory analysis, adhering to the Lipinski Rule of 5 for drug-likeness.
* Identified RandomForestRegressor as the most effective model for IC50 prediction.
* Successfully generated novel molecular compounds with GANN, achieving IC50 values comparable to top SARS-CoV-2 drug candidates.

