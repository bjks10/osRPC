# osRPC
Ordinal Supervised Robust Profile Clustering 

Ordinal Supervised Robust Profile Clustering (osRPC) model is an extension of the Supervised Robust Profile Clustering ([sRPC](https://github.com/bjks10/supRPC/)) model, which is a flexible joint model that can identify high-dimensional exposure patterns that are dependent on an ordinal outcome. Exposure patterns are clustered at two levels: (1) globally, where individuals share an overall population-level pattern via an overfitted finite mixture model, and (2) locally, where a subset of exposure variables deviate from the global pattern via a Beta-Bernoulli process to assume a subpopulation-specific pattern. The exposure model is jointly modeled with an ordinal probit regression model, where the global profiles are informed by the probability of the ordinal outcome. 


# Getting Started

The code and supporting materials are run using MATLAB software. To run the example data, you will need the main file (sim_osRPC15.m) contained in the Simulation folder, as well as the following supporting function files provided here:

drchrnd.m - Dirichlet random generator function
truncnorm2.m - function file to generate draw from truncated normal random distribution

The parameters of the supRPC model are estimated in a two-step sampling algorithm. 
* The adaptive sampling algorithm allows the user to determine the appropriate number of nonempty clusters. 
* The fixed sampling algorithm allows the user to re-run the osRPC model with the number of nonempty clusters predetermined. 

When the number of clusters, globally and locally, is known a priori the adaptive sampling step can be skipped. The attached code was applied to data from the Hispanic Community Health Study/Study of Latinos, which is publicly available through a Data and Materials Distribution Agreement (DMDA). 


# Simulated Examples
The example dataset found in the Simulation folder is a MAT-file that contains the following variables:

* sampledata: 4800x50 matrix. This matrix is the input dataset containing subject level data for 50 variables. Each variable assigned a single categorical value (1,2,3,4).
* trueG: binary 4x50 matrix. This matrix is used as a reference to illustrate the true probability of allocation for each variable within each subpopulation to global (ν= 1) or local (ν= 0).
* subpop_samp: 4800x1 vector. This vector contains subpopulation ID for the 4800 subjects included in the dataset.
* true_global: 50x3 matrix. This matrix contains the 3 global profile patterns modally expected. 
* true_ci: 4800x1 matrix. This matrix contains the true global profile assignment to each subject.
* true_local: 8x50 matrix. This matrix contains the two local profile patterns modally expected for each subpopulation. Rows 1-2 correspond to subpopulation 1. Rows 3-4 correspond to subpopulation 2. Rows 5-6 correspond to subpopulation 3. Rows 7-8 correspond to subpopulation 4.  
* true_Li: 4800x1 matrix. This matrix contains the local profile assignment to each subject.
* true_xi: 1x7 vector. This row vector contains the true coefficients of the probit regression model
* true_ordy: 4800x1 vector. This column vector contains the true ordinal outcome for each subject taking on values of 1,2, or 3.
* phi_WXtrue: 4800x1 vector. This column vector contains the true probability of outcome for each subject.

The case demonstrated in the Simulation folder contains a simulated population composed of 4 subpopulations that share 3 global patterns. Each subpopulation has 2 local patterns present in a subset of variables, defined by 'trueG'. 

Authors

Briana Stephenson, Daniela Sotres-Alvarez, Jianwen Cai

