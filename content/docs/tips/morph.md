---
title: "Morph"
description: "What are morph files"
summary: "Morph files explained"
draft: false
weight: 0
toc: true
---

Morph files are like shape-keys in Blender: morph.dat contains data for deforming the object in a certain way, good example is vanilla weights circle found in the character creator menu.

#### Morph file contains:
- Deformation data (similar to the Blender shape-keys)
- Vertex colors
- Delta normals & Tangents

___

# FAQ

### Do I need a morph file at all?
Morph file is needed for outfits, headparts, etc. Sometimes, the file is not needed at all.

### What is the difference between performance and chargen morphs?
In general, performance morphs contain noticeable vertex colors and are changed when the character *performs*, as-in facial expression or bending fingers.

Chargen morphs, on the other hand, are supposed to allow for character customization, for example changing the weight between Overweight, Thin, Strong, or adjusting a specific facial feature. Chargen morphs also can be applied using `ApplyChargenMorph` command, opposed to performance morphs.

### What is the correct way of storing it?
A single file named `morph.dat` (the morph file itself) should be located in a folder. The folder specifically should be referenced in the game plugin file, and not the `morph.dat` file itself.

### Is it possible to create a custom morph?
Yes, it is possible by exporting the morph.dat from the Blender using the Starfield Geometry Bridge addon.

### Where are the morph.dat files located?
Morph files are located in [.ba2 archives](/docs/tips/archives/) that have `Meshes` in the archive name. The files are located specifically inside the `/meshes/morphs/` folder.

### How to open morph.dat file?
The morph.dat file can't be previewed using double click or imported as-is in Blender due to how it stores data. Instead, it should be imported on the model you have in Blender. The morph.dat should contain the exact vertex amount and correct vertex order, so the best way would be using that model's specific morph.dat, if it exists.
