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

### `png`
```
DESCRIPTION
 
    "png" saves a PNG format image file of the current display.
 
USAGE
 
    png filename [, width [, height [, dpi [, ray]]]]
 
ARGUMENTS
 
    filename = string: file path to be written
 
    width = integer or string: width in pixels (without units), inches (in)
    or centimeters (cm). If unit suffix is given, dpi argument is required
    as well. If only one of width or height is given, the aspect ratio of
    the viewport is preserved. {default: 0 (current)}
 
    height = integer or string: height (see width) {default: 0 (current)}
 
    dpi = float: dots-per-inch {default -1.0 (unspecified)}
 
    ray = 0 or 1: should ray be run first {default: 0 (no)}
 
EXAMPLES
 
    png image.png
    png image.png, dpi=300
    png image.png, 10cm, dpi=300, ray=1
 
NOTES
 
    PNG is the only image format supported by PyMOL.
 
SEE ALSO
 
    mpng, save
 
PYMOL API
 
    cmd.png(string filename, int width, int height, float dpi,
            int ray, int quiet)
 
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

## ray tracing commands

### `ray`
```
DESCRIPTION
 
    "ray" creates a ray-traced image of the current frame. This
    can take some time (up to several minutes, depending on image
    complexity).
 
USAGE
 
    ray [width [,height [,antialias [,angle [,shift [,renderer [,quiet
        [,async ]]]]]]]]]
 
ARGUMENTS
 
    width = integer {default: 0 (current)}
 
    height = integer {default: 0 (current)}
 
    antialias = integer {default: -1 (use antialias setting)}
 
    angle = float: y-axis rotation for stereo image generation
    {default: 0.0}
 
    shift = float: x-axis translation for stereo image generation
    {default: 0.0}
 
    renderer = -1, 0, 1, or 2: respectively, default, built-in,
    pov-ray, or dry-run {default: 0}
 
    async = 0 or 1: should rendering be done in a background thread?
 
EXAMPLES
 
    ray
    ray 1024,768
    ray renderer=2
 
NOTES
 
    Default width and height are taken from the current viewpoint. If
    one is specified but not the other, then the missing value is
    scaled so as to preserve the current aspect ratio.
 
    angle and shift can be used to generate matched stereo pairs
 
    renderer = 1 uses PovRay.  This is Unix-only and you must have
        "povray" in your path.  It utilizes two two temporary files:
        "tmp_pymol.pov" and "tmp_pymol.png".
 
    See "help faster" for optimization tips with the builtin renderer.
    See "help povray" for how to use PovRay instead of PyMOL's
    built-in ray-tracing engine.
 
PYMOL API
 
    cmd.ray(int width, int height, int antialias, float angle,
            float shift, int renderer, int quiet, int async)
SEE ALSO
 
    draw, png, save
```

## MAPS commands

### `isomesh`
```
DESCRIPTION
 
    "isomesh" creates a mesh isosurface object from a map object.
 
USAGE
 
    isomesh name, map, level [, selection [, buffer [, state [, carve ]]]]
 
ARGUMENTS
 
    name = the name for the new mesh isosurface object.
 
    map = the name of the map object to use for computing the mesh.
 
    level = the contour level.
 
    selection = an atom selection about which to display the mesh with
        an additional "buffer" (if provided).
 
    state = the state into which the object should be loaded (default=1)
        (set state=0 to append new mesh as a new state)
 
    carve = a radius about each atom in the selection for which to
        include density. If "carve" is not provided, then the whole
        brick is displayed.
 
NOTES
 
    If the mesh object already exists, then the new mesh will be
    appended onto the object as a new state (unless you indicate a state).
 
    state > 0: specific state
    state = 0: all states
    state = -1: current state
 
    source_state > 0: specific state
    source_state = 0: include all states starting with 0
    source_state = -1: current state
    source_state = -2: last state in map
 
SEE ALSO
 
    isodot, load
```

### `isodot`
```
DESCRIPTION
 
    "isodot" creates a dot isosurface object from a map object.
 
USAGE
 
    isodot name, map [, level [, selection [, buffer [, state
        [, carve [, source_state [, quiet ]]]]]]]
 
ARGUMENTS
 
    map = the name of the map object to use.
 
    level = the contour level.
 
    selection = an atom selection about which to display the mesh with
        an additional "buffer" (if provided).
 
NOTES
 
    If the dot isosurface object already exists, then the new dots will
    be appended onto the object as a new state.
```

## display commands

### `cls`
```
DESCRIPTION
 
    "cls" clears the output buffer.
 
