## view Commands

### `turn`
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

### `move`
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
### `clip`
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

### `rock`
```
DESCRIPTION
 
    "rock" toggles Y axis rocking.
 
USAGE
 
    rock
 
PYMOL API
 
    cmd.rock()
```

### `show`
```
DESCRIPTION
 
    "show" turns on representations for objects and selections.
 
USAGE
 
    show [ representation [, selection ]]
 
ARGUMENTS
 
    representation = lines, spheres, mesh, ribbon, cartoon, sticks,
       dots, surface, labels, extent, nonbonded, nb_spheres, slice,
       extent, slice, dashes, angles, dihedrals, cgo, cell, callback,
       or everything
 
    selection = string: a selection-expression or name-pattern
 
NOTES
 
    With no arguments, "show" alone turns on lines for all bonds and
    nonbonded for all atoms in all molecular objects.
 
EXAMPLES
 
    show
    show ribbon
    show lines, (name CA+C+N)
```

### `hide`
```
DESCRIPTION
 
    "hide" turns off atom and bond representations.
 
 
USAGE
 
    hide [ representation [, selection ]]
 
ARGUMENTS
 
    representation = lines, spheres, mesh, ribbon, cartoon,
       sticks, dots, surface, labels, extent, nonbonded, nb_spheres,
       slice, extent, slice, dashes, angles, dihedrals, cgo, cell, callback, 
       or everything
 
    selection = string: a selection-expression or name-pattern
 
EXAMPLES
 
    hide lines, all
    hide ribbon
 
PYMOL API
 
    cmd.hide(string representation, string selection)
```

### `enable`
```
DESCRIPTION
 
    "enable" turns on display of one or more objects and/or selections.
 
USAGE
 
    enable name
 
ARGUMENTS    
 
    name = name-pattern or selection. 
 
NOTES
 
    If name matches a selection name, then selection indicator dots
    are shown for atoms in that selection.  If name is a
    selection-expression, then all objects with atoms in that
    selection are enabled.
 
    For an object's content to be displayed in the 3D viewer, the
    object must be enabled AND at least one of the available
    representations must be shown.
 
PYMOL API
 
    cmd.enable(string object-name)
 
EXAMPLES
 
    enable target_protein  # enables the target_protein object
 
    enable 1dn2.*   # enables all entities starting with 1dn2.
 
    enable *lig     # enables all entities ending with lig
```

### `disable`

```
DESCRIPTION
 
    "disable" turns off display of one or more objects and/or selections.
 
USAGE
 
    disable name
 
ARGUMENTS    
 
    name = name-pattern or selection.
 
PYMOL API
 
    cmd.disable(string name) 
```

### `reset`
```
DESCRIPTION
 
    "reset" restores the rotation matrix to identity, sets the origin
    to the center of mass (approx.) and zooms the window and clipping
    planes to cover all objects.  Alternatively, it can reset object
    matrices.
 
USAGE
 
    reset [ object ]
 
PYMOL API
 
    cmd.reset()

```

### `refresh`
```
DESCRIPTION
 
    "reset" restores the rotation matrix to identity, sets the origin
    to the center of mass (approx.) and zooms the window and clipping
    planes to cover all objects.  Alternatively, it can reset object
    matrices.
 
USAGE
 
    reset [ object ]
 
PYMOL API
 
    cmd.reset()
 
PyMOL>help refresh
 
DESCRIPTION
 
    "refresh" causes the scene to be redrawn as soon as the operating
    system allows it to be done.
 
USAGE
 
    refresh
 
PYMOL API
 
    cmd.refresh()
```

### `rebuild`

```
DESCRIPTION
 
    "rebuild" forces PyMOL to recreate geometric objects in
    case any of them have gone out of sync.
 
USAGE
 
    rebuild [selection [, representation ]]
 
ARGUMENTS
 
    selection = string {default: all}
 
    representation = string: {default: everything}
 
PYMOL API
 
    cmd.rebuild(string selection, string representation)
```

### `reinitialize`

```
DESCRIPTION
 
    "reinitialize" reinitializes the program by deleting all objects
    and restoring the default program settings.
 
USAGE
 
    reinitialize
```

### `zoom`
```
DESCRIPTION
 
    "zoom" scales and translates the window and the origin to cover the
    atom selection.
 
USAGE
 
    zoom [ selection [, buffer [, state [, complete [, animate ]]]]]
 
EXAMPLES
 
    zoom 
    zoom complete=1
    zoom 142/, animate=3
    zoom (chain A)
 
ARGUMENTS
 
    selection = string: selection-expression or name pattern {default: all}
 
    buffer = float: distance  {default: 0}
 
    state = 0: uses all coordinate states {default}
 
    state = -1: uses only coordinates for the current state
 
    state > 0: uses coordinates for a specific state
 
    complete = 0 or 1: will insure no atoms centers are clipped
 
    animate < 0: uses the default animation duration
 
    animate = 0: no animation
 
    animate > 0: animates using the provided duration in seconds
 
PYMOL API
 
    cmd.zoom(string selection, float buffer, int state, int complete,
             int animate)
 
NOTES
 
    The zoom command normally tries to guess an optimal zoom level for
    visualization, balancing closeness against occasional clipping of
    atoms out of the field of view.  You can change this behavior by
    setting the complete option to 1, which will guarantee that the
    atom positions for the entire selection will fit in the field of
    an orthoscopic view.
 
    To absolutely prevent clipping, you may also need to add an
    additional buffer (typically 2 A) to account for graphical
    representations which extend beyond the atom coordinates.
```

