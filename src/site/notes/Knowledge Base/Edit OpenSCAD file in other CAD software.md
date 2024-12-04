---
{"dg-publish":true,"permalink":"/knowledge-base/edit-open-scad-file-in-other-cad-software/","dgPassFrontmatter":true}
---

*Posted: December 14, 2022*
# Loving all the CAD software
![attachments/Pasted image 20230224162609.png](/img/user/attachments/Pasted%20image%2020230224162609.png)

I really enjoy working in [OpenSCAD](https://openscad.org/) because creating things with text on a computer in an iterative way where I can copy/paste things, do and undo things across a wide area, and make big changes by tweaking just a number here or there. I also enjoy making reusable functions to use the same code over and over.

However, [OpenSCAD](https://openscad.org/) has pain points. Primarily for me at least the two big things that are not easy with OpenSCAD are

1.  Fillet’s are very difficult to add to parts.
2.  Measurements between abstract points.

It **is** possible to do something like fillets in OpenSCAD, but it isn’t as easy and just “grabbing” a corner and “pulling” it to exactly the point you want.

You would **think** that if I built an entire assembly with math, that I’d know how to calculate the distance between any two points, **but** it is easy to get to state where this isn’t simple. That and I’m actually not great at math, I juts brute force a lot of things and that leaves me not always able to reverse engineer things.

A more traditional CAD program makes both of these easy.

What you need to do is get the .scad file into a STEP file format that you can then import into almost any traditional CAD software. I use [Shapr3D](https://www.shapr3d.com/), but this works for any CAD program.

# Convert from .scad to STEP format with FreeCAD

1. Build your OpenSCAD file as usual.
    1. You don’t have to “render” it, just create it. Our next tool will read the OpenSCAD code.
    2. Keep your designs simple.
        1. No need to use minkowski, etc. if you are going to tweak in Fusion 360 anyway.
        2. Skip things like triangle supports if you plan to use fillets instead, as you won't be able to easily delete those triangles later.
2. **Comment out any `$fn`, `$fa`, or `$fs` entries.** These can mess up the output.
        1. In particular, it turns normal rounded surfaces into a series of faces that are impossible to edit.
3. Open up FreeCAD
    1. https://www.freecadweb.org/
    2. NOTE: I find that the weekly build works more reliably: https://github.com/FreeCAD/FreeCAD-Bundle/releases/tag/weekly-builds
4. *FIRST TIME ONLY - Go to View  → Workbench → OpenSCAD* 
    1. This is required to enable opening OpenSCAD files,
    2. **but is only required the first time you open FreeCAD**
5. You should be able to open up the OpenSCAD file just like any other file now.
6. Select your parts
    1. Edit -> Box Selection (or Shift+b)
    2. Drag to select the entire set of parts in the model view
    3. **DO NOT USE Ctrl+a**
        1. This will grab the "sub-parts" of unions and differences and make a MESS
        2. You will know you did this because the import later will see thousands of parts, when it should be under 100.
7. File → Export
8. Export as a “STEP with colors (*.step *.stp)” file.
    1. Note that the "Scheme" is not really important. AP203 includes everything we need, the newer formats add stuff we don't even have in this drawing, but also don't hurt.
    ![attachments/Pasted image 20221226143146.png](/img/user/attachments/Pasted%20image%2020221226143146.png)
    I've been checking the "Write out curves" box, but I don't know if it matters or not.

## All done!

This .step file should easily import into any CAD software. I use Shapr3D myself.

---
# Other Old Notes
... that you probably do NOT need.

## Cleanup

**This only happens if you used Ctrl+a to select parts!** If you used the Box Selection tool, this won't happen.

Sometimes you get “ghost parts” that you didn’t intend. Fusion 360 apparently interprets the .step differently than OpenSCAD and FreeCAD do.

![attachments/01b396a0c83baad1baa55bf9ddaccf7e_MD5.png](/img/user/attachments/01b396a0c83baad1baa55bf9ddaccf7e_MD5.png)


Use the part list on the left to find your part

![attachments/4ae9fc2255f13666a4883ea74f46959c_MD5.png](/img/user/attachments/4ae9fc2255f13666a4883ea74f46959c_MD5.png)


It will probably consist of many pieces, but each entry should highlight the bit it corresponds to when you select it, and highlight it “a little less” when you hover over it.

![attachments/47f1c6da0c2cdfe65f17ae49c39edeb3_MD5.png](/img/user/attachments/47f1c6da0c2cdfe65f17ae49c39edeb3_MD5.png)


You can either Right Click on the entry and select “Delete” or use the Del key on your keyboard to delete it.
Keep doing this with all of the bit until the entire host part is gone.

![attachments/1884e1233af573c0cceb7aa817d141ca_MD5.png](/img/user/attachments/1884e1233af573c0cceb7aa817d141ca_MD5.png)


Notice that I had to delete a LOT of parts!


## Combine

**This happens in Fusion 360, but I have not had to do this in Shapr3D.**

If you try to select the edge between two unrelated bits of the model, you will find none exists. They are just random pieces that happen to overlap.

To combine them pick the “Combine” option from “Modify” section of the “SOLID” menu.

![attachments/14bc8b882ad40a1c3f17988d4b04aced_MD5.png](/img/user/attachments/14bc8b882ad40a1c3f17988d4b04aced_MD5.png)


You can only combine two parts at a time, so in my case, it takes two operations to combine each cylinder with the box.

A menu pops up. Select the first bit to combine, then select the next bit, then hit “OK”.
The little boxes in the menu change to show what bit you are selecting. If they don’t automatically jump to the next after selecting a bit, you can tell it by clicking on the box which bit you intend to select.

![attachments/4014b3b0a932f7fd544afe55d1e0a2e7_MD5.png](/img/user/attachments/4014b3b0a932f7fd544afe55d1e0a2e7_MD5.png)


“Click”

![attachments/467159ef6102491b64c750d415462fad_MD5.png](/img/user/attachments/467159ef6102491b64c750d415462fad_MD5.png)


“Click”

![attachments/d89adcea2e4a167dacfbbbe0dd5f9983_MD5.png](/img/user/attachments/d89adcea2e4a167dacfbbbe0dd5f9983_MD5.png)


“OK”

Notice how it doesn’t let you hit OK until you’ve selected both bits.

I’m not entirely sure if it matters, or how it matters, which is the “Target” and which is the “Tool”.

Once it is done, there will be an edge between the two that you can select for things like Fillet.

![attachments/2aec14299ebdd6b432ff53c4240bc893_MD5.png|Close up before combine.](/img/user/attachments/2aec14299ebdd6b432ff53c4240bc893_MD5.png)


Notice there is no edge between the cylinder and the box, and the cylinder clearly protrudes into the box. You could literally just move it right out of there, it isn’t joined in any way, and we cannot act on the point where they “touch”.


![attachments/3e64186ceb9b4b66e7d2b5acc77072b4_MD5.png|Close up after combine.](/img/user/attachments/3e64186ceb9b4b66e7d2b5acc77072b4_MD5.png)


I had to select the Fillet tool to let me highlight the edges, but notice:

1. There IS now an edge to select between the cylinder and the box.
2. The cylinder no longer protrudes into the box, it is actually connected to it as a piece.


----------
## Fillets in OpenSCAD

There are a few ways to “fillet” or smooth out parts in OpenSCAD

### Minkowski

https://en.wikibooks.org/wiki/OpenSCAD_User_Manual/Transformations#minkowski
This adds two parts together. The difficult part s getting an exact final measurement.

Combine a piece with a sphere, and it will round the edges.

### Fillet Function

This function performs a sort of Fillet between two parts

https://github.com/clothbot/ClothBotCreations/blob/master/utilities/fillet.scad

### OpenSCAD Functions

There is a pile of OpenSCAD functions here.

https://github.com/nophead/NopSCADlib

#MakeStuff #PvcPipeCreations #Mechanical #OpenSCAD #KnowledgeBase 