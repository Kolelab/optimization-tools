# optimization-tools
Framework for automated generation and optimization of neuron models

To run a model for the first time:
	- Download and install NEURON.
	- Import cellular morphology via getmorph.hoc.
	- Load morphology with loadmorph.hoc to identify recorded sections
	- Run setup.hoc
	- This process should be performed once per cell
	- Once setup.hoc is completed, the model may be opened with openmodel.hoc


Startup options:
getmorph.hoc
	- Import cellular morphology (in ASCII format or other)

loadmorph.hoc
	- Load cellular morphology in 3D.
	- Identify cellular locations of interest by section name and sublocation (0-1).

setup.hoc
	- Quintessential starting point to create a model cell.
	- Requires recording setup information and data.
	- Initialize the model cell (mode, axon type, session options, etc).

compilemod.hoc
	- Compile or recompile mod files.
	- Required for running any model.
	- Run once after setup or download to a new machine.

openmodel.hoc
	- View and test the model.
	- Try different parameter combinations.
	- Run optimizations.
	- etc.
	- Typical entry point after setup.
	- Broadest option for model interaction.

resetmode.hoc
	- Switch mode from passive to active and vice versa.

resetses.hoc
	- Reset session data (recording information) to mode-appropriate default options.

resetaxon.hoc
	- Switch between model axon options. 
	- Available options include no myelin, single cable and double cable.

*modeltype*.type
	- Describes current model setup. Composed of three parts separated by dashes.
	- First part: active ("act") or passive ("pas").
	- Second part: selected cellular location(s) of interest combination. SO = soma, AX = axon, DE = dendrite.
	- Third part: axon model type. NOMY = no myelin, SC = single cable, DC = double cable, etc.
	- Updated after opening openmodel.hoc.

startopt.hoc
	- Run massive optimization of passive parameters using custom optimization procedure.
	- May be run in parallel at the NSG (https://www.nsgportal.org/) or properly configured machines.
	- Saves simulation results in an "outdir", in a subfolder entitled *modeltype*

rankopt.hoc
	- Rank optimized model solutions. 
	- To be used only after startopt.hoc has returned solutions.
	- Based on current model setup and matching solution set.

playopt.hoc
	- Play optimized and ranked solutions of current model setup.
	- startopt.hoc and rankopt.hoc must have returned first.
	- To start playing a solution set, select it by clicking on the corresponding checkbox.
	- Solutions will play from best to worst.
	- To stop at a particular solution, uncheck the corresponding checkbox by clicking on it.