### `origin`
```
DESCRIPTION
 
    "origin" sets the center of rotation about a selection.  If an
    object name is specified, it can be used to set the center of
    rotation for the object (for use in animation and editing).
 
USAGE
 
    origin [ selection [, object [,position, [, state ]]]]
 
ARGUMENTS
 
    selection = string: selection-expression or name-list {default: (all)}
 
    state = 0 (default) use all coordinate states
 
    state = -1 use only coordinates for the current state
 
    state > 0  use coordinates for a specific state
 
EXAMPLES
 
    origin chain A
 
    origin position=[1.0,2.0,3.0]
 
PYMOL API
 
    cmd.origin(string object-or-selection)
```

### `orient`
```
DESCRIPTION
 
    "orient" aligns the principal components of the atoms in the
    selection with the XYZ axes.  
 
USAGE
 
    orient [ selection [, state [, animate ]]]
 
ARGUMENTS
 
    selection = a selection-expression or name-pattern {default: (all)}
 
    state = 0: use all coordinate states {default}
 
    state = -1: uses only coordinates for the current state
 
    state > 0: uses coordinates for a specific state
 
EXAMPLES
 
    orient organic
 
NOTES
 
    The function is similar to the orient command in X-PLOR.
 
PYMOL API
 
    cmd.orient(string object-or-selection, int state, float animate)
```

### `view`
```
DESCRIPTION
 
    "view" saves and restore camera views.
 
USAGE
 
    view key [, action [, animate]]
 
ARGUMENTS
 
    key = string or *
 
    action = store, recall, clear: {default: recall}
 
NOTES
 
    Views F1 through F12 are automatically bound to function keys
    provided that "set_key" has not been used to redefine the
    behaviour of the respective key, and that a "scene" has not been
    defined for that key.
 
EXAMPLES
 
    view 0, store
    view 0
 
PYMOL API
 
    cmd.view(string key, string action)
```

### `get_view`
```
DESCRIPTION
 
    "get_view" returns and optionally prints out the current view
    information in a format which can be embedded into a command
    script and can be used in subsequent calls to "set_view".
 
    If a log file is currently open, get_view will not write the view
    matrix to the screen unless the "output" parameter is 2.
 
USAGE
 
    get_view [output]
 
ARGUMENTS
 
    output = 0: output matrix to screen
 
    output = 1: do not Output matrix to screen
 
    output = 2: force output to screen even if log file is open
 
    output = 3: return formatted string instead of a list
 
NOTES
 
    Contents of the view matrix:
 
    * 0  -  8: column-major 3x3 matrix which rotates model space to camera space
 
    * 9  - 11: origin of rotation relative to camera (in camera space)
 
    * 12 - 14: origin of rotation (in model space)
 
    * 15: front plane distance from the camera
 
    * 16: rear plane distance from the camera
 
    * 17: orthoscopic flag (+/-) and field of view (if abs(value) > 1)
 
    The camera always looks down -Z with its +X left and its +Y down.
 
    Therefore, in the default view, model +X is to the observer's
    right, +Y is upward, and +Z points toward the observer.
 
PYMOL API
 
    cmd.get_view(output=1, quiet=1)
```

### `set_view`
```
DESCRIPTION
 
    "set_view" sets viewing information for the current scene,
    including the rotation matrix, position, origin of rotation,
    clipping planes, and the orthoscopic flag.
 
USAGE
 
    set_view [ view ] 
 
EXAMPLE
 
    set_view (\
        0.999876618,   -0.000452542,   -0.015699286,\
        0.000446742,    0.999999821,   -0.000372844,\
        0.015699454,    0.000365782,    0.999876678,\
        0.000000000,    0.000000000, -150.258514404,\
        11.842411041,   20.648729324,    8.775371552,\
        118.464958191,  182.052062988,    0.000000000 )
 
PYMOL API
 
    cmd.set_view(string-or-sequence view)  
```

## movies commands

### `mplay`

```
DESCRIPTION
 
    "mplay" starts the movie.
 
USAGE
 
    mplay
 
PYMOL API
 
    cmd.mplay()
```

### `mstop`
```
DESCRIPTION
 
    "mstop" stops playing of the movie.
 
USAGE
 
    mstop
```

