---
{"created":"2023-12-27","time":"Wednesday, December 27th, 2023 @ 2:16:37pm","tags":["unknown"],"authors":["ChrisL8"],"dg-publish":true,"permalink":"/godot/godot-skybox-with-space-engine/","dgPassFrontmatter":true}
---


Licensing: Please see the Space Engine site for information on licensing. I believe that by buying the basic Space Engine you do NOT acquire a license to use exported images.
However, you also can only export very low rez skybox images that look pretty crappy, so for testing and development I am just using them for now.
To obtain a license to use these images in your work and the ability to export high resolution images look for and buy the "SpaceEngine PRO" license.

# Export Skybox from Space Engine
 - Find a spot in the Universe where you like the view.
 - Tick things off/on that you don't want to see like labels or galaxies or whatever.
 - Escape to the main menu and select:
     - Tools, then
     - Export skybox
 - Note that you are still "in the engine" now so you can still move the view around and tick features on and off.
 - Turn OFF "Identify faces" as you don't want that text in the image.
 - Export
Space engine will just put the files in this folder, overwriting the last save:
`C:\Program Files (x86)\Steam\steamapps\common\SpaceEngine\export`

# Convert the Cubemap to a "Panorama"
As per the Godot [documentation](https://docs.godotengine.org/en/stable/classes/class_panoramaskymaterial.html#class-panoramaskymaterial) it uses a "equirectangular sky map" instead of a cube map and you can use this tool to convert it:
https://docs.godotengine.org/en/stable/classes/class_panoramaskymaterial.html#class-panoramaskymaterial

Upload each segment form the folder. The names of the files should make it clear which one goes where.
Set the rotation to 0 for ALL segments.
use the "Update" button to update the image.
![](/img/user/attachments/Pasted%20image%2020231227142414.png)
When you are done use "Download(save) result" to get the file for Godot.

**Copy this saved file into your Godot project somewhere.**
# Set up a Skybox in Godot
 - Add a "WorldEnvironment" to your scene
 - Add a "New Environment" to it
   ![](/img/user/attachments/Pasted%20image%2020231227142617.png)
 - Click on the Environment and under Background -> Mode select "Sky"
   ![](/img/user/attachments/Pasted%20image%2020231227142733.png)
   - Open up the "Sky" drop down now and click on `<empty>` and add a new Sky
![](/img/user/attachments/Pasted%20image%2020231227142839.png)

 - Click on "Sky" to make it open up and click on `<empty>` underneath next to "Sky Material" and select "New PanoramaSkyMaterial"
![](/img/user/attachments/Pasted%20image%2020231227143141.png)

 - Click on "PanoramaSkyMaterial" to make it open up so that you see `<empty>` next to "Panorama"
 - Drag the file panorama image file you saved from the web site earlier onto this box.
   ![](/img/user/attachments/Pasted%20image%2020231227143546.png)

Now it should look something like this and you will see the exported background from Space Engine in your editor.
![](/img/user/attachments/Pasted%20image%2020231227143655.png)

