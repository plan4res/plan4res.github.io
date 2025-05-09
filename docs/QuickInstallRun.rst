Quick Install and Run
=====================

Quick Install
-------------

-  Clone the install repo in a chose directory, e.g. P4R_DIR: *git
   clone* https://github.com/plan4res/install

-  Move the files \*.sh from in P4R_DIR, make them executable (*chmod
   a+x \*.sh*)

-  Run the install script: *./plan4res_install.sh* with needed options
   (-S $SOLVER with $SOLVER=CPLEX, GUROBI, SCIP ; else it will use HiGHS
   ; -I $installer if $SOLVER is CPLEX or GUROBI; -L $LICENCE if $SOLVER
   is GUROBI; ….)

If you wish to run plan4res from a different directory, e.g
P4R_DIR_LOCAL, move the script user_init_plan4res.sh in P4R_DIR_LOCAL
and run it as follows: *./user_init_plan4res.sh -D P4R_DIR -S $SOLVER*

Quick Run
---------

-  Create dataset in P4R_DIR_LOCAL/data (e.g. YourDataset), with a
   subdirectory IAMC, a subdirectory settings and a subdirectory
   TimeSeries

-  Move your IAMC file (as computed by GENeSYS-MOD for instance) in
   IAMC/ and rename it YourDataset.xlsx

-  Copy the settings files from P4R_DIR_LOCAL/data/settings/toyDataset
   to settings/

-  Create or get and Upload your timeseries to TimeSeries

-  Edit configuration files in settings:

   -  Edit settingsCreatePlan4res_simul.yml and
      settingsCreatePlan4res_invest.yml (in particular the IAMC scenario
      and year, the list of regions, the regions partitions, the list of
      technologies, the list of scenarios, the definition of coupling
      constraints, the initial filling rates, the (optional) parameters
      for capacity expansion, and if necessary the list of variables to
      use from your IAMC file)

   -  Edit DictTimeSeries.yml (so that is has the good names for your
      timeseries)

   -  If necessary (if you have changed some variable names in
      settingsCreatePlan4res_XXX.yml), edit the VariablesDictionnary.yml

-  Run CREATE: p4r CREATE YourDataset (with option -M invest if running
   a capacity expansion case)

-  Edit settings_format_optim.yml, settings_format_simul.yml and
   settings_format_invest.yml configuration files in settings (in
   particular the sections Calendar, and the Scenarios and
   ScenarisedData in section ParametersFormat)

-  Run SSV: p4r SSV YourDataset

-  Run SIM: p4r SIM YourDataset

-  Run CEM: p4r CEM YourDataset

-  Edit settingsPostTreatPlan4res_simul.yml and
   settingsPostTreatPlan4res_invest.yml in settings. In particular, the
   start and end dates of you study, the list of technologies (if you
   added new technologies), and the size of graphs (to allow to cope
   with all regions / all interconnections / all technos)

-  Run POSTTREAT: p4r POSTTREAT YourDataset (with option -M invest if
   running a capacity expansion case)