### `mset`
```
DESCRIPTION
 
    "mset" sets up a relationship between molecular states and movie
    frames.  This makes it possible to control which states are shown
    in which frame.
 
USAGE
 
    mset specification [ ,frame ]
 
PYMOL API
 
    cmd.mset( string specification [, int frame] )
 
EXAMPLES
 
    # simplest case, one state -> one frame
 
    mset 1
 
    # ten frames, all corresponding to state 1
 
    mset 1 x10     
 
    # the first thirty frames are state 1
    # the next 15 frames pass through states 1-15
    # the next 30 frames are of state 15
    # the next 15 frames iterate back to state 1
 
    mset 1 x30 1 -15 15 x30 15 -1
```

### `mdo`
```
DESCRIPTION
 
    "mdo" defines (or redefines) the command-line operations
    associated with a particular movie frame.  These "generalized
    movie commands" will be executed every time the numbered frame is
    played.
 
USAGE
 
    mdo frame: command
 
PYMOL API
 
    cmd.mdo( int frame, string command )
 
EXAMPLE
 
    // Creates a single frame movie involving a rotation about X and Y
 
    load test.pdb
    mset 1
    mdo 1, turn x,5; turn y,5;
    mplay
 
NOTES
 
 These commands are usually created
    by a PyMOL utility program (such as movie.rock).  Command can
    actually contain several commands separated by semicolons ';'
 
    The "mset" command must first be used to define the movie before
    "mdo" statements will have any effect.  Redefinition of the movie
    clears any existing mdo statements.
```

### `mpng`
```
DESCRIPTION
 
    "mpng" writes movie frames as a series of numbered png files.
 
USAGE
 
    mpng prefix [, first [, last [, preserve [, modal [, mode [, quiet
        [, width [, height ]]]]]]]]
 
ARGUMENTS
 
    prefix = string: filename prefix for saved images -- output files
    will be numbered and end in ".png"
 
    first = integer: starting frame {default: 0 (first frame)}
 
    last = integer: last frame {default: 0 (last frame)}
 
    preserve = 0/1: Only write non-existing files {default: 0}
 
    modal = integer: will frames be rendered with a modal draw loop
 
    mode = int: 2=ray, 1=draw, 0=normal {default: -1, check
    ray_trace_frames or draw_frames}
 
    width = int: width in pixels {default: current viewport}
 
    height = int: height in pixels {default: current viewport}
 
NOTES
 
    If the "ray_trace_frames" variable is non-zero, then the frames
    will be ray-traced.  Note that this can take many hours for a long
    movie with complex content displayed.
 
    Also, be sure to avoid setting "cache_frames" when rendering a
    long movie to avoid running out of memory.
 
    Arguments "first" and "last" can be used to specify an inclusive
    interval over which to render frames.  Thus, you can write a smart
    Python program that will automatically distribute rendering over a
    cluster of workstations.  If these options are left at zero, then
    the entire movie will be rendered.
 
PYMOL API
 
    cmd.mpng(string prefix, int first, int last)
```

### `mmatrix`
```
DESCRIPTION
 
    "mmatrix" sets up a matrix to be used for the first frame of the movie.
 
USAGE
 
    mmatrix action
 
ARGUMENTS
 
    action = clear, store, or recall
 
NOTES
 
    This command ensures that the movie always starts from the same
    camera view.
 
    "mmatrix" should not be used when controlling the camera using
    "mview".
 
PYMOL API
 
    cmd.mmatrix( string action )
 
EXAMPLES
 
    mmatrix store
```

### `frame`
```
DESCRIPTION
 
    "frame" sets the viewer to the indicated movie frame.
 
USAGE
 
    frame frame
 
ARGUMENTS
 
    frame = integer: frame number to display
 
EXAMPLE
 
    frame 10
 
PYMOL API
 
    cmd.frame( int frame_number )
 
NOTES
 
    Frame numbers are 1-based.
```

### `rewind`
```
DESCRIPTION
 
    "rewind" goes to the beginning of the movie.
 
USAGE
 
    rewind
 
PYMOL API
 
    cmd.rewind()
```

### `middle`
```
DESCRIPTION
 
    "middle" goes to the middle of the movie.
 
USAGE
 
    middle
 
PYMOL API
 
    cmd.middle()
```

### `ending`
```
DESCRIPTION
 
    "ending" goes to the end of the movie.
 
USAGE
 
    ending
 
PYMOL API
 
    cmd.ending()
```

### `forward`

```
DESCRIPTION
 
    "forward" moves the movie one frame forward.
 
USAGE
 
    forward
 
PYMOL API
 
    cmd.forward()
```

### `backward`
```
DESCRIPTION
 
    "backward" moves the movie back one frame.
 
USAGE
 
    backward
 
PYMOL API
 
    cmd.backward()
```

## imaging commands
