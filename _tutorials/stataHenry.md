---
layout: post
title: Stata on Henry2 HPC
feature-img: "assets/img/pexels/computer.jpeg"
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

With the help of [Prof. Jay Li](https://bryan.uncg.edu/faculty-and-staff/li-yin/), we have a script that you can use to generate a sample Stata `.do` file.
[Dowload](https://raw.githubusercontent.com/jtande/jhub-file-download/master/Stata/make_script.sh) the bash script and generate the `.do` file. Login to
Henry2 and in your home directory download the `make_script.sh` with the following: 

```
$ wget https://raw.githubusercontent.com/jtande/jhub-file-download/master/Stata/make_script.sh
```
Generate the `.do` file by hitting the return key after each command.  Note the `./` on the second command.

```
$ chmod +x make_script.sh
$ ./make_script.sh > stata_do_script.do
```
Before the interactive session follow instructions below to
[install community tools](#CommunityTools) needed by Stata.
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
<a name="CommunityTools"></a>
### Installing Community Tools
The community-contributed (e.g `ftools` and `ivreg2` suites) can be added to
Stata. These packages are available from the [Statistical Software Components (SSC) archive](https://econpapers.repec.org/software/bocbocode/s458213.htm).

Login on Henry2 and follow the commands below to install tools from the SSC
archive. The pound sign (#) precedes comments. These commands need to be
exercised when you are at your home directory. Don't try to include these
commands in your Stata .do file because a .do file runs on the HPC compute
nodes that does not communicate with the SSC.
```
1. module load stata          # load Stata from module
2. stata-mp                   # type and hit return key to start Stata
3. ssc install ftools         # install ftools
4. ssc install ivreg2         # install ivreg2
5. ssc inst ranktest          # inst ranktest
6. ssc inst outreg2           # inst outreg2
7. exit                       # type and hit return to exit Stata
```
### HPC Compute Resource Management
Compute resource management is important for a smooth execution.

### Memory Management
[Memory management in Linux](https://www.stata.com/manuals13/u6.pdf) is
different from Windows. It is [strongly recommended](https://www.stata.com/manuals13/dmemory.pdf#dmemoryRemarksandexamplesSeriousbuginLinuxOS) that the
parameter <span style="color:red">max_memory</span> be defined when running in a Linux environment.

The value of <span style="color:red">max_memory</span> should match the memory
requested in the batch script <span style="color:red">#BSUB -R rusage[mem=24GB]</span>. The following should then be defined in the .do file. <span style="color:red">set max_memory 24gb, permanently</span>. The option `permanently` ensures maximum memory is set once for the job. 

### Using Multiprocessors
We recommend requesting resources such as the number of CPUs prudently. Using too many CPUs may generate temporary data files that exceed your shared storage, causing crashes. The number of processors should be set to ensure there is at
least `2GB of memory/processor`. Processors and cores are used interchangeably. In the batch script above, we requested 12 processors (-n 12) and 24GB of memory.
