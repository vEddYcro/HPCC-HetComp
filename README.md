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


# HPCC download and configuration
wget https://hpcchallenge.org/projectsfiles/hpcc/download/hpcc-1.5.0.tar.gz

Use the provided configuration file from HPCC makefiles directory for platforms mentioned in the paper
# Make-arma72 needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with ARM A72-based platform
# Make-jetson needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with NVIDIA Jetson TX2 NX-based platform
# Make-riscv needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with SiFive HiFive Unmatched-based RISC-V platform
# Make-rk1.linux needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with Turing RK1-based ARM platform
# Make-x86.linux needs to be renamed to Make.linux and copied to HPCC's hpl directory, if you're working with x86-based platform

After you rename the file in hpl directory, you need to go back to the hpcc directory a level below, and type in the following command to compile hpcc:
make arch=linux

After the compilation is done, it's time to use the HPCC configs directory and available files.
They're actually exactly the same, so here's the content of all of these files. You need to save this content to a file in hpcc directory named hpccinf.txt.

HPLinpack benchmark input file
Innovative Computing Laboratory, University of Tennessee
HPL.out      output file name (if any)
6            device out (6=stdout,7=stderr,file)
1            # of problems sizes (N)
10000        Ns
1            # of NBs
128          NBs
0            PMAP process mapping (0=Row-,1=Column-major)
1            # of process grids (P x Q)
1            Ps
1            Qs
16.0         threshold
1            # of panel fact
2            PFACTs (0=left, 1=Crout, 2=Right)
1            # of recursive stopping criterium
4            NBMINs (>= 1)
1            # of panels in recursion
2            NDIVs
1            # of recursive panel fact.
1            RFACTs (0=left, 1=Crout, 2=Right)
1            # of broadcast
1            BCASTs (0=1rg,1=1rM,2=2rg,3=2rM,4=Lng,5=LnM)
1            # of lookahead depth
1            DEPTHs (>=0)
0            SWAP (0=bin-exch,1=long,2=mix)
1            swapping threshold
1            L1 in (0=transposed,1=no-transposed) form
1            U  in (0=transposed,1=no-transposed) form
0            Equilibration (0=no,1=yes)
8            memory alignment in double (> 0)

