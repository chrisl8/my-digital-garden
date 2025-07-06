---
{"created":"2024-10-26","time":"Saturday, October 26th, 2024 @ 12:40:42pm","tags":["unknown"],"authors":["ChrisL8"],"dg-publish":true,"permalink":"/blender-notes/","dgPassFrontmatter":true}
---


# Initial Setup
## Startup
Set Spacebar to Search, it is much more useful:
[Open: Pasted image 20241117163818.png](attachments/b9b717b696f3214b43267a96906d9eb8_MD5.jpeg)
![](/img/user/attachments/b9b717b696f3214b43267a96906d9eb8_MD5.jpeg)
### Timeline removal
       - Hover over the intersection on the right until a cross-hair appears
         [Open: Pasted image 20241026124554.png](attachments/30446ae22b2a0b82c0a5fd21455ec210_MD5.jpeg)
![](/img/user/attachments/30446ae22b2a0b82c0a5fd21455ec210_MD5.jpeg)
    - Click and drag down until it turns into a "down chevron" and let go
      [Open: Pasted image 20241026124637.png](attachments/c6347bde7915f3394713e00080a3c5a2_MD5.jpeg)
![](/img/user/attachments/c6347bde7915f3394713e00080a3c5a2_MD5.jpeg)
      and it will go away
 - New File -> General
 - Click in "scene" or on the grid area if it doesn't have focus (keys don't work).
 - `a`
 - `del`
Deletes everything in the scene to get a truly empty file.

 - `t` - Close (or open) the panel on the left side, course leaves it closed
   [Open: Pasted image 20241026124351.png](attachments/5fa65c686e8fad7db9bf15272688e0cc_MD5.jpeg)
![](/img/user/attachments/5fa65c686e8fad7db9bf15272688e0cc_MD5.jpeg)
## Preferences
### Preferences Location
If you want to wipe or back up Blender settings, they are here:
`%APPDATA%\Blender Foundation\Blender`
### Saving Preferences
[Open: Pasted image 20241026131516.png](attachments/babe0a4fc46d2a7aff8fffb7f794bf6a_MD5.jpeg)
![](/img/user/attachments/babe0a4fc46d2a7aff8fffb7f794bf6a_MD5.jpeg)
Auto-Save is on by default, and hence you see now "Save Preferences" button. You can change this if you like.
### Interface
 - Resolution Scale: As you like, but try 1.2
 - -> Navigation Controls: OFF
 - You can turn off the Splash Screen if you like.
[Open: Pasted image 20241117180251.png](attachments/fa877dc98df8fff1922d55c5b98bc50f_MD5.jpeg)
![](/img/user/attachments/fa877dc98df8fff1922d55c5b98bc50f_MD5.jpeg)
### Viewport
 - Increase Anti-Aliasing if you like, it looks nicer.
 - Increase Anisotropic Filtering if you like, it looks nicer.
 - Change the 3D Viewport Axes type if you like, some like the simpler one better
