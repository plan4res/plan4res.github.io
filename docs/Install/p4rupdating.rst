Updating
~~~~~~~~

Update p4r-env
^^^^^^^^^^^^^^

./plan4res_install.sh -U p4r-env

Update StOpt
^^^^^^^^^^^^

./plan4res_install.sh -U stopt

Update SMS++
^^^^^^^^^^^^

./plan4res_install.sh -U sms++

Change the solver
^^^^^^^^^^^^^^^^^

./plan4res_install.sh -S New_SOLVER [ -I installer -L licence -v
version] (installer to be provided in New_SOLVER is CPLEX or GUROBI,
licence to be provided if New_SOLVER is GUROBI, version to be provided
in New_SOLVER is SCIP)

Update the solver
^^^^^^^^^^^^^^^^^

./plan4res_install.sh -S SOLVER -U SOLVER [ -I installer -L licence -v
version] (installer to be provided in New_SOLVER is CPLEX or GUROBI,
licence to be provided if New_SOLVER is GUROBI, version to be provided
in New_SOLVER is SCIP)

Update plan4res scripts and documentation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following directories can be updated:

-  P4R_DIR/documentation

-  P4R_DIR/p4r-env/scripts/python/openentrance: to update the
   openENTRANCE nomenclature definition.

-  P4R_DIR/p4r-env/scripts/python/plan4res-scripts: to update the data
   processing and visualization scripts

-  P4R_DIR/p4r-env/scripts/include: to update the launching scripts

To check if new versions are available, run the following commands:

1. cd P4R_DIR/p4r-env/scripts/python/openentrance

2. git fetch --dry-run --verbose

If the following output is displayed, it means your installation is up
to date:

.. image:: ../../_static/gitfetch.png
    :width: 650

Otherwise, you can perform the update using:

3. git pull

Do the same with the repositories
p4r-env/scripts/python/plan4res-scripts and p4r-env/scripts/include if
necessary.

Update example of dataset
^^^^^^^^^^^^^^^^^^^^^^^^^

When installing plan4res, an example of dataset is created in
P4R_DIR/data/toyDataset

As plan4res may have been ran in this dataset, it is not recommended to
update it but to download the last version of this toyDataset:

-  From P4R_DIR/p4r-env/data, change the name of the dataset (mv
   toyDataset toyDataset_save)

-  Download the new version of the dataset:
   git clone https://github.com/plan4res/toyDataset

