---
layout: post
title: Stata on Henry2 HPC
feature-img: "https://i.imgur.com/4KpVtQF.png"
date: 10 November 2020
---
##  Stata  
[Stata](https://www.stata.com/products/which-stata-is-right-for-me/) is fully featured data analysis and statistical software

### Using Stata on Henry 2
Versions 13 and 16 of stata are installed on Henry2
To use Stata, you must first load the module:
```
module load stata
```
The Stata binaries are:     
* <span style="color:red">stata</span> - Stata for mid-sized datasets (default Stata/IC) 
* <span style="color:red">stata-mp</span> - The fastest edition of Stata (for quad-core, dual-core, and multicore/multiprocessor computers) that can analyze the most data (Stata/MP)
* <span style="color:red">stata-se</span> - Stata for large datasets (Stata/SE)
* <span style="color:red">xstata</span> - the gui version of Stata/IC
* <span style="color:red">xstata-se</span> - the gui version of Stata/SE
* <span style="color:red">xstata-mp</span> - the gui multi-processor version of Stata/MP
## Running Stata      
You can run Stata in three different ways:
1. Interactive on the HPC Compute Nodes
2. Batch jobs on the HPC Compute Nodes
3. Interactive on the HPC Compute Nodes using GUI

### Interactive on the HPC Compute Nodes
To use interactive mode on the HPC Compute Nodes, you will [login to Henry 2](https://projects.ncsu.edu/hpc/Documents/Login.php). Request an interactive
session on the compute nodes directly and type the stata commands just as you would on your computer. This is a good way for troubleshooting. However, you must stay logged in while your jobs are running. For long running jobs, we recommend using batch mode (see below).

For interactive use of STATA, use the following command on an HPC login node:
```
Run a job with 12 tasks (-n 12) on 1 node with 12 cores per node.
bsub -Is -n 12 -W 20 -R "select[hc] span[hosts=1]" tcsh
stata-mp -b do stata_do_script
```