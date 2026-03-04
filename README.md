# CHARLS-CVD-Muscle-Psychology-Code
Association of Depressive Trajectories and Handgrip Strength Trajectories with CVD R 4.0.5 code for the study covers four core functions: Multiple Imputation, Univariate Analysis, Cox Regression, Interaction Testing.

Project Overview
This code repository focuses on the analysis of the association between changes in grip strength and cardiovascular disease in middle-aged and elderly patients with depression. The core process includes:
Missing value handling: Supplement missing data through multiple imputation, and complete convergence diagnosis and distribution consistency testing;
Univariate analysis: Group according to the quartiles of grip strength changes, and perform ANOVA/chi square tests on continuous/categorical variables respectively;
Interaction test: based on COX regression test, examine the interaction between grip strength changes and depression trajectory;
Advanced analysis: time-varying Cox regression (PH hypothesis test), additive interaction test (RERI/AP/S), multiple comparison correction, sample size/event count statistics.
Code Structure and Function Description
1. Multiple interpolation (R version)
Suggested file name
multiple_imputation_corrected.R
core functionality
Process missing values in the dataset and optimize the prediction matrix for "singularity errors" (excluding non predictive variables such as ID);
Perform multiple imputation (m=5, max=10) to complete Gelman Rubin convergence diagnosis (PSRF<1.1 indicates convergence);
Verify the consistency of the distribution between the interpolated values and the original observed values (continuous variable KS test, binary variable chi square test);
Export interpolated data in Excel/Orange tab format.
2. Single factor analysis (fully revised version)
Suggested file name
univariate_analysis_final.R
core functionality
Group according to the quartiles of 'Grip strength changes' and conduct univariate analysis on the specified variables;
Continuous variables (such as baseline grip strength, TC, age, etc.): ANOVA analysis+mean ± standard deviation statistics;
Categorical variables (such as gender, education, smoking, etc.): chi square test+frequency (percentage) statistics;
Supports two output methods: manual calculation of results, and tableone package standardized table (exporting CSV).
3. Interaction test (COX regression interaction)
Suggested file name
interaction_test_cox.R
core functionality
Based on Cox proportional hazards regression, test the interaction between grip strength changes and depression trajectory;
Data preprocessing: variable name space processing, categorical variable factor conversion, missing value checking;
Build two models: without interaction terms (base model) and with interaction terms (full model);
Likelihood ratio test is used to calculate the P-value of the interaction term and determine the significance of the interaction effect;
Extract HR/95% CI/P values for each level of the interaction term, verify the PH hypothesis, and export the results to Excel.
4. PH test+additive interaction+multiple comparisons+sample size analysis
Suggested file name
cox_tv_additive_multiple_comparison.R
core functionality
Time variant coefficient COX regression: For variables that violate the PH hypothesis, add a time interaction term;
Stratified analysis: overall/depression subgroups (persistent no depression/remission/persistent depression/new onset depression), quartiles of grip strength/continuous variable;
Multiple comparison correction: interquartile comparison of grip strength within the depression subgroup (Bonferroni/FDR);
Addition interaction test: Calculate RERI, AP, and S values (Bootstrap 1000 validations);
Descriptive statistics: output the sample size, number of events, and event rate of each model exposure group;
Cox analysis of depression alone: the association between four categories of depression trajectories and CVD.
