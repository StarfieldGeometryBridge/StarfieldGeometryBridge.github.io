---
title: "Nif"
description: "What are nif files"
summary: "Nif files explained"
draft: false
weight: 0
toc: true
---

Nif files are files that contain the [mesh](/docs/tips/mesh/) or link to the mesh along with other data. These files have various editable properties allowing for adjusting the model and sometimes how it behaves in-game (eq. physics data, collision). These files can be referenced in the plugin file, which allows Starfield to load the custom model.

#### Nif files contain:
- [Mesh](/docs/tips/mesh/) path or internal geometry
- [Material](/docs/tips/material/) path
- Translation (how mesh is rotated, for example)
- In some cases, Physics data. Information on creating custom physics data can be found [here](/docs).
- In some cases, Collision data.
- Nif files also contain other data.

___

## FAQ

### Is it possible to create a custom nif?
Yes, currently it is possible to create a custom nif file, along with the custom [mesh](/docs/tips/mesh/) file or internal geometry.

### What is internal geometry?
Internal geometry is a mesh but inside the nif file itself. Most of the vanilla nif files are the opposite: they link to the mesh by specific path, having the mesh stored externally.

### Where are nif files?
Vanilla nif files are located in [.ba2 archives](/docs/tips/archives/) that have `Meshes` in the archive name. Nif files are located specifically inside the `meshes` folder.

### How to open nif file?
Starfield nif file can be opened using [fo76utils NifSkope fork](https://github.com/fo76utils/nifskope/releases/latest). To view the nif correctly, you should set-up the paths at the NifSkope options. Also, it can be imported to Blender directly using the Starfield Geometry Bridge addon.
