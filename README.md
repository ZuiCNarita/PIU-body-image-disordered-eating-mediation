# PIU-body-image-disordered-eating-mediation
R code for mediational g-formula analyses of problematic internet use, body dissatisfaction, disordered eating, and adolescent mental health in the Tokyo Teen Cohort.

PIU-body-image-disordered-eating-mediation

R code for mediational g-formula analyses of problematic internet use, body dissatisfaction, disordered eating, and adolescent mental health in the Tokyo Teen Cohort.

Overview

This repository contains R code associated with the study:

Narita et al., “Body Dissatisfaction and Disordered Eating as Pathways Linking Problematic Internet Use to Depressive Symptoms and Suicidal Ideation in Adolescents.”

The code implements the parametric mediational g-formula to estimate total effects (TE), natural direct effects (NDE), natural indirect effects (NIE), and proportions mediated (PM). The models account for exposure-mediator and mediator-mediator interactions.

The currently available code covers the overall-sample analysis of depressive symptoms, comparing medium versus low and high versus low problematic internet use (PIU). Sex-stratified analyses, other mental health outcomes, and sensitivity analyses are not yet included.

File organization

The recommended file structure is as follows:

run_analysis.R: Main R script for mediation analysis and bootstrap confidence intervals.

demo/make_demo_imputed_data.R: Script for generating synthetic data and performing multiple imputation.

README.md: Documentation and instructions.

LICENSE: MIT License.

.gitignore: Specifies files excluded from version control.

The imputed_data.RData file is generated locally and is not included in this repository.

System requirements

Software:

R version 4.5.2 was used for the manuscript analyses.

Required R packages include mice, boot, and randomForest.

To install these packages, run:

install.packages(c("mice", "boot", "randomForest"))

No specialized hardware is required. Installation times and compatibility across operating systems have not been systematically evaluated.

Demo instructions

A demonstration using entirely synthetic data is provided. No actual Tokyo Teen Cohort participant data are included.

First, download or clone the repository and set the working directory to the repository's root directory.

Generate synthetic data and perform multiple imputation by running:

source("demo/make_demo_imputed_data.R")

The demonstration generates 800 synthetic observations and three imputed datasets, which are saved locally in imputed_data.RData.

Next, run the mediation analysis in demo mode:

Sys.setenv(RUN_MODE = "demo")

source("run_analysis.R")

Demo mode uses 50 bootstrap samples per imputed dataset, producing 150 bootstrap estimates for each exposure comparison when all model fits succeed.

The resulting estimates are illustrative and do not reproduce the numerical findings reported in the manuscript.

Instructions for use with real data

The Tokyo Teen Cohort participant data are not publicly available because of ethical restrictions and data-use agreements.

Researchers with authorized access must prepare an analytical dataset containing the required variables and perform multiple imputation. The resulting mice object should be named df_miced and saved in a file named imputed_data.RData in the repository's root directory.

To run the full analysis, execute:

Sys.setenv(RUN_MODE = "full")

source("run_analysis.R")

Full mode uses 200 bootstrap samples per imputed dataset. With 20 imputed datasets, this produces 4,000 bootstrap estimates per exposure comparison when all model fits succeed.

The number of imputed datasets is determined by the input data. Selecting full mode does not automatically create 20 imputations.

Statistical output

The script reports TE, NDE, NIE, and PM for medium and high PIU compared with low PIU.

Bootstrap percentile 95% confidence intervals are calculated for TE, NDE, and NIE.

The proportion mediated is calculated as the natural indirect effect divided by the total effect (PM = NIE / TE).

PM is reported as a point estimate only. No confidence interval is calculated or reported for PM.

Interpretation of NDE and NIE as causal effects depends on the identification assumptions described in the manuscript.

Reproducibility

The synthetic demonstration allows researchers and reviewers to inspect the analytical workflow and test the code without access to confidential participant data.

Because the original cohort data are restricted, the demonstration cannot reproduce the numerical estimates reported in the manuscript.

The full analysis uses 20 imputed datasets and 200 bootstrap samples per dataset. The reduced demo setting is intended for testing and illustration rather than validating the manuscript confidence intervals.

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
