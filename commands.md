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

Measure angles:

`angle angle1, atom1, atom2, atom3  # Measures angle between three atoms`

### Creating Animations
Create animations using the mplay and mview commands:

```
mplay          # Starts animation playback
mview store    # Stores the current frame
mview rewind   # Rewinds the animation
```

### Customizing Labels
Add labels to specific atoms or residues:

`label resn ALA and name CA, "ALA"  # Labels alpha carbons of alanine residues`

### Using Scripts
Run a script to automate tasks:

`run /path/to/script.py`

### Example script:

```
load 1abc
show cartoon
color red, chain A
save image.png
```

### Keyboard Shortcuts
- A: Toggle atom labels.
- S: Toggle sticks representation.
- C: Toggle cartoon representation.
- Spacebar: Reset view.

### Create a new object from a selection:

`create new_object, selection`

example:

`create ligand, resn LIG`

### Delete an object:

`delete object_name`

### Rename an object:

`rename old_name, new_name`

### Copy an object:

`copy new_object, old_object`

### Group objects:

`group group_name, object1, object2`

### Transparency:

`set transparency, 0.5  # 0 = opaque, 1 = fully transparent`

### Dashed lines for hydrogen bonds:

`show dashes`

### Display symmetry-related molecules:

`symexp sym, object, cutoff_distance`

example:

`symexp sym, 1abc, 10  # Displays symmetry mates within 10 Å`

### Display non-bonded interactions:

`show nonbonded`

### Display disulfide bonds:

`show disulfides`

### Set the background color:

`bg white  # Options: white, black, gray, etc.`

### Set the field of view:

`set field_of_view, 50  # Adjust the zoom level`

### Set the depth cueing (fog effect):

`set fog, 0.5  # 0 = no fog, 1 = maximum fog`

### Set the lighting:

```
set light_count, 4  # Number of light sources
set specular, 1     # Adjust reflection intensity
```

### Color by element:

`util.cba  # Color by atom (default coloring)`

### Color by hydrophobicity:

`util.cbh  # Color by hydrophobicity`

### Color by charge:

`util.cbc  # Color by charge`

### Color by B-factor (thermal motion):

`spectrum b, selection  # Colors by B-factor values`

### Color by conservation:

`spectrum cons, selection  # Requires conservation data`

### Measure dihedral angles:

`dihedral angle_name, atom1, atom2, atom3, atom4`

### Calculate RMSD between two structures:

`rmsd molecule1, molecule2`

### Calculate surface area:

`get_area selection`

### Calculate electrostatic potential:

`util.propka  # Requires pre-calculated electrostatic data`

### Render high-quality images:

`ray  # Renders the current view`

### Set the resolution for ray tracing:

```
set ray_trace_frames, 1  # High-quality rendering for animations
set ray_trace_gain, 10   # Adjust brightness
```

### Export an image:

`png /path/to/image.png, dpi=300  # Saves as PNG with 300 DPI`

### Export a movie:

```
mplay
mset 1-100  # Sets 100 frames
mray        # Renders all frames
msave /path/to/movie, png  # Saves frames as PNGs
```

### Run a Python script:

`run /path/to/script.py`

### Loop through residues:

`iterate (resi 1-10), print(name, resi, vdw)  # Prints atom names, residue numbers, and VDW radii`

### Customize labels with Python:

`label selection, "Residue %s" % resi`

### List all loaded objects:

`ls`

### help commands

`help commands`

### Reset the view:

`reset`

### Clear the workspace:

`reinitialize  # Clears all objects and settings`

### Set the working directory:

`cd /path/to/directory`

### Hide/show the command line:

`set internal_gui, off  # Hides the command line`

### Customize the GUI:

`set internal_gui_width, 300  # Adjusts the width of the GUI`

### Enable/disable mouse controls:

`set mouse_enabled, 0  # Disables mouse controls`

### Load a plugin:

`plugin load plugin_name`

### Install a plugin:

`plugin install plugin_name`

Example plugins:

- APBS Tools: For electrostatic potential calculations.

- Mutagenesis Wizard: For in silico mutagenesis.

- Movie Maker: For creating animations.

### Color residues by chain:
```
for chain in ["A", "B", "C"]:
    color chain_color, chain
```

### Create a surface for a specific selection:

```
create surface_object, selection
show surface, surface_object
```

### Align multiple structures:

```
for obj in cmd.get_names():
    align obj, reference_object
```

### Center and zoom on a selection:

`zoom selection`

### Display all hydrogen bonds:

`show hbonds`

### Color by secondary structure:

`util.cbss`

### Display all polar contacts:

`show contacts`










