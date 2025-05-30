# Oceananigans Coupled Global Simulation

This repo is to setup a coupled global simulation using ClimaOcean coupled to 
a biogeochemistry model in OceanBioME. 


## Juila on Grace

Computing is done on Yale's Grace HPC. Here are the steps to get setup with Julia on Grace

1. Make sure you have an account on Grace
2. Log into grace with `ssh netid@grace.ycrc.yale.edu` 
3. Log into the devel partition `salloc -c4 -p devel`
4. Load miniconda `module load miniconda
5. Create a new conda enviroment, useful if you use OOD `conda create --name climaocean python jupyter jupyterlab`. Here I named it climaocean, but you can choose anything
6. Make the environment a kernel so you can use it with notebooks `ycrc_conda_env.sh update`
7. Activate your new environment `conda activate climaocean`
8. Load Julia `module load Julia/1.11.4-linux-x86_64`
9. start the Julia REPL: `julia`
10. Once in the REPL, type `]` to go into the `Pkg` environment
11. From here, type `add IJulia` to add the IJulia kernel. This is so you can use Julia with Jupyter
12. Now if you start an OOD session on Grace, make sure to include `Julia/1.11.4-linux-x86_64` under additional modules and make sure to activate the environment you just created

### Move .julia to project

By defult, the `.julia/` direction is created in the home directory. This is where packages and any necessary downloaded files to be stored.
This directory can become bloated and there is not enough space in your home directory. It is best to move this to `/home/$USER/project/.julia`
and then symlink to the original location in your home directory. Here are the steps to do this:

1. move .julia to project `mv /home/${USER}/.julia /home/${USER}/project/.julia` 
2. symlink to your home direcotry `ln -s /home/${USER}/project/.julia /home/${USER}/.julia`

### Creating a Julia environment

1. navigate to where you want your environment to live
2. type `julia` to start to the REPL
3. then type `]` to start the package manager
4. type `activate .` to set the current working directory as the active environment
5. add packages to the environment `add ClimaOcean OceanBioME`
6. Once that is complete, press `delete` to go to the julia repl then type `exit()` to close out the REPL