[Open: Pasted image 20241117180445.png](attachments/bbd01adb3c782cb2149b49412606b080_MD5.jpeg)
![](/img/user/attachments/bbd01adb3c782cb2149b49412606b080_MD5.jpeg)
### Keymap
 - Set *Spacebar Action* to *Search* instead of Play (if it wasn't already done at startup)
[Open: Pasted image 20241117180656.png](attachments/2141204f6740d47a2f4273bee6ba797d_MD5.jpeg)
![](/img/user/attachments/2141204f6740d47a2f4273bee6ba797d_MD5.jpeg)
 - Turn off Middle Mouse to Rotate and set Middle Mouse without Shift to Pan:
[Open: Pasted image 20241117183659.png](attachments/3aed8634190a0bd0cb1e8f6ba1c20fc1_MD5.jpeg)
![](/img/user/attachments/3aed8634190a0bd0cb1e8f6ba1c20fc1_MD5.jpeg)
This way I can grab the gizmo for rotate and middle mouse to pan, and never get stuck forgetting to Shift to pan.
Note there are other Rotate & Pan inputs, ignore them, just adjust the two shown as modified by the <- beside them.
### System
  - Set Cycles Render Devices to CUDA to use your GPU and make sure it is selected.
  - Up your Undo Steps to the max unless you have a system with low RAM
[Open: Pasted image 20241117180755.png](attachments/e411a914ac87dd3c5e6da9ec44c66c82_MD5.jpeg)
![](/img/user/attachments/e411a914ac87dd3c5e6da9ec44c66c82_MD5.jpeg)
### Get Extensions
 - 3D Print Toolbox
 - Bool Tool
 - Copy Attributes Menu
 - Edit Mesh Tools
 - Extra Curve Objects
 - Extra Mesh Objects
 - F2
 - Loop Tools
 - MeasureIt
 - Modifier Tools
[Open: Pasted image 20241117181348.png](attachments/8a2c064d9a7f9413d75c7c3d5118505d_MD5.jpeg)
![](/img/user/attachments/8a2c064d9a7f9413d75c7c3d5118505d_MD5.jpeg)
### Add-ons
 - Node Wrangler
#### Down Add-Ons and Install From Disk
Note that Blender Market now has a $1 minimum, so for truly free add-ons, use Gumroad.
##### MACHIN3tools
It is paid, but they use it, so whatevs, $5 is fine.
https://blendermarket.com/products/MACHIN3tools?ref=1051
##### Powersave
https://bonjorno7.gumroad.com/l/powersave
[Open: Pasted image 20241117181557.png](attachments/ba635284482b1a7f95d07b1d7ce2c146_MD5.jpeg)
![](/img/user/attachments/ba635284482b1a7f95d07b1d7ce2c146_MD5.jpeg)
[Open: Pasted image 20241101194820.png](attachments/d71f4b0d10c517d55ed02fa9c97be7a5_MD5.jpeg)
![](/img/user/attachments/d71f4b0d10c517d55ed02fa9c97be7a5_MD5.jpeg)
#### Themes
 - 3D Viewport -> Face Orientation Front -> Alpha Value: 0
[Open: Pasted image 20241117180529.png](attachments/1b1c0fe42e516398294f539c7b9ec943_MD5.jpeg)
![](/img/user/attachments/1b1c0fe42e516398294f539c7b9ec943_MD5.jpeg)
 - Widen the sizes to 7 at the bottom of 3D Viewport
   [Open: Pasted image 20241117180111.png](attachments/d4dd7d12a389c595d12c8e420d2319d7_MD5.jpeg)
![](/img/user/attachments/d4dd7d12a389c595d12c8e420d2319d7_MD5.jpeg)

## Default File Setup
### Clip Start
Set it to 0.1 m instead of 0.01 m
 - Press `n`
 - Select the `View` tab.
[Open: Pasted image 20241026132733.png](attachments/45d4536c3e0232a77835f168c64a276f_MD5.jpeg)
![](/img/user/attachments/45d4536c3e0232a77835f168c64a276f_MD5.jpeg)

### Rendering
[Open: Pasted image 20241026133343.png](attachments/12b514c0f3757a4d746a360640f76e45_MD5.jpeg)
![](/img/user/attachments/12b514c0f3757a4d746a360640f76e45_MD5.jpeg)
[Open: Pasted image 20241026133417.png](attachments/9f2c4b9e9a548ad4228b96c9a9bec238_MD5.jpeg)
![](/img/user/attachments/9f2c4b9e9a548ad4228b96c9a9bec238_MD5.jpeg)
[Open: Pasted image 20241026133505.png](attachments/d6547f12934fea08f39ad9df37fcc108_MD5.jpeg)
![](/img/user/attachments/d6547f12934fea08f39ad9df37fcc108_MD5.jpeg)
### Output Format
[Open: Pasted image 20241026133659.png](attachments/dca96dc4565daed678ac3b4fc1422ae5_MD5.jpeg)
![](/img/user/attachments/dca96dc4565daed678ac3b4fc1422ae5_MD5.jpeg)
## Viewport Shading
Not required, but copy these to look like his, which you'll notice when you see his lighting seems different than yours and things like edges "pop" in the video in ways that they don't for you.
This is why, do this to match his view:
[Open: Pasted image 20241117182704.png](attachments/8e4318d24addcc9e4a59d3476fb38235_MD5.jpeg)
![](/img/user/attachments/8e4318d24addcc9e4a59d3476fb38235_MD5.jpeg)
## SAVE!
File -> Defaults -> Save Startup File
[Open: Pasted image 20241026133803.png](attachments/3092144d9500c9baa460b75c8be1a4e3_MD5.jpeg)
![](/img/user/attachments/3092144d9500c9baa460b75c8be1a4e3_MD5.jpeg)
## Status Bar
[Open: Pasted image 20241026135813.png](attachments/85108abcb240232a88c35b3c6d878a03_MD5.jpeg)
![](/img/user/attachments/85108abcb240232a88c35b3c6d878a03_MD5.jpeg)
# Keyboard

`n` - N Panel
    Mostly useful to see Transform information about selected object.
    Also has all of your add-ons if you are wondering where to see their config
`t` - T Panel
    Mouse based ability to do things which we will do via keyboard shortcuts, so only use it to find things you forgot how to do.
`shift-a` - Add an Object
[Open: Pasted image 20241026141206.png](attachments/82d77ceeec22c1221210db9e8bab4574_MD5.jpeg)
![](/img/user/attachments/82d77ceeec22c1221210db9e8bab4574_MD5.jpeg)
`shift-d` - Duplicate selected Object
`shift-RightClick` - MOVE 3D Cursor
`shift-s`, `W` (or click)  to put Cursor to World Origin again
[Open: Pasted image 20241026143105.png](attachments/491bdbff510148b1db78e051927f2215_MD5.jpeg)
![](/img/user/attachments/491bdbff510148b1db78e051927f2215_MD5.jpeg)
`F3` *or* `Space` - Search - Use it to search for anything you forgot how to do
`Ctrl-Space` - Collapse side menus
`Ctrl-Alt-Space` - "Distraction Free" view
## Selection
`Left Click` - To Select
`Shift + Left Click` - Select More Objects
    Note there is still an "active" object
`a` - Select **EVERYTHING** in the scene
    Note there is still an "active" object
`Alt-a` - DE-select Everything
`b` - Box select (seems to work not the same for me, just click)
`c` - Circle select (not used much)
`Ctrl-i` - **Invert** Selection

### Selection Extras in Edit Mode
Some of these are also in the select menu which can help find them.
`Ctrl + Left Click` - *Continuous Selection* **In Edit Mode** selects multiple things (faces, vertexes, edges) and everything **in between** (Kind of the opposite of how Shift/Ctrl select works in most tools)
`Alt + Left Click` - Select Loop of Edges around clicked Face
You can hold `Shift` when doing these as well to not un-select the same things.
`Ctrl + ALt + Left Click` - *Same Direction* Select everything in the same direction.
`Ctrl +/-` - Expand/Contract selection
`l` - Select all "linked" geometry (yes, you can have unlinked geometry within an object, such as when using the `p` key, as seen later)
`Shift + l` **De**select linked geometry

Also be sure to look at the `Select` menu as it has a **lot** of really useful selection options for difficult cases.

Remember that in Edit mode you can select a Face and switch to Edge mode and the Edges will now be selected, so this is a quick way to select all edges associated with one or more Faces.
## View
`Middle Mouse` - Orbit
`Shift - Middle Mouse` - Pan
`Mouse Wheel` - Zoom
`Alt + Left Click` - Recenter view on selected object
`~` - Open up menu for view angles (similar to the 3D Viewport Axes usage)
`Numpad 1/3/7` - Quick jump to Back, Left, Bottom views.
`Ctrl+Numpad 1/3/7` - Opposite of above
    He likes the `~` key though
Note that the Navigation->Orbit & Pan->Auto->Perspective Preference  determines whether or not going to a "side" view changes the view to Orthographic automatically or not:
[Open: Pasted image 20241026150710.png](attachments/ea10f39ec6d7a2994c377af264d72501_MD5.jpeg)
![](/img/user/attachments/ea10f39ec6d7a2994c377af264d72501_MD5.jpeg)
It is on by default and you want it on typically, but if it isn't working, this is why.
## Transforms
`g` - Grab (Move)
`s` - Scale
`r` - Rotate
`x/y/z` - Lock transform to axis
`Shift-x/y/z` - **Exclude** axis form transform
    For a transform across only 2 dimensions
`Double x/y/z` - Switch from global to local

`Numpad /` - Toggle Local View for active object
## Objects
`Shift+a` - Add menu
`Shfit+d` - Duplicate Object
`Ctrl+c` & `Ctrl-v` works too, although Duplicate is usually easier to work with.
`Shift+r` - Repeat Previous Operation
    This will duplicate things over and over!
        Works with like Rotate, Scale, etc. too.
`Del` - Delete Object
`x` - Also deletes and is less far away on the keyboard

`h` - Hide Object (See the eyeball icon in the Collections Panel)
`alt-h` - Unhide Object
`shift-h` - Hide Everything **Else**
`m` - Move all selected Objects to the collection you pick in the menu that comes up

## Undo
`Ctrl+z` - Undo
`Ctrl+Shift+z` - Redo

## Bool Tool
 - The bool tool ALSO automatically turns the cutter object to wire display!
Select cutter first, then `Shift + Click` target object.
`Ctrl + Numpad(-)` - Difference Boolean
`Ctrl + Numpad(+)` - Union Boolean
`Ctrl + Numpad(*)` - Intersect Boolean
`Ctrl + Numpad(/)` - Slice Boolean

You can also do this with a menu
`Shift + Ctrl + b` brings up:
[Open: Pasted image 20241101195251.png](attachments/b9145d7e52c930b2d270867d072676dd_MD5.jpeg)
![](/img/user/attachments/b9145d7e52c930b2d270867d072676dd_MD5.jpeg)
 - Auto - Auto applies, deleting the cutters, basically destructive
 - Brush - Does not apply it, as you are used to, leaving the cutters and can turn them into wireframe display if enabled
### Bool Tool QOL Benefits
 - The Bool Tool automatically makes a "boolean_cutters" collection and puts the cutters in it.
 - The Bool Tool automatically parents the cutters to the target object so that they move with it.
 - The Bool Tool automatically sets the cutters to be displayed as "Bounding Boxes" which are just boxlike frames
You can change all of these and I actually like setting display to "Wire" although it can affect performance:
[Open: Pasted image 20241101201428.png](attachments/fa49c9551ad508f1411eeb91691377d4_MD5.jpeg)
![](/img/user/attachments/fa49c9551ad508f1411eeb91691377d4_MD5.jpeg)

## Mode
Object Mode and Edit Mode
[Open: Pasted image 20241026150924.png](attachments/c056de9ab07945eb818c17db45a1e666_MD5.jpeg)
![](/img/user/attachments/c056de9ab07945eb818c17db45a1e666_MD5.jpeg)
`Tab` - Quickly switch modes
`1, 2, 3` - Vertex, Edge or Face quick select
(Note, this is **with** the MACHIN3tools addon)
[Open: Pasted image 20241026150955.png](attachments/a06b3990766e98c6603548c6e441af7e_MD5.jpeg)
![](/img/user/attachments/a06b3990766e98c6603548c6e441af7e_MD5.jpeg)
Note that with MACHIN3tools you can jump not just to "Edit Mode" but right into Vertex, Face or Edge rather than having to go to "Edit Mode" and then pick one of those 3.

If you do not have MACHIN3tools, `Tab` will just cycle between Object Mode and Edit Mode instead of bringing up this menu.

It might be faster if you can remember 1, 2, 3 to use `Tab`  then 1, 2, 3 than this menu for you.
The assumption though is that you have the mouse in your left hand at all times anyway for manipulation, so it is fast to use this tool.
# Modifiers
If you Apply any modifier, it technically moves to the TOP of the stack and then applies.
So you really just need to Apply in top-down order, which makes sense anyway.

# Scaling
## Apply
`Ctrl+a` - Apply Menu, Scale

This will APPLY the scale, which will become apparent if you add a Bevel modifier before applying it.

*In Edit Mode transforms are applied automatically.*
# Shading
Default is "Shade Flat"
[Open: Pasted image 20241026154659.png](attachments/6e5f3878cddd1d5b1fb185dc5fcc183a_MD5.jpeg)
![](/img/user/attachments/6e5f3878cddd1d5b1fb185dc5fcc183a_MD5.jpeg)
## Auto Smooth
This smooths each face based on the set Angle.
i.e. Any face that is 30 degrees or higher from another face will be smoothed independently of the other faces.
Actually adds a **Modifier** in Blender 4!
Be aware of that as you have to order/apply it with other things you did.
You can adjust the Angle.
**Don't apply this,** because if you do it will later get applied before cuts, and that will cause a mess.
[Open: Pasted image 20241130175624.png](attachments/e3d7630b1bd199a7500807ce866a1a44_MD5.jpeg)
![](/img/user/attachments/e3d7630b1bd199a7500807ce866a1a44_MD5.jpeg)
# Topology
## Face Topology Types
Based on edge count.
 - Triangles - Cannot be bent!
 - Quads
 - N-Gons - Any face with more than 4 edges.

# Edge Tool Commands
`h` - *Hide Geometry* as it ever was
`Alt+h` - *UN-Hide Geometry*
`Ctrl+r` - Add a *Loop Cut*
    This creates more faces, edges and vertices by cutting the object.
        First click selects the plane and second click selects the location along the plane.
`e` - *Extrude* Face, Edge or Vertex
    Works like it sounds.
    You can extrude multiple faces at once as well.
    **Try constraining the Extrude on the various axis!** It seems at first like there is a logical "only direction" that you can extrude a face, but that just isn't true, you can extrude on any axis from any face, it just produces different results.
    Yes, you can "extrude" faces and vertexes.

Between Loop Cuts and Extrude you can do a **lot** of stuff!
    Remember to move your edges to obtain angles.

`i` - *Inset*
    Insets a face. Try it.
    It works on multiple faces at once too!
        **If the faces are adjacent** press `i` again while insetting multiple faces to switch between insetting them *together* or *individually*
`f` - *Fill*
    Select edges, and then use this to "fill" in between them with a Face.
    Obviously the typical usage is if you deleted a face and want to restore it later, but you can try it across any set of edges.
`Ctrl+b` - *Bevel Tool* on Edges, Faces or Vertexes
    **Similar** to the bevel modifier, but lets you get into the geometry of the faces and pick what to bevel and how far.
    **Scroll Mouse Wheel** to adjust face count in the bevel. To change it from a "chamfer" to a bevel of whatever resolution you want.
    Yes, you can "bevel" faces and vertexes.
`Alt+e` - *Extrude Menu* which has some alternate Extrude types.
    *Extrude Individual Faces* is particularly useful when you want to select some adjacent faces that are not at the same angle and extrude each face "alone". It is easiest to see on the sides of a cylinder.
`p` - Split Geometry so that in Object Mode it is now its own Object
    Use `Shfit + d` (duplicate) and then `p` to quickly create a face/edge/vertex (but usually face) in a new Object.
`m` - Merge Geometry
    Pick two or more Edges/Vertexes/Faces and press `m` and there are several options to merge them together, with resulting changes in geometry
`k` - *Knife Tool* (Cut) through geometry by placing vertexes. Pres `Enter` to accept your cut.
    They warn against using it much as it is a bit dangerous, but it is sometimes important.
[Open: Pasted image 20241029174512.png](attachments/6cd4b53a3d6dd77a9b760517a7f4a3c1_MD5.jpeg)
![](/img/user/attachments/6cd4b53a3d6dd77a9b760517a7f4a3c1_MD5.jpeg)
An example of the chaos one can achieve.

**Limited Dissolve** To "weld" faces (back) together, press `x` and pick "Limited Dissolve" after selecting the two faces to join back together.

# Mirroring
**First, remember that you have to pick a Mirror Object, otherwise it does nothing!**

Note that you mirror "along" the axis chosen. In other words, point an arrow FROM the target object ALONG the axis chosen TOWARD the Mirror Object.

Also note that a Mirror is essentially "overwriting" the other half, so if you modified both sides of an object and then try to mirror it, you lose the bits you modified on the other side.
The only way to accomplish mirroring and keeping things is to mirror the **cutter** instead of the object itself.
It can be confusing because for basic shapes, you can accomplish exactly the same thing by mirroring the object or the cutters, but as your objects get more complex, this starts to matter.
## Unmirrored
[Open: Pasted image 20241114201258.png](attachments/fb227581cff14a4ac985519eb0ffa535_MD5.jpeg)
![](/img/user/attachments/fb227581cff14a4ac985519eb0ffa535_MD5.jpeg)
## Mirrored across *Y*
Y axis is Green here, so you can see that we point an arrow FROM the target object ALONG the Green (Y) axis, toward the Mirror Object to obtain the mirrored object.
[Open: Pasted image 20241114201110.png](attachments/76a01fef29f363420d7d9811fd88751b_MD5.jpeg)
![](/img/user/attachments/76a01fef29f363420d7d9811fd88751b_MD5.jpeg)
## Mirrored across *X*
X axis is Red here, so you can see that we point an arrow FROM the target object ALONG the Red (X) axis, toward the Mirror Object to obtain the mirrored object.
[Open: Pasted image 20241114201146.png](attachments/310fd3819a6743eed8e61bf091283f25_MD5.jpeg)
![](/img/user/attachments/310fd3819a6743eed8e61bf091283f25_MD5.jpeg)
If you pick *Z* (blue line) you'll see nothing, because both the object and the Mirror object are at the same point along the Z axis. Technically the box may be mirrored "over itself", but that is essentially a "null" operation.

You **can** mirror an object "across itself".

## Bisect and Flip
If you think about it, it makes no sense that you can cut a bit out of a cube, mirror it across itself, and then see the cut. The mirror should just cause the entire cube to overlap itself.
You really should mirror the **cutter** instead.

But you can cheat, and the [Blender Mirror Modifier Docs](https://docs.blender.org/manual/en/latest/modeling/modifiers/generate/mirror.html) exlain this perfectly:

### Bisect
If the mesh is already on both sides of the mirror plane, it is cut by that plane, and only one side (the “positive” one by default) is kept to perform the mirror process.

### Flip
When _Bisect_ is enabled on an axis, you can use this setting to switch the side kept and mirrored (i.e. when it is enabled, the “negative” side will be kept, instead of the “positive” one).

So when Blender Bro says, "Sometimes you just have to check 'bisect' and I don't know why." what he means is, you should have mirrored the cutter, but you can use `Bisect` to tell Blender to cut the object in half before mirroring it and then `Flip` if it is cutting off the wrong half.

This how you can cut one corner, and mirror an object across itself, across all axis, and cut out all four corners.
[[attachments/df086c77c0afd1b0152fe46b7b4b2f84_MD5.jpeg|Open: Pasted image 20250109171837.png]]
![attachments/df086c77c0afd1b0152fe46b7b4b2f84_MD5.jpeg](/img/user/attachments/df086c77c0afd1b0152fe46b7b4b2f84_MD5.jpeg)
## Symmetrize
Symmetrize is the same as Mirror, but it is destructive.
[[attachments/bd6d04247aab466b3cc27865b6c280a3_MD5.jpeg|Open: Pasted image 20250706143514.png]]
![attachments/bd6d04247aab466b3cc27865b6c280a3_MD5.jpeg](/img/user/attachments/bd6d04247aab466b3cc27865b6c280a3_MD5.jpeg)
Once you activate it, then at the bottom you will have options for how to "Symmetrize", that being the axis and the direction.
[[attachments/f8de28a127abadfb48d7c50bca61b95e_MD5.jpeg|Open: Pasted image 20250706143653.png]]
![attachments/f8de28a127abadfb48d7c50bca61b95e_MD5.jpeg](/img/user/attachments/f8de28a127abadfb48d7c50bca61b95e_MD5.jpeg)
I'm not aware of any reason to use this instead of Mirror, but it is there and this is how it works.
# Solidify *a plane*
Solidify is used on a plane to allow you to extrude it.
*Even Thickness* is affects how the plane is solidified and generally just keep it on always, but be aware of it if you feel the solidification doesn't look right when solidifying a complex shape.
# Export to FBX for Unity
## Consider Naming your Objects Meaningfully
Within the Collections panel each object has a name.
These names **will** show up in Unity, but:
1. The "folders" will not: The structure will be flattened.
2. No two objects can share a name: Numbers will be added to duplicate names when imported into Unity.
So if you desire, name them to help in Unity. It isn't required though. It depends on how much you plan to work with the mesh and/or update it over time from Blender.
## Apply Everything
1. `a` - Select All
2. `Ctrl + a` - Apply
3. Pick *All Transforms*
## Set Origin Meaningfully
This is kind of up to you, but if the object "sits on the ground", place it so it sits at "0 Z", and the center is centered in X/Y as well.
If it is a spaceship maybe you want the center in the geometric center.

Basically make it easy to import into Unity without having to fuss around with the position more than necesary.

## Export
As FBX. Use the "Operator Presets" to save your settings to use again.
[Open: Pasted image 20241031193858.png](attachments/ee0d7e2cb013919efcdd9581c4644a16_MD5.jpeg)
![](/img/user/attachments/ee0d7e2cb013919efcdd9581c4644a16_MD5.jpeg)
You can save the `.fbx` right into the Unity folder you want it in and you can re-export over it to update it and Unity will handle the update.

# Application of Modifiers
Be aware that until you **apply** a modifier, the geometry shown is only a *preview*. You can demonstrate this by switching from Object to Edit mode and you will not see the modified object **or** you can turn on "preview in edit" mode [Open: Pasted image 20241101192435.png](attachments/9e769f185c89fc27b0b1e31206dbaea4_MD5.jpeg)
![](/img/user/attachments/9e769f185c89fc27b0b1e31206dbaea4_MD5.jpeg) to see what will happen when you apply it.

Also note that you can only apply modifiers in Object mode.

[Open: Pasted image 20241101192538.png](attachments/1bb9d319d1bab17544fe80d0308a73e3_MD5.jpeg)
![](/img/user/attachments/1bb9d319d1bab17544fe80d0308a73e3_MD5.jpeg)

# Destructive Workflows
Be aware that things done in Edit mode are "destructive" because the change can't be "removed" or "changed", while things done in Object mode via Modifiers are considered "non-destructive" because you can undo/change them easily, at least before you apply them.

# Boolean Notes
## View Cutter Object as Wire
You can select any single Object and view **it alone** as wire to make it easier when cutting so you don't have to hide it and you can move it around and see the result:
[Open: Pasted image 20241101194028.png](attachments/4c4cf899e0c2f73c04f4e8edd6230102_MD5.jpeg)
![](/img/user/attachments/4c4cf899e0c2f73c04f4e8edd6230102_MD5.jpeg)
## Types
### Difference (Subtract)
### Union (Add)
### Intersect (Overlapping part)
### Slice (Add a slice at the face intersections)
This one is "secret" or "hidden" and has to be obtained through menus,
although it is in the Bool Tool found with Shift+Ctrl+b

Note that a slice technically duplicates the object and then makes two difference cuts. This means if you delete the cutter, you get a duplicate of your object left behind. Also deleting the Slide Modifier may leave the "slice" still overlapping the uncut object.
## "Cutting the Cutter"
You can make a cut on the cut object itself to put parts of the original target "back".
[Open: Pasted image 20241114195903.png](attachments/83fa2166b5918c6ec4ad6d65c3b2ee51_MD5.jpeg)
![](/img/user/attachments/83fa2166b5918c6ec4ad6d65c3b2ee51_MD5.jpeg)
[Open: Pasted image 20241114200301.png](attachments/bcc1a28bcaedc2ecb13c49511112ed46_MD5.jpeg)
![](/img/user/attachments/bcc1a28bcaedc2ecb13c49511112ed46_MD5.jpeg)
## Mirroring Cutters
You can either mirror the Target/Main Object
[Open: Pasted image 20241114200456.png](attachments/81b61b7eccf1e59ab99e487705a491b8_MD5.jpeg)
![](/img/user/attachments/81b61b7eccf1e59ab99e487705a491b8_MD5.jpeg)
or you can mirror just the cutter
[Open: Pasted image 20241114201752.png](attachments/e955bef40ab4f40a5f79b45a377adbd5_MD5.jpeg)
![](/img/user/attachments/e955bef40ab4f40a5f79b45a377adbd5_MD5.jpeg)
You could also reorder the Modifiers in the first example instead.
## Solver
If your cut isn't happening, you might need to change the solver. Typically you can **always** just use *Exact* and and set that as your default, but sometimes you might want to use a *Fast* in some situation. Just try switching it to see what happens.
Here is an example where *Fast* is just failing with a sphere:
[Open: Pasted image 20241101201246.png](attachments/029dd83a081913b8030dc6cb835c0752_MD5.jpeg)
![](/img/user/attachments/029dd83a081913b8030dc6cb835c0752_MD5.jpeg)
And switching to *Exact* fixes it.
[Open: Pasted image 20241101201304.png](attachments/c28e5eaba04713fd6730c0416b4d840e_MD5.jpeg)
![](/img/user/attachments/c28e5eaba04713fd6730c0416b4d840e_MD5.jpeg)
## Applied
Booleans, before they are Applied are sometimes called "live", so a "live" Boolean is just an un-applied Boolean.
## Connectors
Every Boolean must have two connecting edges to connect it to the Object.
This will be seen if you make a cut that doesn't cross any edges, that is only through faces, you will see extra edges in Edit mode that "connect" the cut too the rest of the object.
[Open: Pasted image 20241101204347.png](attachments/1e47d03c8917a827b78496597b984789_MD5.jpeg)
![](/img/user/attachments/1e47d03c8917a827b78496597b984789_MD5.jpeg)
Otherwise the cut/hole would just collapse out of existence.
Be aware of how this will affect your topology by adding additional geometry (triangles, quads, ngons).
You can try deleting these extra edges in Edit mode to demonstrate what happens without them.

## Bevels, Smoothing and Such
 - Bevels should generally be done **after** cutting to avoid shading issues.
 - Remember to "Shade Autosmooth" your **cutter** as well as the Object.
 - Sometimes you might need to "Clear Custom Split Normal Data" to fix shading:
   [Open: Pasted image 20241114203309.png](attachments/7ac6500a9806e8cb553fa27d206646cd_MD5.jpeg)
![](/img/user/attachments/7ac6500a9806e8cb553fa27d206646cd_MD5.jpeg)
   
### Bad Bevels due to non-perpendicular connection points
Sometimes Blender places the connection edges at a place that causes bevels to not work well.
[Open: Pasted image 20241101210117.png](attachments/7b99b353e64d68f0e17431b321f71ac9_MD5.jpeg)
![](/img/user/attachments/7b99b353e64d68f0e17431b321f71ac9_MD5.jpeg)
You can fix this by creating new connecting edges and dissolving the old ones.
 - Select two new points that are nice and perpendicular to the beveled edge.
 - `j` to join them with an edge.
   [Open: Pasted image 20241114205952.png](attachments/3771b4d279695316712171693c40a307_MD5.jpeg)
![](/img/user/attachments/3771b4d279695316712171693c40a307_MD5.jpeg)
 - Select the bad edges and use `Del` or `Ctrl`+`x` and to "Dissolve Edges"
   [Open: Pasted image 20241114210009.png](attachments/3d7a6996b5b1b97f432cf0fd795173ad_MD5.jpeg)
![](/img/user/attachments/3d7a6996b5b1b97f432cf0fd795173ad_MD5.jpeg)
Then your bevel should work fine.

You could also Turn OFF "Loop Slide"
[Open: Pasted image 20241114210058.png](attachments/7f37eeeb6bfaa8158cb2692201805341_MD5.jpeg)
![](/img/user/attachments/7f37eeeb6bfaa8158cb2692201805341_MD5.jpeg)
## Non-Manifold Geometry
*An easy way to think of "manifold" is that it should be water-tight. If you put the Object itself **into water** no water would enter "into it".*

Booleans can obviously easily create non-manifold geometry.
Booleans also often fail to work on non-manifold geometry, or work oddly.
## Z-fighting
The *Exact* solver should prevent thus but just be aware that you should extend your far enough to cleanly cut through your object, otherwise the "surface" may not want to cut cleanly due to z-fighting.
## N-gons
Just be aware that Booleans often create many n-gons and those can cause shading issues.

## Boolean Ideas to Remember
 - You can Edit and start manipulating (extruding, beveling, etc.) the cutter which will affect the cut.
     - So you can edit the Object **with** the cutter!
 - You can **cut the cutter** to essentially add bits or "parts" **back** to the cut object which will often expand or simplify your workflow.

# Bevels
In Edit mode, select one or more Edges.
`Ctrl`+`b` - Start a bevel.
    Move the mouse to adjust the Bevel.
`Shift` to "slow down" the bevel adjustment input from the mouse.
`Mouse Wheel` - Increase/Decrease segments.
`p` - Change to adjusting the "profile" or "shape"
    Again, now move the mouse to adjust the Profile of the Bevel.
    It is called "Shape" in the bevel modifier box.
    The default Shape (Profile) is 0.5 if you need to put it back.
`c` - Clamp overlap to prevent bevel overlapping
## Bevel Modifier
After you click to "lock in" your bevel, this appears:
[Open: Pasted image 20241114205301.png](attachments/2aa9caff3e7df66309fedfd464c89f3f_MD5.jpeg)
![](/img/user/attachments/2aa9caff3e7df66309fedfd464c89f3f_MD5.jpeg)
Open it up to fine tune your bevel. It has lots of options to modify/fix/improve your bevel by increasing or reducing segment count and other things. Basically everything you did with the mouse you can re-do or do instead here.

You can even customize the profile/shape and do wacky stuff:
[Open: Pasted image 20241114205401.png](attachments/65f42c7a8cf888c14682e90c0b3af2ed_MD5.jpeg)
![](/img/user/attachments/65f42c7a8cf888c14682e90c0b3af2ed_MD5.jpeg)
## Double edges caused by meeting bevels
We met two bevels together by selecting the two edges on this cube and `c` to clamp them and moved them as far as we could
[Open: Pasted image 20241114204001.png](attachments/29385383d4e18bf608eb577f6a5aa392_MD5.jpeg)
![](/img/user/attachments/29385383d4e18bf608eb577f6a5aa392_MD5.jpeg)
But there are TWO edges at that point, which you can see by selecting and grabbing and seeing that you pull one away leaving the other
[Open: Pasted image 20241114204048.png](attachments/e8de3a1019248ba39bd4c6d8ac77d4a9_MD5.jpeg)
![](/img/user/attachments/e8de3a1019248ba39bd4c6d8ac77d4a9_MD5.jpeg)
So you can do one of these:
 - Grab that extra edge and hit `Ctrl`+`x` to just disolve the extra edge.
 - Select all (`a`) and press `m` with the edge selected to "Merge" and pick "By Distance" and it should say it removed two vertices, meaning one edge.
## Scale
Remember to apply scales before beveling, otherwise bevels won't be even, which you will see if you've done this.
The bevel will be "biased".
## Chamfer and Fillet
A "bevel" with a single segment on an edge is what is called a "Fillet".
A "bevel" with many segments is what is called a "Chamfer".
## Bevel Modifiers
### Typical Workflow
1. Right click on Object and "Shade Autosmooth"
2. Add Bevel Modifier
3. Set Segments to 3
4. Set Shading->Harden Normals
This just gives you edges that "pop" or "highlight" looking more lifelike because all edges of all thing IRL, even the edge of a knife has some amount of "roundness" to the edges that catch light.

As opposed to beveling in Edit Mode.
 - ONLY use this to add "edge highlights"
 - NEVER apply them, because it causes problems later and prevents us from adjusting them.
 - Always either check Shading -> "Harden Normal" in the Bevel Modifier and/or add a "WeightedNormal" Modifier in addition to the Bevel Modifier.
So you always want your "Bevel" and "WeightedNormal" modifiers unapplied and always at the **bottom of the stack.**
[Open: Pasted image 20241114205734.png](attachments/f3ce498d4d0947b31e89d2b32720be47_MD5.jpeg)
![](/img/user/attachments/f3ce498d4d0947b31e89d2b32720be47_MD5.jpeg)
Note that Bevel Modifiers also have
 - Loop Slide
 - Clamp
 just like Edit Mode Bevels.
### Clamping
If you find that you cannot get something to bevel, and clamp is on, look at the wireframe and see if you have really dense geometry causing almost immediate clamping or overlapping.
This is where you may want to use a "bevel shader".
### Limit Method
In Bevel Modifiers there is a Limit Method.
#### None
Probably never want None, or things like a cylinder will have the sides beveled and you didn't want that.
#### Weight
If making the Angle small enough to catch edges you want also catches edges that you don't.
You can actually SET the weight of each edge, giving you full control of what gets beveled:
 - Edit
 - Select -> Select Sharp Edges
   [Open: Pasted image 20241114212503.png](attachments/85b180464ca6b2669cc540874b501e3d_MD5.jpeg)
![](/img/user/attachments/85b180464ca6b2669cc540874b501e3d_MD5.jpeg)
   - [Open: Pasted image 20241114212542.png](attachments/5e02bf0de372436b670fdc2ce773a832_MD5.jpeg)
![](/img/user/attachments/5e02bf0de372436b670fdc2ce773a832_MD5.jpeg)
   - Select each edge and set the weight this way.
## Loop Slide
If you have bevels that are acting badly, kind of "sliding up" edges and you can't fix the edges, you can also turn OFF "Loop Slide" in the Bevel properties:
[Open: Pasted image 20241114210147.png](attachments/7f37eeeb6bfaa8158cb2692201805341_MD5.jpeg)
![](/img/user/attachments/7f37eeeb6bfaa8158cb2692201805341_MD5.jpeg)
This causes edges like that to be "pushed out" instead of overlapping the bevels.
This can be helpful in many cases where you want the intersecting edges to not cut across the bevels.
## Segment Count
### In Edit Mode for smooth edges
Basically it doesn't matter, but if you see the lines after using Shade Autosmooth, then you probably needed more,
but you may want to limit your bevel count for games where vertex count matters.
### Bevel Modifiers in Object Mode
Use either 1 or 3, because the entire point is to add "highlights" to the edges so that they "pop" and look more realisitc. More than 3 doesn't really show up.
# Empty
You can add "Empty" objects for use with things like mirror across. Save as with Meshes, `Shift+a` and then pick Empty and whatever you want.
Plan Axis is often used for these things.
It can be a lot easier than making junk meshes for tasks like this.
# Screw
This is like a "revolve" although it takes some fiddling to understand it and get what you want, it is quite powerful.
https://blender.stackexchange.com/questions/46464/how-to-extrude-revolve-2d-shapes-axisymmetrically
# Tips
## Why can't I bevel in Edit Mode?
Or why does the bevel seem to only affect one "face"?
Probably you have adjacent edges somehow, so do this:
In Edit mode `a` to select all, then use the `Mesh` tool menu and select `Cleanup` -> `Merge by Distance` and it should erase adjacent edges and bevels should work as you expect.
[Open: Pasted image 20241102160139.png](attachments/14af8cee12df8dbbc0e9d7abb97915a4_MD5.jpeg)
![](/img/user/attachments/14af8cee12df8dbbc0e9d7abb97915a4_MD5.jpeg)
## Zoom Stuck
Sometimes you cannot Zoom or Pan anymore due to being stuck at some invisible limit.
`Alt+Middle Click` - Will reset your focus to the clicked point and typically fixes this.
# Test Ring Notes
[Open: Pasted image 20241102160124.png](attachments/d2b8023a09fd5bd1abc0fe0b55b49286_MD5.jpeg)
![](/img/user/attachments/d2b8023a09fd5bd1abc0fe0b55b49286_MD5.jpeg)
25 Edges:
[Open: Pasted image 20241130163229.png](attachments/f41168e8feed73f77e9038cd9296a8a4_MD5.jpeg)
![](/img/user/attachments/f41168e8feed73f77e9038cd9296a8a4_MD5.jpeg)

# Further Addons
## HardOps
 - Generally recommended as good, even required.
## BoxCutter
 - Less important than HardOps, but many people still wouldn't live without it. Seems to go "with" BoxCutter?
## Fluent
 - A competitor to BoxCutter. Seems possibly less mature although has a decent community. Seems generally less well-liked than BoxCutter.
## Decal Machine
 - Promoted by BB, seems good.
 - Has a lot of videos on exporting to Unity and such.
## XDecal
 - Newer competitor to Decal Machine. @Dark on BB Discord likes it better than Decal Machine.
 - I haven't found much in the way of docs yet.

# Links to Helps
## Add Vertices to Intersection of two Edges
https://blender.stackexchange.com/questions/2976/how-can-i-add-vertices-to-intersection-of-two-edges
## Disable click to move (grab)
https://blender.stackexchange.com/questions/93045/how-can-i-disable-click-to-move-grab
