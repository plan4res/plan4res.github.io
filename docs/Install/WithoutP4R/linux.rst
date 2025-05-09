Installing on Linux
~~~~~~~~~~~~~~~~~~~

Install python:
^^^^^^^^^^^^^^^

Python3 must be the default version of python

The following python packages must be installed (e.g. with pip-install):

   *setuptools, openpyxl, scipy, pandas, pyyaml, matplotlib, geopandas,
   fiona, descartes, shapely, pillow, mapclassify, numpy, requests,
   requests-toolbelt, rtree, pygeos, wheel, netCDF4, pyam-iamc*

Install SMS++ dependencies
^^^^^^^^^^^^^^^^^^^^^^^^^^

The requirements for installing SMS++ are described in the SMS++ gitlab
repo [1]_. Their installation may be included in the installation script
of SMS++, but, in particular in the case of a Linux installation, the
version which would be installed depend on which linux OS is installed
(and which version), and thus may be too old. (This in particular
happens on linux Debian::bullseye). In that case you should install
manually a more recent version.

For each SOFTWARE install, on linux, PATH and LD_LIBRARY_PATH must be
updated to include $SOFTWARE_PATH/mpi and $SOFTWARE_PATH/mpi/lib. For
BOOST, the variable $BOOST_PATH must also be set.

-  **Boost**\  [2]_ **(minimum version 1.87).**

-  **OpenMPI**\  [3]_ **(minimum version 3.1.4) OR MPICH**\  [4]_
   **(minimum version 3.3.2)**

-  **NETCDF**\  [5]_ **(minimum version 4.9.2) and NETCDFCXX (minimum
   version: 4.3.1).**

-  **Eigen**\  [6]_ **(minimum version 3.3.7)**

-  **Cmake**\  [7]_ **(minimum version 3.28.1)**

Install plan4res
^^^^^^^^^^^^^^^^

   Mkdir P4R_DIR (can be any directory name)

   cd P4R_DIR

   git clone https://github.com/plan4res/install

   chmod a+x \*.sh

   ./plan4res_install.sh -X -S <SOLVER> [-D <solverpath>] [-I
   <installer>] [-L <license>] [-v <version>] [-M <mpi>]

   Where:

-  SOLVER is the chosen solver among CPLEX, GUROBI, SCIP, HiGHS. If this
      option is not provided, HiGHS is chosen

-  solverpath is to be provided if the solver is already installed in
      your system. In that case you need to provide the path where it is
      installed

   -  for CPLEX: solverpath is where you find e.g. cplex/bin and
      cplex/lib

   -  for GUROBI: solverpath is where you find e.g. gurobi1101/linux64
      and gurobi1101/gurobi.lic is version 11.01 is installed

   -  for HiGHS: solverpath is where you find bin, include and lib

-  Installer is the installer file for CPLEX of Gurobi, the -I option
      must only be provided when CPLEX or GUROBI are chosen

-  License is the license file, only for GUROBI

-  Version is the solver version, only for SCIP

-  mpi is the chosen MPI version among MPICH and OpenMPI. If this option
      is not provided, OpenMPI is chosen.

Plan4res running scripts
^^^^^^^^^^^^^^^^^^^^^^^^

It is possible to get the plan4res running scripts with git clone
https://github.com/plan4res/include but some adaptations will need to be
made in order to make those scripts functional without the p4r-env
environment. This has not been done yet.
