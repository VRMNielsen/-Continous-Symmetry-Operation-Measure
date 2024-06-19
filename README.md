# Continous Symmetry Operation Measure
A program to evaluate the point group symmetry of a coordinating structure.
The program is puplished in association with the following paper in Journal of Physical Chemistry A.

Title:

Authors: 

DOI:


# 2. Description
The program is intended as a tool in coordination chemistry to evaluate the point group symmetry of a coordination complex.
The coordination complex is given as file containing the coordinates and labels for all atoms in the coordination complex. 
The first atom in the series is used to center the complex such that it lies in origo.
Then a set of point groups is manually chosen for evaluation on the complex. 
The evaluation is done by comparing the euclidean distance between all coordinates in the input coordinates with new coordinates generated from the symmetry operations within the point group that is used for evaluation.

An autonomous assignment of the principal axis is performed prior to the evalution. This assures that the input structure is always aligned optimally with the symmetry axis used for evaluation.

The output of the program is the symmetry deviation values provided for each selected symmetry operations, deviation values of individual symmetry operations within each point group, and new coordinate files for each structure that has been generated by the symmetry operations. 

A detailed description is provided in the paper associated with this program: [insert DOI here]

# 3. How to install
The Program is written in the python environment Spyder and it is intended to be used in this or a similar coding environment. 
The program therefore need no formal installation if Spyder is installed: https://www.spyder-ide.org/

When the program is downloaded it is downloaded as a folder containing two python scripts entitled: "CSoM_Program.py" and "CSoM_functions.py" and a folder containing information on all available point groups entitled: "Operations". 

+ "CSoM_Program.py" is the main file and is used to run the program.
+ "CSoM_functions.py" contains all custom functions used by the program.

The "CSoM_Program.py" is opened in a python environment and must always be in the same folders as "CSoM_functions.py" and "Operations".

To run the code the following packages need to be installed: 

+ numpy
+ math
+ re
+ pandas
+ scipy
+ datetime


# 4. How to Use
When the program is open in a python environment, it can be run by inserting the required inputs. Here we go through all inputs as they are written in the program file:

The structure file required to run the program is an .xyz file commonly used and generated with programs such as VESTA: https://jp-minerals.org/vesta/en/download.html. It contains the labels and coordinates of all atoms in the complex
**The central atom in the complex, is the first atom listed.** This is the coordinate that will be used as Origo in the calculations, if a manual coordinate is not selected.

Examples of input files are provided in this recepoire. 

**Inputs for the structure file is required:**
 + mypath: The path to the folder where your structure file is located.
 + all_structure: Select True if all files in the folder is to be analysed. Select False if only selected files are to be analyzed.
 + structures_selected: If all files are not to be analysed write the names of files to be analysed here. e.g. 'filename.xyz'


**Inputs for symmetry operations**
+ point_group_names: provide all pointgroups that are to be used in this format. point_group_names = [pointgroup_C2, pointgroup_D3h, ... ]. In this case the pointgroups C2, and D3h will be evaluated on the coordination file.  
+ if all pointgroups available is to be used, then the following line can be used: point_group_names = [os.path.basename(os.path.join(Path_To_Symmetry_Operations,f)).split('.')[0] for f in os.listdir(Path_To_Symmetry_Operations) if os.path.isfile(os.path.join(Path_To_Symmetry_Operations, f))]

With these inputs the program can be run as intended and we recommend to run all other inputs with their default values. However, some manual changes can be done if so desired. These include manual centering and a deactivaton of the autonoumous assignment of the principle axis:

# 5. Additional Settings

It is not recommended to change the default settings

**Manual inputs for the optimization iterations of the principle axes**

+ N_input_zaxis: Select how many principle axes are to be optimized. The more that are used the more likely the correct global minimum for the principle axis is to be found, but the computational time will increase. Default value is 10
+ N_input_angles: Select how many initial angles that are to be optimized for the xy plane vertical to the principle axis. The more that are used the more likely the correct global minimum for the principle axis is to be found, but the computational time will increase. Default value is 2. We found that generally 10 axes and 2 angles will always find the proper minima.

**Manual inputs for of the principle axes**
+ Manual_Zaxis: Default is True which will run the minimization of principle axis. If this minimization is to be deactivated, this parameter is set to False. Then additional inputs will be needed:
+ Zaxis: The vector for a manual principle axis. The input is an array with the following format np.array([x,y,z])
+ Manual_Angle: Additionally if a manual selection of the angle for the xy-plane is desired this can be selected here but putting in "True". Otherwise the angle is found through minimization with respect to the manual Z axis this is chosen with False.
+ angle: manual selected angle for the xy-plane vertical to the manually selected Zaxis.


**Manual inputs for the centering of the complex, from which the point group analysis is performed**
+ ManualCentering: Default is "False", which means that the centering of the complex will be the first atom listed in the input .xyz file. If "True" is selected, then a manual input for the centering can be used. Here the x0, y0, z0 provide the coordinate for this.

**Possible inclusion of a cutoff of what to include in the point group analysis**
cut_off_distance: False is default, then the file 
cutoff: The cutoff distance selected with respect to the units used in the .xyz file.

# 5. Credits and how to cite