USAGE
 
    cls
```

### `viewport`

```
DESCRIPTION
 
    "viewport" changes the size of the graphics display area.
 
USAGE
 
    viewport width, height
 
PYMOL API
 
    cmd.viewport(int width, int height)
```

## selections commands

### `select`
```
DESCRIPTION
 
    "select" creates a named atom selection from a
    selection-expression.
 
USAGE
 
    select name, selection [, enable [, quiet [, merge [, state [, domain ]]]]]
 
ARGUMENTS
 
    name = a unique name for the selection
 
    selection = a selection-expression
 
NOTES
 
    If a selection-expression with explicit surrounding parethenses is
    provided as the first argument, then the default selection name
    is used as the name argument.
 
EXAMPLES 
 
    select chA, chain A
    select ( resn HIS )
    select near142, resi 142 around 5
 
PYMOL API
 
    cmd.select(string name, string selection)
 
```

### `mask`

```
DESCRIPTION
 
    "mask" makes it impossible to select the indicated atoms using the
    mouse.  This is useful when you are working with one molecule in
    front of another and wish to avoid accidentally selecting atoms in
    the background.
 
USAGE
 
    mask (selection)
 
PYMOL API
 
    cmd.mask( string selection="(all)" )
 
SEE ALSO
 
    unmask, protect, deprotect, mouse
```

### `unmask`

```
DESCRIPTION
 
    "unmask" reverses the effect of "mask" on the indicated atoms.
 
PYMOL API
 
    cmd.unmask( string selection="(all)" )
 
USAGE
 
    unmask (selection)
 
SEE ALSO
 
    mask, protect, deprotect, mouse
```

## settings commands

### `set`

```
DESCRIPTION
 
    "set" changes global, object, object-state, or per-atom settings.
 
USAGE
 
    set name [,value [,selection [,state ]]]
 
ARGUMENTS
 
    name = string: setting name
 
    value = string: a setting value {default: 1}
 
    selection = string: name-pattern or selection-expression
    {default:'' (global)}
 
    state = a state number {default: 0 (per-object setting)}
 
EXAMPLES
 
    set orthoscopic
 
    set line_width, 3
 
    set surface_color, white, 1hpv
 
    set sphere_scale, 0.5, elem C
 
NOTES
 
    The default behavior (with a blank selection) is global.  If the
    selection is "all", then the setting entry in each individual
    object will be changed.  Likewise, for a given object, if state is
    zero, then the object setting will be modified.  Otherwise, the
    setting for the indicated state within the object will be
    modified.
 
    If a selection is provided as opposed to an object name, then the
    atomic setting entries are modified.
 
    The following per-atom settings are currently implemented.  Others
    may seem to be recognized but will have no effect when set on a
    per-atom basis.
 
    * sphere_color
    * surface_color
    * mesh_color
    * label_color
    * dot_color
    * cartoon_color
    * ribbon_color
    * transparency (for surfaces)
    * sphere_transparency
 
    Note that if you attempt to use the "set" command with a per-bond
    setting over a selection of atoms, the setting change will appear
    to take, but no change will be observed.  Please use the
    "set_bond" command for per-bond settings.
 
 
PYMOL API
 
    cmd.set(string name, string value, string selection, int state,
            int updates, int quiet)
 
SEE ALSO
 
    get, set_bond
 
```

### `button`

```
DESCRIPTION
 
    "button" can be used to redefine what the mouse buttons do.
 
USAGE
 
    button button, modifier, action
 
ARGUMENTS
 
    button = left, middle, right, wheel, double_left, double_middle,
        double_right, single_left, single_middle, or single_right
 
    modifiers = None, Shft, Ctrl, CtSh, CtAl, CtAl, CtAS, 
 
    actions = None, Rota, Move, MovZ, Slab, +Box, -Box, Clip, MovS,
        +/-, PkAt, Pk1, MvSZ, Sele, Orig, Menu, PkAt, Pk1 RotO, MovO,
        MvOZ, MovA, PkAt, PkTB, MvSZ MvAZ, DrgM, RotZ, PkBd, ClpN,
        ClpF
 
NOTES
 
   Changes made using the button command are easily overridden when
   the user iterates through the mouse modes.  This behavior needs to
   be changed.
 
   Obsolete actions: lb, mb, rb, +lb, +mb, +rb, +lbX, -lbX,
 
   Unsupported, Internal, or Future Actions: RotD, MovD, MvDZ, RotF,
    MovF, MvFZ, TorF, RotV, MovV, MvVZ, DgMZ, DgRT
 
