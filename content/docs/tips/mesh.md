---
title: "Mesh"
description: "What are mesh files"
summary: "Mesh files explained"
draft: false
weight: 0
toc: true
---

Mesh files contain geometry, weights, UV, and other data. Essentially, mesh file is the model file that should to be referenced in the [nif](/docs/tips/nif/), and mesh file isn't linked in the game plugin directly (the nif is linked instead).

#### Mesh files contain:
- Geometry data
- UV data
- Weights data
- Vertex Colors

___

## FAQ

### Is it possible to create a custom mesh?
Yes, it is possible to export your model as mesh file in Starfield Geometry Bridge.

### Is Internal geometry better than the External geometry?
In general, it's a matter of preference. Many find that working with [nif](/docs/tips/nif/) with **Internal geometry** is easier considering the repetitive process of making changes and re-exporting the files.

### Where are mesh files?
Mesh files are located in [.ba2 archives](/docs/tips/archives/) that have `Meshes` in the archive name. Mesh files are located specifically inside the `geometries` folder.

### How to open mesh files?
Mesh file can't be opened using double-click. Instead, it can be imported to Blender using the Starfield Geometry Bridge addon. As an alternative when the nif is present, the nif that contains a path to that specific mesh can be opened to preview the model.
