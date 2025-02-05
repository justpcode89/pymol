## Pymol commands

### Fetch and delete a structure from RCSB:
`fetch 1a1e`

`delete 1a1e`

### Load a local file:
`load <file_name>.pdb`

### Cartoon: Represents secondary structures such as alpha helices and beta sheets.
`show cartoon`

### Sticks: Displays the structure as sticks, useful for small molecules.
`show sticks`

### Surface: Shows the molecular surface.
`show surface`

### You can change the color of the molecular structure to improve visualization.
`color red, chain A`

### Selections allow you to specify subsets of atoms for visualization or manipulation.
`select my_selection, chain A and resi 50-100`

### Moving and Rotating
You can move and rotate structures using the mouse:
- Left Button: Rotate the structure.
- Middle Button: Translate the structure.
- Right Button: Zoom in and out.

### Aligning Structures
To align one structure to another, use the align command.
`align target_object, mobile_object`

### Saving Images
You can save images of your molecular structures using the png command.
`png filename.png`

### Scripting in PyMOL
PyMOL supports scripting in Python. You can automate tasks and create custom visualizations by writing Python scripts.

Example Script
Here's a simple example of a PyMOL script:
```
# Load a structure
load 1a1e.pdb

# Show cartoon representation
show cartoon

# Color the structure
color blue

# Save an image
png structure.png
```







