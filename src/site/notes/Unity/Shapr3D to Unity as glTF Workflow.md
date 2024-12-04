---
{"created":"2023-12-02","time":"Saturday, December 2nd, 2023 @ 10:05:51pm","tags":["unknown"],"authors":["ChrisL8"],"dg-publish":true,"permalink":"/unity/shapr3-d-to-unity-as-gl-tf-workflow/","dgPassFrontmatter":true}
---

I use CAD software to build models for games. This is neither normal nor a recommended method, and it isn't a great method, but it is what I do and I like it.

So here is how to use transfer modes from [Shapr3D](https://www.shapr3d.com/) to Unity via the royalty free [glTF](https://en.wikipedia.org/wiki/GlTF) standard.
# Build models in Shapr3D
## Scale
I suggest using `Meters` as your scale, and then basically build everything to an aproximately realistic scale.
I typically use the "Minecraft scale" that a person is "about 2 meters tall".
![](/img/user/attachments/Pasted image 20231202223736.png)
## Textures
 - Shapr3D allows applying shaders to models, and this method will allow basic colors ("albedo") to be transferred into the game engine. So go ahead and use colors, but don't get carried away with "textures" like metallic, etc. as they won't transfer.
![](/img/user/attachments/Pasted image 20231203203353.png)
# Export STEP file
 - Use the Export feature, and chose `STEP` format
 - The default settings are fine and will include all relevant data that can be transferred
 ![](/img/user/attachments/Pasted image 20231202224227.png)
# Use FreeCAD to convert STEP to glTF
*This can also be done with Blender, but I find FreeCAD quicker and easier if I don't intend to make any edits.*
## Install FreeCAD
https://www.freecad.org/downloads.php
You can either use the installer, or you can download the portable version and just stick it in a folder.
I find using the portable version best for using for conversions, since I don't need an entire installed app with updates or plugins.
 - Note that if you download the portable version, it will be a 7zip file. You must [download 7zip](https://www.7-zip.org/download.html) to extract it. Windows might pretend that it can extract it, but it will fail and claim the file is corrupt.
## Run FreeCad
 - `freecad.exe` is in the `bin` folder if you are using the portal version
 - Open the `STEP` file
## Select the model inside FreeCAD
The export function exports what is selected, not the entire file.
**Do not use Select All** as this will usually produce a mess, instead:
- Press **Shift+b** to enter "Select Mode"
 - Select the entire model in FreeCAD
![](/img/user/attachments/Pasted image 20231203203452.png)
## Export
 - Press **Ctrl+e** to export
 - Set the *Save as type* as `glTF (*.gltf *.glb)`
 - **Name the file with a `.glb` extension, NOT `.gltf`**
     *By using the `.glb` extension, which is the "binary" format of glTF, all parts of the mode will be in **one file**, otherwise you end up with multiple files and it is hard to work with.*
![](/img/user/attachments/Pasted image 20231203203424.png)
# Bring glTF into Unity
## Install Unity glTFast Package
https://docs.unity3d.com/Packages/com.unity.cloud.gltfast@6.0/manual/index.html
Unity doesn't have built in glTF support, but this plugin appears to be official.
 - WIndow->Package Manager
 - Use the + sign dropdown and pick "Add package by name..."
     - ![](/img/user/attachments/Pasted image 20231203195941.png)
 - Paste in `com.unity.cloud.gltfast` and click Add
## Drag the `.glb` File into Unity Project
Open up your Unity editor and Find the file in Windows Explorer and drag the `.glb` file into the Unity project folder where you want it to be.
![](/img/user/attachments/Pasted image 20231203203728.png)
## Drag the imported model into the Unity Scene
Open the Scene that you want to put the model into, and drag the model from the folder into the scene
![](/img/user/attachments/Pasted image 20231203204058.png)
# Colliders
Each side of the model will have its own mesh instance.
![](/img/user/attachments/Pasted image 20231203205008.png)
To add static colliders select ALL of the "roots" by click on the top one and holding Shift while clicking on the last one
**Be sure to select the "root" along with all of the children.**
What looks like the root will just be one of the sides, so if you skip it, one side will not have a collider.
![](/img/user/attachments/Pasted image 20231203210208.png)
Add a Mesh Collider to the selected entries
![](/img/user/attachments/Pasted image 20231203205220.png)
Now is a good time to also drag any scripts that these meshes need onto the group
![](/img/user/attachments/Pasted image 20231203210324.png)

