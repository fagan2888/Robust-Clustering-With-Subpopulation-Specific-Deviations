The Robust Profile Clustering (RPC) model is a population-based clustering technique that adjusts for differences that may exist within different subpopulations. Here, participants are clustered at two levels: (1) globally, where subjects are assigned to an overall population-level cluster using an overfitted mixture model, and (2) locally, where variations to global patterns are accommodated via a Beta-Bernoulli process dependent on subpopulation differences.

Supporting Files
The code and supporting materials are run using MATLAB software. To run the example data, you will need the following four files:

1. RPC_example.m Ð source code to perform RPC

2. drchrnd.m - random generator function for the Dirichlet Distribution that accepts two arguments drchrnd(a,b).
a = vector of Dirichlet hyperparameters
b = number of random draws

3. heatmap.m Ð function file to generate desired heatmap figures (this file is only needed if running MATLAB 2016a or earlier, later versions have this file included in the base library of functions).

4. ExampleData.mat - input data source

EXAMPLE INPUT
The example dataset (ExampleData.mat) is a MAT-file that contains the following variables:

1. subdata: 1800x50 matrix. This matrix is the input dataset containing subject level data for 50 variables. Each variable assigned a single categorical value (1,2,3,4).

2. sub_nu: binary 50x3 matrix. This matrix is used as a reference to illustrate the true probability of allocation for each variable within each subpopulation to global (\nu= 1) or local (\nu= 0).

3. subpop_i: 1800x1 vector. This vector contains subpopulation ID for the 1800 subjects included in the dataset.

4. Subpop1_true: 50x3 matrix. This matrix contains the 3 modal cluster patterns modally expected from subpopulation 1. Each column represents a different global pattern with a deviation reflected in 13 of the 50 variables.
5. Subpop2_true: 50x3 matrix. This matrix contains the 3 modal cluster patterns modally expected from subpopulation 2. Each column represents a different global pattern with a deviation reflected in 24 of the 50 variables.
6. Subpop3_true: 50x3 matrix. This matrix contains the 3 modal cluster patterns modally expected from subpopulation 3. Each column represents a different global pattern with no deviation in any of the 50 variables.

RUNNING RPC CODE
The RPC source file is organized into five parts.

Step 0. DATA INPUT: reading input data (ExampleData.mat)
Step 1. PRIOR SETUP: define prior of all parameters and initial parameter estimates
Step 2. MCMC Data Storage: arrays are preallocated to store MCMC parameter estimates 
Step 3. Posterior Computation: Gibbs sampler of RPC
Step 4. Post-processing: Pasapiliopoulis method to reorder label switching, summary plots, and posterior median estimates, save output

COMPUTATION TIME: approx. 7-8 hours on MATLAB 2017a

EXAMPLE OUTPUT
Execution of the RPC_example.m file with Example dataset should generate the following results:

1. Posterior median estimates of all RPC model parameters (\pi,\lambda,\theta_0,\theta_1,\nu,\beta) saved as RPCparm_ex.mat

2. Text file outputs of \pi,\nu,\beta (pis.txt, nus.txt, betas.txt).
3. Text file output of predicted modal pattern of global clusters (GlobalPattern_predicted.txt)
4. Trace plot figures of \pi, \beta (pis.png, betas.png)
5. Dendrogram plot from posterior pairwise label switching step (dendrogram.png)
6. Heatmap comparison side-by-side plots of predicted deviations by subpopulation and actual deviations by subpopulation. (G_deviations.png) 
