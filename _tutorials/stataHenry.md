---
layout: post
title: Stata on Henry2 HPC
feature-img: "https://i.imgur.com/4KpVtQF.png"
date: 10 November 2020
---
##  Stata  
[Stata](https://www.stata.com/products/which-stata-is-right-for-me/) is fully featured data analysis and statistical software

### Using Stata on Henry 2
Versions 13 and 16 of stata are installed on Henry2. To use Stata, you must first load the module:
```
module load stata
```
The Stata binaries are:     
* <span style="color:red">stata</span> - Stata for mid-sized datasets (default Stata/IC) 
* <span style="color:red">stata-mp</span> - The fastest edition of Stata (for multiprocessor computers) that can analyze the most data (Stata/MP)
* <span style="color:red">stata-se</span> - Stata for large datasets (Stata/SE)

### Running Stata      
You can run Stata in three different ways:       
1. Interactive on the HPC Compute Nodes
2. Batch jobs on the HPC Compute Nodes
3. Interactive on the HPC Compute Nodes using GUI

#### Interactive on the HPC Compute Nodes
To request an interactive session on the compute nodes directly, you will [login to Henry 2](https://projects.ncsu.edu/hpc/Documents/Login.php).

For interactive use of STATA, use the commands below on an HPC login node:
Run an interactive (-Is) job with 12 tasks (-n 12) on 1 node (span[hosts=1])
with 12 cores per node (select[hc]) for 20 minutes (-W 20).

This is a good way for troubleshooting and testing script before a long run.
However, you must stay logged in while your jobs are running. For long running jobs, we recommend using batch mode (see below).
```
$ bsub -Is -n 12 -W 20 -R "select[hc] span[hosts=1]" tcsh
$ stata-mp -b do stata_do_script
```

#### Batch jobs on the HPC Compute Nodes
In batch mode, you submit your job to the system and it will run independently, like other HPC jobs. This is the preferred way of submitting large Stata jobs. 
The following is an example of a batch job submission script (stata_job.csh)
that will run a `Stata job` via [LSF](https://projects.ncsu.edu/hpc/Documents/LSF.php#jump) with a do-file called *stata_sample.do*.
```
#!/bin/tcsh
#BSUB -n 12                            ## number of cpus
#BSUB -W 2:30                          ## Wall clock (HH:MM)
##BSUB -q queue_name                   ## Henry2 will make a guess
#BSUB -R span[hosts=1]                 ## Number of nodes
#BSUB -R select[hc]                    ## Nodes with 12 cores
#BSUB -R rusage[mem=24GB]              ## Request 24 GB memory, 2GB/core
#BSUB -J stata_uncg_test               ## Name job on LSF queu
#BSUB -o stata_test.out                ## Name output file
#BSUB -e stata_test.err                ## Name error file
#BSUB -x                               ## Request exclusive run on node
module load stata                      ## Load stata binaries
stata-mp -b do stata_sample            ## execute Stata/MP to run script
```
Then use the command below to submit the job to the compute node:
```
$ bsub < stata_job.csh
```
### Installing Community Tools
The community-contributed `ftools` and `gtools` suites can be added to Stata.
'ftools` or `gtools` is available from the [Statistical Software Components (SSC) archive](https://econpapers.repec.org/software/bocbocode/s458213.htm).

Login on Henry2 and follow the commands below to install tools from the SSC
archive. The pound sign (#) precedes comments.
```
1. module load stata          # load Stata from module
2. stata-mp                   # type and hit return key to start Stata
3. ssc install ftools         # install ftools
4. exit                       # type and hit return to exit Stata
```