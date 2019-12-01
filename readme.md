# Robust Clustering With Subpopulation-Specific Deviations

# Author Contributions Checklist Form

## Data

### Abstract 

The NBPDS dataset used for this manuscript contains 12440 subjects from 10 identified subpopulations. Each subject has categorical values (1,2,3,4) for 63 variables. The simulated dataset, made available to demonstrate the model discussed in this manuscript is stored in a MAT-File saved as ExampleData.mat. The dataset contains the following variables:

*	subdata: 1800x50 matrix. This matrix is the input dataset containing subject level data for 50 variables. Each variable assigned a single categorical value (1,2,3,4) probabilistically, as described in the simulation section of the manuscript. 
*	sub_nu: binary 50x3 matrix. This matrix is used as a reference to illustrate the true probability of allocation for each variable within each subpopulation to global (ν= 1) or local (ν= 0). 
*	subpop_i: 1800x1 vector. This vector contains subpopulation ID for the 1800 subjects included in the dataset.
*	Subpop1_true: 50x3 matrix. This matrix contains the 3 modal cluster patterns modally expected from subpopulation 1. Each column represents a different global pattern with a deviation reflected in 13 of the 50 variables. 
*	Subpop2_true: 50x3 matrix. This matrix contains the 3 modal cluster patterns modally expected from subpopulation 2. Each column represents a different global pattern with a deviation reflected in 24 of the 50 variables.
*	Subpop3_true: 50x3 matrix. This matrix contains the 3 modal cluster patterns modally expected from subpopulation 3. Each column represents a different global pattern with no deviation in any of the 50 variables. 

### Availability 

The dataset used in the manuscript comes from the National Birth Defects Prevention Study. This data contains personally identifiable information (PII). For this reason, it is not available for public distribution. The example dataset and code will be made publicly available on GitHub. 

### Description 

MATLAB code, data, and supporting materials is found at https://github.com/bjks10/RPC. 


## Code

### Abstract 
The attached code is a single matlab file that performs the RPC model referenced in the manuscript (RPC_example.m) and supporting matlab function files: drchrnd.m, heatmap.m. The input dataset to use and a MAT-file dataset (ExampleData.mat) to be used as a data source.

Description (Mandatory)
MATLAB code, data, and supporting materials is found at https://github.com/bjks10/RPC. 

Optional Information (complete as necessary) 
Supporting software requirements: MATLAB 2013 or later

### Description

The Robust Profile Clustering (RPC) model is a population-based clustering technique that adjusts for differences that may exist within different subpopulations. Here, participants are clustered at two levels: (1) globally, where subjects are assigned to an overall population-level cluster using an overfitted mixture model, and (2) locally, where variations to global patterns are accommodated via a Beta-Bernoulli process dependent on subpopulation differences.

Supporting Files
The code and supporting materials are run using MATLAB software. To run the example data, you will need the following four files:

1. RPC_example.m - source code to perform RPC

2. drchrnd.m - random generator function for the Dirichlet Distribution that accepts two arguments drchrnd(a,b).
a = vector of Dirichlet hyperparameters
b = number of random draws

3. heatmap.m - function file to generate desired heatmap figures (this file is only needed if running MATLAB 2016a or earlier, later versions have this file included in the base library of functions).

4. ExampleData.mat - input data source

### Optional information

Supporting software requirements: MATLAB 2013 or later


## Instructions for Use

### Reproducibility

COMPUTATION TIME: approx. 7-8 hours on MATLAB 2017a

Execution of RPC model can be performed with the following code and supporting function files: RPC_example.m, drchrnd.m, heatmap.m. Accompanied with the example dataset (ExampleData.mat), the following output should be produced:

*	Posterior median estimates of all RPC model parameters (π,λ,θ_0,θ_1,ν,β) saved as RPCparm_ex.mat
*	Text file outputs of π,ν,β (pis.txt, nus.txt, betas.txt).
*	Text file output of predicted modal pattern of global clusters (GlobalPattern_predicted.txt)
*	Trace plot figure of π (pis.png)
*	Trace plot figure of β (betas.png)
*	Dendrogram plot from Posterior pairwise label switching step (dendrogram.png)
*	Heat map comparison side-by-side plots of predicted deviations by subpopulation and actual deviations by subpopulation. (G_deviations.png)


