### `turn` command
```
DESCRIPTION
 
    "turn" rotates the camera about one of the three primary axes,
    centered at the origin.
 
USAGE
 
    turn axis, angle
 
EXAMPLES
 
    turn x, 90
    turn y, 45
 
PYMOL API
 
    cmd.turn(string axis, float angle)
```

### move
```
DESCRIPTION
 
    "move" translates the camera about one of the three primary axes.
 
USAGE
 
    move axis, distance
 
EXAMPLES
 
    move x, 3
    move y, -1
 
PYMOL API
 
    cmd.move(string axis, float distance)
```
### clip
```
DESCRIPTION
 
    "clip" alters the positions of the clipping planes.
 
USAGE
 
    clip mode, distance [, selection [, state ]]
 
ARGUMENTS 
 
    mode = near, far, move, slab, or atoms
 
    distance is a floating point value
 
    selection = atom selection (for mode=atoms only)
 
EXAMPLES
 
    clip near, -5           # moves near plane away from you by 5 A
    clip far, 10            # moves far plane towards you by 10 A
    clip move, -5           # moves the slab away from you by 5 A
    clip slab, 20           # sets slab thickness to 20 A
    clip slab, 10, resi 11  # clip 10 A slab about residue 11
 
    clip atoms, 5, pept     # clip atoms in "pept" with a 5 A buffer
                            # about their current camera positions
 
PYMOL API
 
    cmd.clip(string mode, float distance, string selection, int state)
```
