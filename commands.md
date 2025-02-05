## Pymol commands

### Fetch and delete a structure from RCSB:
`fetch 1a1e`

`delete 1a1e`

### Load a local file:
`load <file_name>.pdb`

### Cartoon: Represents and hide secondary structures such as alpha helices and beta sheets.
`show cartoon`

`hide cartoon`

### Sticks: Displays and hide the structure as sticks, useful for small molecules.
`show sticks`

`hide sticks`

### Surface: Shows and hide the molecular surface.
`show surface`

`hide surface`

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
Save this script as a .pml file and run it in PyMOL using:

`@script.pml`

### Selecting Atoms and Residues
Select specific atoms or residues using the `select` command:

```
select resn ALA  # Selects all alanine residues
select chain A   # Selects all atoms in chain A
select name CA   # Selects all alpha carbons
```

### Changing Representations
Change the molecular representation using the `show` command:

```
show sticks    # Displays sticks
show spheres   # Displays spheres
show surface   # Displays molecular surface
show cartoon   # Displays secondary structure as a cartoon
```

### Coloring Molecules
Color molecules using the `color` command:
```
color red       # Colors the entire molecule red
color green, resn ALA  # Colors alanine residues green
color blue, chain A    # Colors chain A blue
```

### Save your session to a file:

`save /path/to/session.pse`

### To load a saved session:

`load /path/to/session.pse`

### Displaying Secondary Structures
Use the `cartoon` representation to highlight secondary structures:
```
show cartoon
color orange, ss h  # Colors helices orange
color yellow, ss s  # Colors sheets yellow
```

### Creating Surfaces
Generate a molecular surface:
```
show surface
set surface_color, white  # Sets surface color to white
```

### Highlighting Specific Regions
Highlight specific regions using the `select` and `color` commands:

```
select binding_site, resi 50-60  # Selects residues 50-60
color red, binding_site          # Colors the binding site red
```
### Aligning Structures
Align two structures using the `align` command:
`align molecule1, molecule2`

### Measuring Distances and Angles
Measure distances between atoms:

`distance dist1, atom1, atom2  # Measures distance between atom1 and atom2`














