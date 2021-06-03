# Predicting-Alzheimers-Disease-Risk

## Motivation 
Alzheimer's disease is an irreversible, degenerative brain disorder that steadily damages memory and thinking skills and, finally, the ability to carry out the simplest tasks. According to the Alzheimer's Association, more than 6 million Americans of all ages have Alzheimer’s. An estimated 6.2 million Americans age 65 and older are living with Alzheimer’s dementia in 2021, and 72% of whom are 75 or older. In addition, 1 in 9 people over the age of 65 has Alzheimer’s dementia. In most patients with the disease—those with the late-onset type—symptoms first develop in their mid-60s. Due to the irresistibility of the disease, it is imperative to explore approaches that can predict Alzheimer’s disease risk in order for preventive measures to take place. With the rise in popularity and power of machine learning, it is necessary to explore ways to apply machine learning in predicting Alzheimer’s disease risk.

## Dataset
In this project, I am using the datasets from the GWAS catalog (https://www.ebi.ac.uk/gwas/). More precisely, I am using two datasets from the catalog that are most relevant to the purpose of the project- Alzheimer’s disease (EFO_0000249) and late-onset Alzheimers disease (EFO_1001870). The datasets contain useful information regarding many variants and risk alleles. In the dataset, I will only use the name of the variant and risk allele, the risk allele frequency (how frequently the allele appears in a population), and beta (the resulting coefficient from a fit).

## Data Preparation
To have a dataset that can be used for training the models, I used the EFO_1001870 dataset from the GWAS catalog to simulate a dataset of 10,000 individuals with SNP data as the features and an associate Alzheimer’s disease risk label (low risk, medium risk, and high risk). I used EFO_1001870 to conduct a separate GWAS, identified relevant SNPs linked to Alzheimer’s disease, and scattered them across a ‘population’ based on minor allele frequencies. In order to produce a realistically simulated dataset, I introduce the concept of bias by giving different individuals higher probabilities of having certain SNPs. In addition, the bias allows the individuals to be classified into 1 of 3 classes: low risk, medium risk, and high risk. I made 50% of the population low risk, 35% of the population medium risk, and 15% of the population high risk. This split gives the simulated population a realistic polygenic risk score distribution. Moreover, the 3 classes are decently separable. To complete the dataset, I removed the polygenic risk score and intersected the features (variants and risk alleles) of the current dataset with those of EFO_0000249. The resulting dataset contains 10,000 individuals and 122 features denoting 122 variants and risk alleles, 1 label denoting low, medium or high risk. 

## Choosing models
This problem is now reduced to a multi-class classification problem. Because the dataset is relatively small, I experimented with logistic regression, gaussian naive bayes, support vector machine, K-nearest neighbor, decision tree, multi-layer perceptron, random forest, and XGBoost- a total of 8 different algorithms. 

## Training 
The dataset is split into a training set and a test set (80/20 split). I used grid search and hyperopt to tune the hyperparameters to improve the performance of the models. 

## Results
I used precision, recall, f1, and AUC as the metrics to evaluate the performance of the models. Precision is the ratio of correctly predicted positive observations to the total predicted positive observations. Recall is the ratio of correctly predicted positive observations to the all observations in actual class. F1 is the weighted average of Precision and Recall. AUC is the measure of the ability of a classifier to distinguish between classes. Logisic regression was the best performing model, with an f1 score of 0.89.

Discussion
This project shows a promising future for machine learning’s ability to predict Alzheimer’s disease risk. An extension of this project will be to work with organizations, such as 23andMe, with real human data, and perform training using real data. With the model, for instance, 23andMe can warn users whose DNA show potential risk to Alzheimer’s disease according to the prediction of the machine learning model. 

