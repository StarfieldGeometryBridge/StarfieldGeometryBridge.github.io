---
title: "Common problems"
description: "Various solutions to common problems."
summary: "Various solutions to common problems."
draft: false
weight: 0
toc: true
---

## Invisible in-game
It being invisible in-game might mean:
- If your object has [morph](/docs/tips/morph/): Try re-exporting while having world origin consistent across all your exports for that specific armor (either all use world origin, or nothing uses world origin)
- Incorrect [nif](/docs/tips/nif/) path in your plugin file
- If you don't use internal geometry, then it might be incorrectly exported `.mesh`: geometries folder should be at the root of the folder next to the meshes, etc.
- If your model is Armor Addon, then it might be slots conflict (slot that the armor part occupies is already occupied by other currently equipped clothing item)
- Too high/low, and it's actually too above/below of the point it should be located at. Sometimes because of it being too high/low it's invisible entirely in-game because it exceeds object bounds. Check if it's located at correct location in the NifSkope 3D scene.
- If your model uses physics bones, the nif must contain physics data block.

## Invisible in NifSkope
> At first, make sure you have the correct [NifSkope, by fo76utils](https://github.com/fo76utils/nifskope/releases/latest).

It being invisible in NifSkope might mean you haven't set up your path in NifSkope options. Navigate the NifSkope UI: `Options > Settings > Resources`, enter the path to Starfield if it's not there, and navigate to `Paths`, press Starfield, Auto-Detect, and then if you use Mod Organizer for example you may additionally add the path to your mod folder by pressing the `Add Folder` button. Restart NifSkope, and the problem shouldn't persist: your model should be visible.

## Distorted and moving in all possible directions in-game
Bones that are present in the .nif are not present in the .mesh, or the bone order is incorrect. Try re-exporting .nif, if you prefer using external geometry use the .mesh that is exported with the .nif automatically and not re-export the mesh; depending on your preference, you may use the [internal geometry](/docs/tips/mesh/#is-internal-geometry-better-than-the-external-geometry).

## Looks like cactus in-game (all in small spikes)
Incorrect morph, try re-exporting it. Please mind world/object origin when you're exporting the morph: usually, it's either only world origin or only object origin (object origin is world origin unticked).

## Armor addon texture is incorrect/mesh has skin texture in-game where it's not needed
**For skin:** Make sure your Armor Addon (ARMA) has been marked as skin, in Creation Kit it can be checked at `Right click > Inspector` (scroll until you find it). In xEdit, it can be checked at the record header.

**For regular mesh:** Vise-versa, make sure your armor addon is not marked as skin there.