PIU-body-image-disordered-eating-mediation

R code for mediational g-formula analyses of problematic internet use, body dissatisfaction, disordered eating, and adolescent mental health in the Tokyo Teen Cohort.

Overview

This repository contains R code associated with the study:

Narita et al., “Body Dissatisfaction and Disordered Eating as Pathways Linking Problematic Internet Use to Depressive Symptoms and Suicidal Ideation in Adolescents.”

The code implements the parametric mediational g-formula to estimate total effects (TE), natural direct effects (NDE), natural indirect effects (NIE), and proportions mediated (PM). The models account for exposure-mediator and mediator-mediator interactions.

The available analysis code covers depressive symptoms (SMFQ) in the overall sample and in sex-stratified analyses (girls and boys), comparing medium versus low and high versus low problematic internet use (PIU). Other mental health outcomes and sensitivity analyses are not included in the current repository.

File organization

The repository contains the following files:

mediation for natural effects: R code for parametric mediational g-formula analyses and bootstrap confidence intervals for the overall sample, girls, and boys.

demo data: R script generating synthetic data and performing multiple imputation for demonstration purposes.

README.md: Project documentation and instructions.

LICENSE: MIT License.

The imputed_data.RData file is generated locally and is not included in the repository.

System requirements

The manuscript analyses were conducted using R version 4.5.2.

Required R packages include mice, boot, and randomForest.

To install the required packages, run:

install.packages(c("mice", "boot", "randomForest"))

No specialized hardware is required. Installation time and operating system compatibility have not been systematically evaluated.

Demo instructions

A demonstration using entirely synthetic data is provided. No actual Tokyo Teen Cohort participant data are included.

First, download or clone this repository and set the working directory to the repository's root directory.

Generate synthetic data and perform multiple imputation by running:

source("demo data")

This generates 800 synthetic observations and three imputed datasets, saved locally as imputed_data.RData.

Next, run the mediation analysis:

source("mediation for natural effects")

The analysis uses 200 bootstrap samples per imputed dataset. With three imputed datasets, this yields 600 bootstrap estimates per exposure comparison when all model fits succeed.

The resulting estimates are illustrative and do not reproduce the numerical findings reported in the manuscript.

Instructions for use with real data

The Tokyo Teen Cohort participant data are not publicly available because of ethical restrictions and data-use agreements.

Researchers with authorized access must prepare an analytical dataset containing the required variables and perform multiple imputation. The resulting mice object should be named df_miced and saved in a file named imputed_data.RData in the repository's root directory.

To run the analysis, execute:

source("mediation for natural effects")

The analysis uses 200 bootstrap samples per imputed dataset. With 20 imputed datasets, this yields 4,000 bootstrap estimates per exposure comparison when all model fits succeed.

The number of imputed datasets is determined by the input data.

Statistical output

The script reports total effects (TE), natural direct effects (NDE), natural indirect effects (NIE), and proportions mediated (PM) for the overall sample, girls, and boys.

For each population, medium versus low and high versus low PIU are examined.

Bootstrap percentile 95% confidence intervals are calculated for TE, NDE, and NIE.

The proportion mediated is calculated as the natural indirect effect divided by the total effect (PM = NIE / TE).

PM is reported as a point estimate only. No confidence interval is calculated or reported for PM.

The causal interpretation of NDE and NIE depends on the identification assumptions described in the manuscript.

Reproducibility

The synthetic demonstration allows researchers and reviewers to examine the analytical workflow and test the code without access to confidential participant data.

Because the original cohort data are restricted, the demonstration cannot reproduce the numerical estimates reported in the manuscript.

The manuscript analysis uses 20 imputed datasets and 200 bootstrap samples per dataset. The synthetic demonstration uses three imputed datasets and 200 bootstrap samples per dataset.

Data availability

Individual participant data from the Tokyo Teen Cohort are not included in this repository because they contain sensitive information and are subject to ethical and institutional restrictions.

Access to research data is governed by the Tokyo Teen Cohort's applicable data-sharing procedures and approvals.

License

This code is distributed under the MIT License. See the LICENSE file for details.

Contact

For questions regarding this repository, please contact:

Zui C. Narita

Email: zuinarita@ncnp.go.jp

GitHub: https://github.com/ZuiCNarita
