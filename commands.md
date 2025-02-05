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

### Extract a chain or segment:

`extract new_object, chain A  # Extracts chain A into a new object`

### Split a multi-state object into individual states:

`split_states object_name`

### Combine multiple objects into one:

`combine new_object, object1, object2`

### Remove hydrogens:

`remove hydrogens`

### Remove waters:

`remove solvent`

### Display atomic density:

`show dots`

### Display atomic orbitals:

`show spheres`

### Display atomic labels with custom formatting:

`label selection, "Residue %s, Atom %s" % (resi, name)`

### Display atomic labels with B-factors:

`label selection, "B-factor: %.2f" % b`

### Display atomic labels with charge:

`label selection, "Charge: %.2f" % q`

### Color by custom property:

```
spectrum q, selection  # Colors by atomic charge
spectrum b, selection  # Colors by B-factor
```

### Color by distance from a point:

```
pseudoatom center, pos=[x, y, z]  # Create a pseudoatom at (x, y, z)
distance_to_center, selection, center  # Measure distance to pseudoatom
spectrum any, distance_to_center  # Color by distance
```

### Color by sequence conservation:

```
fetch 1abc, type=conservation  # Requires conservation data
spectrum cons, selection
```

### Color by secondary structure type:

`util.cbss  # Color by secondary structure`

### Measure center of mass:

`get_center_of_mass selection`

### Measure molecular volume:

`get_volume selection`

### Measure solvent-accessible surface area (SASA):

`get_sasa selection`

### Measure buried surface area:

`get_buried_area selection1, selection2`

### Measure electrostatic potential at a point:

`get_property electrostatic_potential, selection`

### Set ray tracing quality:

```
set ray_trace_mode, 1  # Enable ray tracing
set ray_trace_gain, 10  # Adjust brightness
set ray_trace_color, black  # Set background color for ray tracing
```

### Render with shadows:

`set ray_shadows, 1`

### Render with ambient occlusion:

`set ray_ambient_occlusion, 1`

### Render with reflections:

`set ray_reflections, 1`

### Loop through all atoms in a selection:

`iterate selection, print(name, resi, vdw)`

### Loop through all residues in a selection:

`iterate_state 1, selection, print(resi, resn)`

### Create a custom function:

```
def color_by_chain():
    for chain in cmd.get_chains():
        cmd.color("chain_color", f"chain {chain}")
color_by_chain()
```

### Batch process multiple PDB files:

```
import os
for file in os.listdir("/path/to/pdbs"):
    if file.endswith(".pdb"):
        cmd.load(file)
        cmd.show("cartoon")
        cmd.png(f"{file}.png")
        cmd.delete("all")
```

### Add custom text labels:

```
pseudoatom label_pos, pos=[x, y, z]
label label_pos, "Custom Text"
```

### Add arrows:

```
pseudoatom arrow_start, pos=[x1, y1, z1]
pseudoatom arrow_end, pos=[x2, y2, z2]
distance arrow, arrow_start, arrow_end
```

### Add shapes (e.g., spheres, cylinders):

```
cmd.pseudoatom("sphere_center", pos=[x, y, z])
cmd.show("spheres", "sphere_center")
cmd.set("sphere_scale", 5, "sphere_center")  # Adjust sphere size
```

### Create a rotation animation:

```
mset 1-360  # 360 frames
mview store  # Store current view
turn y, 360  # Rotate 360 degrees around the Y-axis
mray         # Render frames
```

### Create a zoom animation:

```
mset 1-100
mview store
zoom selection, 10  # Zoom in
mray
```

### Create a morphing animation:

```
fetch 1abc, async=0
fetch 2def, async=0
super 1abc, 2def
mset 1-100
mview store
morph
mray
```

### APBS Tools for electrostatics:

`plugin load apbs_tools`

### Mutagenesis Wizard:

`plugin load mutagenesis`

### DSSP for secondary structure assignment:

`dssp object_name`

### Load electron density maps:

`load /path/to/map.ccp4`

### Display symmetry mates:

`symexp sym, object, cutoff_distance`

### Display unit cell boundaries:

`show unit_cell`

### Display non-covalent interactions:

`show nonbonded`

### Display hydrogen bonds with custom settings:

```
set dash_gap, 0.5  # Adjust dash spacing
set dash_length, 0.2  # Adjust dash length
```

### Check memory usage:

`print(cmd.get_memory_usage())`

### Optimize performance:

`set defer_builds_mode, 1  # Defer object builds for faster rendering`

### Debug scripts:

```
print(cmd.get_names())  # List all objects
print(cmd.get_chains())  # List all chains
```

### Color all chains differently:

`util.cbc`

### Display all polar contacts:

`show contacts`

### Display all disulfide bonds:

`show disulfides`

### Display all salt bridges:

`show salt_bridges`

### Display all pi-pi interactions:

`show pi_pi`

### Loading and Saving
- `load /path/to/file.pdb` - Load a PDB file.

- `fetch 1abc` - Fetch a structure from the PDB.

- `save /path/to/file.pse` - Save a session.

- `save /path/to/file.png` - Save an image.

- `save /path/to/file.pdb` - Save as a PDB file.

- `reinitialize` - Reset PyMOL to its initial state.

### Navigation
- `zoom selection` - Zoom into a selection.

- `orient selection` - Orient the view to a selection.

- `reset` - Reset the view.

- `turn x, 90` - Rotate 90 degrees around the X-axis.

- `move x, 5` - Move along the X-axis.

- `clip slab, 10` - Set the clipping plane.

### Object Management
- `create new_object, selection` - Create a new object from a selection.

- `delete object_name` - Delete an object.

