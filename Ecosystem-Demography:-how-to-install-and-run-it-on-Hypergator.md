# What is Ecosystem Demography (ED2.1)?
ED is a process oriented deterministic model aiming at scaling vegetation dynamics (Moorcroft et al., 2001, Medvigy et al., 2012). The ecosystem structure is simulated by quantifying ecophysiological processes occurring on plant functional type level (i.e. fake species whose physiological and allometric parameters are kept constant in space and time). Detailed information about ED can be found in the github project https://github.com/EDmodel

# How to compile it on the Hypergator
The HyperGator comes with the possibility to load Intel Compilers, which I would suggest to use to get rid of some retro-compatibility issues found in gfortran. 

## Fork the project using Git
The whole project is on github. To fork the master, follow this guide: https://github.com/EDmodel/ED2/wiki/Using-Github-with-ED2
## Create your include.mk file
Here comes the most complicated part. For the HyperGator I'd suggest to use the following platform file:

`MAKE=/usr/bin/make`

` BASE=$(ED_ROOT)/build/`

` USE_HDF5=1`

`HDF5_PATH=/apps/intel/2013.sp1.3.174/hdf5/1.8.15`

`HDF5_INCS=-I$(HDF5_PATH)/include`

`HDF5_LIBS= -lz -lm -L$(HDF5_PATH)/lib -lhdf5 -lhdf5_fortran -lhdf5_hl`

`USE_COLLECTIVE_MPIO=0`

`CMACH=PC_LINUX1`

`F_COMP=mpifort`

`C_COMP=mpicc`

`LOADER=mpifort`

`LIBS=`

`MOD_EXT=mod`

`ifeq ($(KIND_COMP),)`

    `KIND_COMP=E`

`endif`

`ifeq ($(KIND_COMP),A)`

    `USE_INTERF=0`

    `F_OPTS= -FR -O0 -recursive  -check all -g -debug extended -debug-parameters used -fpe0 -no-ftz -traceback -
ftrapuv -fp-stack-check -implicitnone -assume byterecl -warn unused -warn uncalled -warn usage -gen-interfaces`

    `C_OPTS= -O0 -DLITTLE  -g -traceback`

    `LOADER_OPTS=$(F_OPTS)`

`endif`

`ifeq ($(KIND_COMP),B)`

   `USE_INTERF=0`

   `F_OPTS= -FR -O0 -recursive  -check all -g -debug extended -debug-parameters used -fpe0 -no-ftz -traceback -ftrapuv -fp-stack-check -implicitnone -assume byterecl -warn unused -warn uncalled -warn usage -warn interfaces`

   `C_OPTS= -O0 -DLITTLE  -g -traceback`

   `LOADER_OPTS=$(F_OPTS)`

`endif`

`ifeq ($(KIND_COMP),C)`

   `USE_INTERF=1`

   `F_OPTS= -FR -O0 -recursive  -check all -g -debug extended -debug-parameters used -fpe0 -no-ftz -traceback -ftrapuv -fp-stack-check -implicitnone  -assume byterecl`

   `C_OPTS= -O0 -DLITTLE  -g -traceback`

   `LOADER_OPTS=$(F_OPTS)`

`endif`

`ifeq ($(KIND_COMP),D)`

   `USE_INTERF=1`

   `F_OPTS= -FR -O0 -recursive -check all-fpe0 -no-ftz -traceback -ftrapuv -fp-stack-check  \`
           `-implicitnone -assume byterecl`

   `C_OPTS= -O0 -DLITTLE  -g -traceback`

   `LOADER_OPTS=$(F_OPTS)`

`endif`

`ifeq ($(KIND_COMP),E)`

   `USE_INTERF=1`

   `F_OPTS= -FR -O3 -recursive -traceback -assume byterecl`

   `C_OPTS= -O3 -DLITTLE -traceback`

   `F_LOWO_OPTS=-FR -O2 -recursive -traceback -assume byterecl`

   `LOADER_OPTS=$(F_OPTS)`

   `endif`

`MPI_PATH=`

`PAR_INCS=`

`PAR_LIBS=`

`PAR_DEFS=-DRAMS_MPI`

`ARCHIVE=ar rs`

## Compile the beast
Due to ram limitation, the program can only be compiled submitting a job. To submit a job, check Shawn and Dave's wiki page https://github.com/weecology/lab-wiki/wiki/Using-HiPerGator
I would advice to use a job with the following structure:

`#install ED2.1 on hipergator`

`#!/bin/bash                                                                                                 `

`#PBS -N nameJob                                                                                               `

`#PBS -M your@mail.edu                                                                                   `

`#PBS -m abe                                                                                                 `

`#PBS -o nameJob$PBS_JOBID.out                                                                                 `

`#PBS -e nameJob $PBS_JOBID.err                                                                                 `

`#PBS -l nodes=1:ppn=2                                                                                       `

`#PBS -l pmem=1gb                                                                                            `

`#PBS -l walltime=01:00:00                                                                                   `

`[[ -d $PBS_O_WORKDIR ]] && cd $PBS_O_WORKDIR`

`date;hostname;pwd`

`module load intel/2016.0.109 openmpi hdf5`

`cd /home/username/ED2/ED/build`

`./install.sh --clean`

`./install.sh --platform ufl`

`date`
 