Installation Summary 
====================

The process to install plan4res is described in the following
subsections.

In summary:

-  Clone the install repo in a chose directory, e.g. P4R_DIR: *git
   clone* https://github.com/plan4res/install

-  Move the files \*.sh from in P4R_DIR, make them executable (*chmod
   a+x \*.sh*)

-  Run the install script: *./plan4res_install.sh* with needed options
   (-S $SOLVER with $SOLVER=CPLEX, GUROBI, SCIP ; else it will use HiGHS
   ; -I $installer if $SOLVER is CPLEX or GUROBI; -L $LICENCE if $SOLVER
   is GUROBI; ….)

-  If you wish to run plan4res from a different directory, e.g
   P4R_DIR_LOCAL, move the script user_init_plan4res.sh in P4R_DIR_LOCAL
   and run it as follows: *./user_init_plan4res.sh -D P4R_DIR -S
   $SOLVER*

After proceeding to the install of plan4res, the software is installed
in P4R_DIR. The datasets should be stored in the subdirectory **data**
of P4R_DIR_LOCAL. Depending of your choices in the install process,
P4R_DIR and P4R_DIR_LOCAL may be identical or different. (in particular
if you are installing on a server, the software will be in P4R_DIR, and
each user will have his P4R_DIR_LOCAL directory, configured by the
*user_init_plan4res.sh* script)

The following subsections details the installation process.

It is recommended to install plan4res with the full environment
(p4r-env), which is embedded in a singularity container. This requires
at least 3Gb. In case you do not have this available, you may install
plan4res without the environment, but it requires installing all the
dependencies first, which may sometimes be quite tricky.

Plan4res requires use of external solver, which can be CPLEX, GUROBI,
SCIP or HiGHS. If you do have a CPLEX or GUROBI license, it is
recommended to use one of these software. If not, it is recommended to
use HiGHS.

If you wish to use CPLEX, you must have a CPLEX linux installer
available, such as cplex_studio2211.linux_x86_64.bin, referenced as
*cplex_studioXXXXXX.bin* below.

If you wish to use GUROBI, you must have a GUROBI linux installer, sur
as gurobi11.0.1_linux64.tar.gz and a gurobi license file: gurobi.lic.

Before starting the install, create an empty directory (for example
*P4R_DIR)* where you want to install plan4res. It should not contain
special characters or whitespaces!

Once installed, the plan4res environment will appear as described in
section
