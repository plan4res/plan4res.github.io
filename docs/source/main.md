

Table of Content

[1 Quick Install and Run 5](#_Toc190931990)

[1.1 Quick Install 5](#_Toc190931991)

[1.2 Quick Run 5](#_Toc190931992)

[2 Installing Plan4res 6](#_Toc190931993)

[2.1 Installation of the full plan4res environment, for all operating systems 6](#_Toc190931994)

[2.1.1 _I_nstalling on Linux: 6](#_Toc190931995)

[2.1.2 Installing on Windows, using WLS 8](#_Toc190931996)

[2.1.3 _I_nstalling on Windows, using Vagrant 8](#_Toc190931997)





# Quick Install and Run

## Quick Install

- Clone the install repo in a chose directory, e.g. P4R_DIR: _git clone_ [_https://github.com/plan4res/install_](https://github.com/plan4res/install)
- Move the files \*.sh from in P4R_DIR, make them executable (_chmod a+x \*.sh_)
- Run the install script: _./plan4res_install.sh_ with needed options (-S $SOLVER with $SOLVER=CPLEX, GUROBI, SCIP ; else it will use HiGHS ; -I $installer if $SOLVER is CPLEX or GUROBI; -L $LICENCE if $SOLVER is GUROBI; ….)

If you wish to run plan4res from a different directory, e.g P4R_DIR_LOCAL, move the script user_init_plan4res.sh in P4R_DIR_LOCAL and run it as follows: _./user_init_plan4res.sh -D P4R_DIR -S $SOLVER_

## Quick Run

- Create dataset in P4R_DIR_LOCAL/data (e.g. YourDataset), with a subdirectory IAMC, a subdirectory settings and a subdirectory TimeSeries
- Move your IAMC file (as computed by GENeSYS-MOD for instance) in IAMC/ and rename it YourDataset.xlsx
- Copy the settings files from P4R_DIR_LOCAL/data/settings/toyDataset to settings/
- Create or get and Upload your timeseries to TimeSeries
- Edit configuration files in settings:
  - Edit settingsCreatePlan4res_simul.yml and settingsCreatePlan4res_invest.yml (in particular the IAMC scenario and year, the list of regions, the regions partitions, the list of technologies, the list of scenarios, the definition of coupling constraints, the initial filling rates, the (optional) parameters for capacity expansion, and if necessary the list of variables to use from your IAMC file)
  - Edit DictTimeSeries.yml (so that is has the good names for your timeseries)
  - If necessary (if you have changed some variable names in settingsCreatePlan4res_XXX.yml), edit the VariablesDictionnary.yml
- Run CREATE: p4r CREATE YourDataset (with option -M invest if running a capacity expansion case)
- Edit settings_format_optim.yml, settings_format_simul.yml and settings_format_invest.yml configuration files in settings (in particular the sections Calendar, and the Scenarios and ScenarisedData in section ParametersFormat)
- Run SSV: p4r SSV YourDataset
- Run SIM: p4r SIM YourDataset
- Run CEM: p4r CEM YourDataset
- Edit settingsPostTreatPlan4res_simul.yml and settingsPostTreatPlan4res_invest.yml in settings. In particular, the start and end dates of you study, the list of technologies (if you added new technologies), and the size of graphs (to allow to cope with all regions / all interconnections / all technos)
- Run POSTTREAT: p4r POSTTREAT YourDataset (with option -M invest if running a capacity expansion case)

# Installing Plan4res

The process to install plan4res is described in the following subsections.

In summary:

- Clone the install repo in a chose directory, e.g. P4R_DIR: _git clone_ [_https://github.com/plan4res/install_](https://github.com/plan4res/install)
- Move the files \*.sh from in P4R_DIR, make them executable (_chmod a+x \*.sh_)
- Run the install script: _./plan4res_install.sh_ with needed options (-S $SOLVER with $SOLVER=CPLEX, GUROBI, SCIP ; else it will use HiGHS ; -I $installer if $SOLVER is CPLEX or GUROBI; -L $LICENCE if $SOLVER is GUROBI; ….)
- If you wish to run plan4res from a different directory, e.g P4R_DIR_LOCAL, move the script user_init_plan4res.sh in P4R_DIR_LOCAL and run it as follows: _./user_init_plan4res.sh -D P4R_DIR -S $SOLVER_

After proceeding to the install of plan4res, the software is installed in P4R_DIR. The datasets should be stored in the subdirectory **_data_** of P4R_DIR_LOCAL. Depending of your choices in the install process, P4R_DIR and P4R_DIR_LOCAL may be identical or different. (in particular if you are installing on a server, the software will be in P4R_DIR, and each user will have his P4R_DIR_LOCAL directory, configured by the _user_init_plan4res.sh_ script)

The following subsections details the installation process.

It is recommended to install plan4res with the full environment (p4r-env), which is embedded in a singularity container. This requires at least 3Gb. In case you do not have this available, you may install plan4res without the environment, but it requires installing all the dependencies first, which may sometimes be quite tricky.

Plan4res requires use of external solver, which can be CPLEX, GUROBI, SCIP or HiGHS. If you do have a CPLEX or GUROBI license, it is recommended to use one of these software. If not, it is recommended to use HiGHS.

If you wish to use CPLEX, you must have a CPLEX linux installer available, such as cplex_studio2211.linux_x86_64.bin, referenced as _cplex_studioXXXXXX.bin_ below.

If you wish to use GUROBI, you must have a GUROBI linux installer, sur as gurobi11.0.1_linux64.tar.gz and a gurobi license file: gurobi.lic.

Before starting the install, create an empty directory (for example _P4R_DIR)_ where you want to install plan4res. It should not contain special characters or whitespaces!

Once installed, the plan4res environment will appear as described in section

## Installation of the full plan4res environment, for all operating systems

Requirements: at least 3G available.

### Installing on Linux

Move to your install directory: cd P4R_DIR, and type the following commands:

cd P4R_DIR

git clone <https://github.com/plan4res/install>

mv ./install/\* . && rm -rf install

chmod a+x \*.sh

./plan4res_install.sh \[-S &lt;SOLVER&gt;\] \[-I &lt;installer&gt;\] \[-L &lt;license&gt;\] \[-v &lt;version&gt;\] \[-M &lt;mpi&gt;\]

Where:

- SOLVER is the chosen solver among CPLEX, GUROBI, SCIP, HiGHS. If this option is not provided, HiGHS is chosen
- Installer is the installer file for CPLEX of Gurobi, the -I option must only be provided when CPLEX or GUROBI are chosen
- License is the license file, only for GUROBI
- Version is the solver version, only for SCIP
- Mpi is the chosen MPI version among MPICH and OpenMPI. If this option is not provided, OpenMPI is chosen.

**Examples:**

./plan4res_install.sh

- Installs plan4res with HiGHS

./plan4res_install.sh -S CPLEX -I cplex_studio2211.linux_x86_64.bin

- Installs plan4res with CPLEX, using ths installer cplex_studio2211.linux_x86_64.bin available in P4R_DIR

./plan4res_install.sh -S GUROBI -I gurobi11.0.1_linux64.tar.gz -L gurobi.lic

- Installs plan4res with GUROBI using the gurobi installer and licence available in P4R_DIR

./plan4res_install.sh -S SCIP -v 9.1.1

- Installs plan4res with SCIP, choses the version 9.1.1 from SCIP

It is possible to configure a specific location where the user wishes to run plan4res. This also allows to install the software once on e.g. a shared directory in an organization, and run it on different user’s sessions.

For doing so, copy the script user_init_plan4res.sh which is present in P4R_DIR to the location where the user wants to run plan4res, e.g. P4R_DIR_LOCAL and run the command:

./user_init_plan4res -D P4R_DIR -S SOLVER

Where:

- P4R_DIR is the directory where plan4res has been previously installed
- SOLVER is the chosen solver among CPLEX, GUROBI, SCIP, HiGHS. If this option is not provided, HiGHS is chosen (this allows to configure the settings files in the example of dataset according to the choice of the solver)

### Installing on Windows, using WLS

Follow the procedure ‘Installing on Linux’

### Installing on Windows, using Vagrant

The procedure is available at [**https://gitlab.com/cerl/plan4res/p4r-env#windows**](https://gitlab.com/cerl/plan4res/p4r-env#windows). It is reproduced below with some more information.

Installation requires Windows 7 Pro 64bit SP1 or higher and [PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-windows-powershell?view=powershell-6) 3.0 or higher. Furthermore, the CPU must support [hardware virtualization](https://www.virtualbox.org/manual/ch10.html#hwvirt). On many systems, the hardware virtualization features first need to be enabled in the BIOS.

#### Required packages Installation (execute once)

- Install Git for Windows (use default settings) <https://git-for-windows.github.io/>
- Install VirtualBox and Extension Pack <https://www.virtualbox.org/wiki/Downloads>
- Install Vagrant <https://www.vagrantup.com/downloads.html>
- (Optional) Install Vagrant Manager <http://vagrantmanager.com/downloads/>

The goal of Vagrant and VirtualBox is to emulate a UNIX system on the Windows computer. Vagrant Manager provides a GUI to facilitate the management of the VM.

#### Installation

Run Git Bash.

If working behind a proxy, define the following environment variables:

export http_proxy = &lt;proxy address&gt;:&lt;port&gt;

export https_proxy = ${http_proxy}

Move to your installation directory:

cd P4R_DIR

Then enter the following commands:

git clone <https://github.com/plan4res/install>

mv ./install/\* .

chmod a+x \*.sh

./plan4res_install.sh \[-S &lt;SOLVER&gt;\] \[-I &lt;installer&gt;\] \[-L &lt;license&gt;\] \[-v &lt;version&gt;\] -M MPICH -V &lt;memory&gt;

Where:

- SOLVER is the chosen solver among CPLEX, GUROBI, SCIP, HiGHS. If this option is not provided, HiGHS is chosen
- Installer is the installer file for CPLEX of Gurobi, the -I option must only be provided when CPLEX or GUROBI are chosen
- License is the license file, only for GUROBI
- Version is the solver version, only for SCIP

**Examples:**

./plan4res_install.sh -M MPICH -V 8192

- Installs plan4res with HiGHS

./plan4res_install.sh -M MPICH -V 8192 -S CPLEX -I cplex_studio2211.linux_x86_64.bin

- Installs plan4res with CPLEX, using ths installer cplex_studio2211.linux_x86_64.bin available in P4R_DIR

./plan4res_install.sh -M MPICH -V 8192 -S GUROBI -I gurobi11.0.1_linux64.tar.gz -L gurobi.lic

- Installs plan4res with GUROBI using the gurobi installer and licence available in P4R_DIR

./plan4res_install.sh -M MPICH -V 8192 -S SCIP -v 9.1.1

- Installs plan4res with SCIP, choses the version 9.1.1 from SCIP


