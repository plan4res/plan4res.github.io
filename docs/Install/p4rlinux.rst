.. _installLinux:

Installing on Linux:
~~~~~~~~~~~~~~~~~~~~

Move to your install directory: cd P4R_DIR, and type the following
commands:

   cd P4R_DIR

   git clone https://github.com/plan4res/install

   mv ./install/\* . && rm -rf install

   chmod a+x \*.sh

   ./plan4res_install.sh [-S <SOLVER>] [-I <installer>] [-L <license>]
   [-v <version>] [-M <mpi>]

   Where:

-  SOLVER is the chosen solver among CPLEX, GUROBI, SCIP, HiGHS. If this
   option is not provided, HiGHS is chosen

-  Installer is the installer file for CPLEX of Gurobi, the -I option
   must only be provided when CPLEX or GUROBI are chosen

-  License is the license file, only for GUROBI

-  Version is the solver version, only for SCIP

-  Mpi is the chosen MPI version among MPICH and OpenMPI. If this option
   is not provided, OpenMPI is chosen.

**Examples:**

./plan4res_install.sh

-  Installs plan4res with HiGHS

./plan4res_install.sh -S CPLEX -I cplex_studio2211.linux_x86_64.bin

-  Installs plan4res with CPLEX, using ths installer
   cplex_studio2211.linux_x86_64.bin available in P4R_DIR

./plan4res_install.sh -S GUROBI -I gurobi11.0.1_linux64.tar.gz -L
gurobi.lic

-  Installs plan4res with GUROBI using the gurobi installer and licence
   available in P4R_DIR

./plan4res_install.sh -S SCIP -v 9.1.1

-  Installs plan4res with SCIP, choses the version 9.1.1 from SCIP

It is possible to configure a specific location where the user wishes to
run plan4res. This also allows to install the software once on e.g. a
shared directory in an organization, and run it on different user’s
sessions.

For doing so, copy the script user_init_plan4res.sh which is present in
P4R_DIR to the location where the user wants to run plan4res, e.g.
P4R_DIR_LOCAL and run the command:

./user_init_plan4res -D P4R_DIR -S SOLVER

Where:

-  P4R_DIR is the directory where plan4res has been previously installed

-  SOLVER is the chosen solver among CPLEX, GUROBI, SCIP, HiGHS. If this
   option is not provided, HiGHS is chosen (this allows to configure the
   settings files in the example of dataset according to the choice of
   the solver)