-`rename old_name, new_name` - Rename an object.

- `copy new_object, old_object` - Copy an object.

- `group group_name, object1, object2` - Group objects.

### Representations
- `show sticks` - Show sticks representation.

- `show spheres` - Show spheres representation.

- `show cartoon` - Show cartoon representation.

- `show surface` - Show molecular surface.

- `show dots` - Show dots representation.

- `show lines` - Show lines representation.

- `show mesh` - Show mesh representation.

- `show ribbon` - Show ribbon representation.

- `show nonbonded` - Show non-bonded interactions.

- `show hydrogen` - Show hydrogen atoms.

### Coloring
- `color red` - Color the entire molecule red.

- `color green, selection` - Color a selection green.

- `util.cba` - Color by atom.

- `util.cbc` - Color by chain.

- `util.cbss` - Color by secondary structure.

- `util.cbh` - Color by hydrophobicity.

- `util.cbq` - Color by charge.

- `spectrum b, selection` - Color by B-factor.

- `spectrum q, selection` - Color by charge.

- `spectrum cons, selection` - Color by conservation.

### Transparency
- `set transparency, 0.5` - Set transparency (0 = opaque, 1 = transparent).

- `set surface_transparency, 0.5` - Set surface transparency.

### Selection Commands
- `select selection_name, selection` - Create a selection.

- `select binding_site, resi 50-60` - Select residues 50-60.

- `select ligand, resn LIG` - Select ligand residues.

- `select backbone, name N+C+CA+O` - Select backbone atoms.

- `select polar, (elem N+O) &! (hydro)` - Select polar atoms.

- `select hydrophobic, (elem C) &! (polar)` - Select hydrophobic atoms.

### Measurement Commands
- `distance dist1, atom1, atom2` - Measure distance.

- `angle angle1, atom1, atom2, atom3` - Measure angle.

- `dihedral dihedral1, atom1, atom2, atom3, atom4` - Measure dihedral angle.

- `get_area selection` - Calculate surface area.

- `get_volume selection` - Calculate volume.

- `get_sasa selection` - Calculate solvent-accessible surface area.

- `get_buried_area selection1, selection2` - Calculate buried surface area.

- `rmsd molecule1, molecule2` - Calculate RMSD.

### Ray Tracing
- `ray` - Render the current view.

- `set ray_trace_mode, 1` - Enable ray tracing.

- `set ray_shadows, 1` - Enable shadows.

- `set ray_ambient_occlusion, 1` - Enable ambient occlusion.

- `set ray_reflections, 1` - Enable reflections.

### Movies and Animations
- `mset 1-100` - Set 100 frames.

- `mview store` - Store the current view.

- `mplay` - Play the animation.

- `mray` - Render all frames.

- `msave /path/to/movie, png` - Save frames as PNGs.

### Symmetry and Unit Cells
- `symexp sym, object, cutoff_distance` - Display symmetry mates.

- `show unit_cell` - Display unit cell boundaries.

### Surfaces and Maps
- `show surface` - Show molecular surface.

- `load /path/to/map.ccp4` - Load an electron density map.

- `isomesh mesh_name, map_name, level` - Create an isomesh.

- `isosurface surface_name, map_name, level` - Create an isosurface.

### Scripting Commands
- `run /path/to/script.py` - Run a Python script.

- `iterate selection, print(name, resi, vdw)` - Loop through atoms.

- `iterate_state 1, selection, print(resi, resn)` - Loop through residues.

- `cmd.get_names()` - List all objects.

- `cmd.get_chains()` - List all chains.

- `cmd.get_atom_coords(selection)` - Get atom coordinates.

### Plugins and Extensions
- `plugin load apbs_tools` - Load APBS Tools for electrostatics.

- `plugin load mutagenesis` - Load Mutagenesis Wizard.

- `plugin load movie_maker` - Load Movie Maker.

- `plugin load dssp` - Load DSSP for secondary structure assignment.

### Utility Commands
- `help commands` - List all commands.

- `help command_name` - Get help for a specific command.

- `cd /path/to/directory` - Change the working directory.

- `ls` - List all loaded objects.

- `print(cmd.get_memory_usage())` - Check memory usage.

### Niche Commands
- `pseudoatom pseudo_name, pos=[x, y, z]` - Create a pseudoatom.

- `label selection, "Residue %s" % resi` - Add a label.

- `show disulfides` - Show disulfide bonds.

- `show salt_bridges` - Show salt bridges.

- `show pi_pi` - Show pi-pi interactions.

- `show cation_pi` - Show cation-pi interactions.

### Debugging and Optimization
- `set defer_builds_mode, 1` - Defer object builds for faster rendering.

- `set cache_frames, 1` - Cache frames for faster playback.

- `set max_threads, 4` - Set the maximum number of threads.

### One-Liners for Power Users
- `util.cbc` - Color all chains differently.

- `util.cbss` - Color by secondary structure.

- `util.cbh` - Color by hydrophobicity.

- `util.cbq` - Color by charge.

- `util.propka` - Calculate pKa values.

- `util.ray_shadows` - Enable shadows.

### Color by Chain
```
for chain in cmd.get_chains():
    cmd.color("chain_color", f"chain {chain}")
```

### Loop Through Residues
```
for resi in range(1, 100):
    cmd.select(f"residue_{resi}", f"resi {resi}")
    cmd.color("red", f"residue_{resi}")
```

### Batch Process PDB Files
```
import os
for file in os.listdir("/path/to/pdbs"):
    if file.endswith(".pdb"):
        cmd.load(file)
        cmd.show("cartoon")
        cmd.png(f"{file}.png")
        cmd.delete("all")
```