PYMOL API
 
    cmd.button(string button, string modifier, string action)
 
SEE ALSO
 
    config_mouse
```

## atoms commands

### `alter`
```
DESCRIPTION
 
    "alter" changes atomic properties using an expression evaluated
    within a temporary namespace for each atom.
 
USAGE
 
    alter selection, expression
 
EXAMPLES
 
    alter chain A, chain='B'
    alter all, resi=str(int(resi)+100)
    sort
 
NOTES
 
    Symbols defined (* = read only):
 
    name, resn, resi, resv, chain, segi, elem, alt, q, b, vdw, type,
    partial_charge, formal_charge, elec_radius, text_type, label, 
    numeric_type, model*, state*, index*, ID, rank, color, ss,
    cartoon, flags
 
    All strings must be explicitly quoted.  This operation typically
    takes several seconds per thousand atoms altered.  
 
    You may need to issue a "rebuild" in order to update associated
    representations.
 
    WARNING: You should always issue a "sort" command on an object
    after modifying any property which might affect canonical atom
    ordering (names, chains, etc.).  Failure to do so will confound
    subsequent "create" and "byres" operations.  
 
SEE ALSO
 
    alter_state, iterate, iterate_state, sort
```

### `alter_state`
```
DESCRIPTION
 
    "alter_state" changes atom coordinates and flags over a particular
    state and selection using the Python evaluator with a temporary
    namespace for each atomic coordinate.
 
USAGE
 
    alter_state state, selection, expression
 
EXAMPLES
 
    alter_state 1, all, x=x+5
    rebuild
 
NOTES
 
    By default, most of the symbols from "alter" are available for use
    on a read-only basis.  
 
    It is usually necessary to "rebuild" representations once your
    alterations are complete.
 
SEE ALSO
 
    iterate_state, alter, iterate
```
## editing commands

### `create`
```
DESCRIPTION
 
    "create" creates a new molecule object from a selection.  It can
    also be used to create states in an existing object.
 
USAGE
 
    create name, selection [,source_state [,target_state ] ]
 
ARGUMENTS
 
    name = string: name of object to create or modify
 
    selection = string: atoms to include in the new object
 
    source_state = integer: {default: 0 -- copy all states}
 
    target_state = integer: -1 appends after last state {default: 0}
 
PYMOL API
 
    cmd.create(string name, string selection, int state,
               int target_state, int discrete)
 
NOTES
 
    If the source and target states are zero (default), then all
    states will be copied.  Otherwise, only the indicated states will
    be copied.
 
SEE ALSO
 
    load, copy, extract
```

### `replace`
```
DESCRIPTION
 
    "replace" replaces the picked atom with a new atom.
 
USAGE
 
    replace element, geometry, valence [, h_fill [, name ]]
 
NOTES
 
    Immature functionality. See code for details.
 
PYMOL API
 
    cmd.replace(string element, int geometry, int valence, int h_fill,
                string name)
 
SEE ALSO
 
    remove, attach, fuse, bond, unbond
```

### `remove`

```
DESCRIPTION
 
    "remove" eleminates the atoms in a selection from their respective
    molecular objects.
 
USAGE
 
    remove selection
 
EXAMPLES
 
    remove resi 124 
 
PYMOL API
 
    cmd.remove( string selection )
 
SEE ALSO
 
    delete
```

### `h_fill`
```
DESCRIPTION
 
    "h_fill" removes and replaces hydrogens on the atom or bond picked
    for editing.
 
USAGE
 
    h_fill
 
NOTES
 
    This is useful for fixing hydrogens after changing bond valences.
 
PYMOL API
 
    cmd.h_fill()
 
SEE ALSO
 
    edit, cycle_valence, h_add
```

### `remove_picked`
```
DESCRIPTION
 
    "remove_picked" removes the atom or bond currently picked for
    editing.
 
USAGE
 
    remove_picked [ hydrogens ]
 
NOTES
 
    This function is usually connected to the
    DELETE key and "CTRL-D".
 
    By default, attached hydrogens will also be deleted unless
    hydrogen-flag is zero.
 
PYMOL API
 
    cmd.remove_picked(integer hydrogens)
 
SEE ALSO
 
    attach, replace
```

### `edit`

```
DESCRIPTION
 
    "edit" picks atoms or a bond for editing.
 
USAGE
 
    edit selection1 [, selection2 [, selection3 [, selection4 [, pkresi [, pkbond ]]]]] 
 
NOTES
 
    If only one selection is provided, an atom is picked.
 
    If two selections are provided, the bond between them
    is picked (by default, if one exists).
 
