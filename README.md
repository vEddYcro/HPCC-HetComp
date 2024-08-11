
# Project Title

A brief description of what this project does and who it's for

# HPCC-HetComp
HPCC-HetComp
This directory represents a guide and stack of files required for:
1. Compiling OpenBLAS, required to compile HPCC
2. HPCC Makefiles, needed to compile HPCC
3. HPCC results for our paper for all five of our platforms.

First, we need to shortly describe the procedure of how to prepare these systems for HPCC runs, starting with OpenBLAS.

# OpenBLAS compilation and installation
# as root user
git clone https://github.com/xianyi/OpenBLAS.git; cd OpenBLAS; mkdir -p /opt/OpenBLAS ; make PREFIX=/opt/OpenBLAS; make PREFIX=/opt/OpenBLAS install


# HPCC download and compilation
wget https://hpcchallenge.org/projectsfiles/hpcc/download/hpcc-1.5.0.tar.gz

# Use the provided configuration file from HPCC makefiles directory for platforms mentioned in the paper

Make-arma72 needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with ARM A72-based platform

Make-jetson needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with NVIDIA Jetson TX2 NX-based platform

Make-riscv needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with SiFive HiFive Unmatched-based RISC-V platform

Make-rk1.linux needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with Turing RK1-based ARM platform

Make-x86.linux needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with x86-based platform

After you rename the file in hpl directory, you need to go back to the hpcc directory a level below, and type in the following command to compile hpcc:
make arch=linux

# Starting the HPCC benchmark
After the compilation is done, it's time to use the HPCC configs directory and available files.
They're actually exactly the same, so download any one of them, and save it as a file in hpcc directory named hpccinf.txt.



