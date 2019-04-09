# Define crack surfaces for 2D seam crack - Abaqus
To define two crack surfaces for an internal seam crack generated by Abaqus 2D model. The definition of the crack surfaces allow for assigning interaction contact conditions to prevent overlapping of nodes under stress wave excitation. 

# To get started
internal-crack.m is the primary file you will be editing in order to generate a new input for with defined crack surfaces for your 2D Abaqus model.
All other files are helper functions.

## The workflow requirement
1. Create your model in Abaqus CAE
2. Define your crack plane with a set name -> The script will look for these set names therefore it is mandatory to define
3. Apply seam crack to your crack plane -> This will generate duplicate nodes at the same plane
4. Create a job and write the input file -> This will be the file imported into the script for modification
5. Run script to generate crack surfaces and crack contact conditions
6. Import inp file into Abaqus for analysis 

See example code below on the parameters you need to change
```Matlab
input_file = 'model.inp';
output_file = 'model_with_crack.inp';
...
num_cracksets = 1; % This is the number of seam cracks in your model
crackset_prefix = 'crack'; % The crack plane set name defined earlier in your model (i.e. crack1, crack2, ...)
...
instancename = 'mortar-crack-1' % Rename this to your instance name of the model 
```

# Advanced parameters
You can change the contact conditions for your crack near the end of the script code such as friction, crack clearance and interaction definition
```Matlab
friction = 0; % Tangential friction behaviour
crack_clearance = 0; % Initial crack clearance
```

# Limitations
* This Matlab script only works for straight cracks with any slope orientation in a 2D model. 
* It does consider quadrilateral and triangle elements.
* Advanced contact condition and interactions not considered in this script - You will have to modify the 2nd last section of the code.