PYMOL API
 
    cmd.edit(string selection1, string selection2,
             string selection3, string selection4,
             int pkresi, int pkbond, int quiet)
 
SEE ALSO
 
    unpick, remove_picked, cycle_valence, torsion
 
```

### `bond`
```
DESCRIPTION
 
    "bond" creates a new bond between two selections, each of which
    should contain one atom.
 
USAGE
 
    bond [atom1, atom2 [,order]]
 
ARGUMENTS
 
    atom1 = str: Atom selection of first atom {default: pk1}
 
    atom2 = str: Atom selection of second atom {default: pk2}
 
    order = int: Bond order {default: 1}
 
    symop = str: Symmetry operation code for second atom (e.g. "1_555")
 
NOTES
 
    The atoms must both be within the same object.
 
SEE ALSO
 
    unbond, fuse, attach, replace, remove_picked
```

### `unbond`

```
DESCRIPTION
 
    "unbond" removes all bonds between two selections.
 
USAGE
 
    unbond atom1,atom2
 
ARGUMENTS
 
    atom1 = string {default: (pk1)}
 
    atom2 = string {default: (pk2)}
 
PYMOL API
 
    cmd.unbond(selection atom1, selection atom2)
 
SEE ALSO
 
    bond, fuse, remove_picked, attach, detach, replace
```

### `h_add`
```
DESCRIPTION
 
    "h_add" adds hydrogens onto a molecule based on current valences.
 
USAGE
 
    h_add [ selection [, state ]]
 
ARGUMENTS
 
    selection = string {default: (all)}
 
    state = int {default: 0 (all states)}
 
NOTES
 
    Because PDB files do not normally contain bond valences for
    ligands and other nonstandard components, it may be necessary to
    manually correct ligand conformations before adding hydrogens.
 
SEE ALSO
 
    h_fill
```

### `fuse`

```
DESCRIPTION
 
    "fuse" joins two objects into one by forming a bond.  A copy of
    the object containing the first atom is moved so as to form an
    approximately resonable bond with the second, and that copy is
    then merged with the first object.
 
USAGE
 
    fuse [ selection1 [, selection2 [, mode [, recolor [, move ]]]]]
 
ARGUMENTS
 
    selection1 = str: single atom selection (will be copied to object 2)
 
    selection2 = str: single atom selection
 
    mode = int: {default: 0}
      3: don't move and don't create a bond, just combine into single object
 
    recolor = bool: recolor C atoms to match target {default: 1}
 
    move = bool: {default: 1}
 
NOTES
 
    Each selection must include a single atom in each object.
    The atoms can both be hydrogens, in which case they are
    eliminated, or they can both be non-hydrogens, in which
    case a bond is formed between the two atoms.
 
SEE ALSO
 
    bond, unbond, attach, replace, fuse, remove_picked
```

### `undo`
```
DESCRIPTION
 
    "undo" restores the previous conformation of the object currently
    being edited.
 
USAGE
 
    undo
 
SEE ALSO
 
    redo, push_undo
```

### `redo`

```
DESCRIPTION
 
    "redo" reapplies the conformational change of the object currently
    being edited.
 
USAGE
 
    redo
 
SEE ALSO
 
    undo, push_undo
```

### `protect`
```
 
    "protect" protects a set of atoms from tranformations performed
    using the editing features.  This is most useful when you are
    modifying an internal portion of a chain or cycle and do not wish
    to affect the rest of the molecule.
 
USAGE
 
    protect (selection)
 
PYMOL API
 
    cmd.protect(string selection)
 
SEE ALSO
 
    deprotect, mask, unmask, mouse, editing
```

### `cycle_valence`
```
DESCRIPTION
 
    "cycle_valence" cycles the valence on the currently selected bond.
 
USAGE
 
    cycle_valence [ h_fill ]
 
ARGUMENTS
 
    h_fill = 0 or 1: updated hydrogens too? {default: 1 (yes)}
 
EXAMPLE
 
    cycle_valence
 
NOTES
 
    If the h_fill flag is true, hydrogens will be added or removed to
    satisfy valence requirements.
 
    This function is usually connected to the DELETE key and "CTRL-W".
 
PYMOL API
 
    cmd.cycle_valence(int h_fill)
 
SEE ALSO
 
    remove_picked, attach, replace, fuse, h_fill
 
```

### `attach`
```
DESCRIPTION
 
    "attach" adds a single atom on to the picked atom.
 
USAGE
 
    attach element, geometry, valence
 
PYMOL API
 
    cmd.attach( element, geometry, valence )
```

## fitting tools
