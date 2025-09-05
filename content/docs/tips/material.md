---
title: "Material (.mat) file"
description: "Tips: Material file"
summary: "Tips: Material (.mat) file"
draft: false
weight: 10
toc: true
---

Material `.mat` file contains json (can be opened with any notepad program) that contains paths to textures and other definitions (e.g. hair shader definitions for hair material).

## FAQ

### Is it possible to create a custom material, so the .mat file?
Yes, Starfield Creation Kit has material editing functionality with preview that shows how it might look with in-game lights. Additionally, [fo76utils NifSkope fork](https://github.com/fo76utils/nifskope/releases/latest) has similar functionality for editing/creating materials.

### Where to get .mat files?
Ready-to-edit "loose" `.mat` files are obtained from `SteamLibrary\steamapps\common\Starfield\Tools\ContentResources.zip` zip archive.

BA2 archives don't contain loose `.mat` files, but do contain a compiled material database.

### How to open .mat files?
Starfield `.mat` files are supposed to be placed at the `Data\Materials` - subfolders can be used for organizational purposes, as well as any name (such as, `Data\Materials\MyFolder\MyMaterialFile.mat`) as long as it's in `Data\Materials`

If one opens Creation Kit after placing material file at the correct location, materials would load into the Material Editor and one could edit it in the way one wants.

### How to link material (mat) file and my model (nif)?
If you want to link existing material with existing nif, open the nif with NifSkope and look for BSGeometry inside the Block List tab. Expand BSGeometry and click on BSLightingShaderProperty, you will see a field Name in the Block Details section. Right click on `Name` and explore the options.

If you choose Select String Index, it would prompt you to enter the path. Note the slash symbol, it should be: `\` and the Material Path should start with `Materials\` and the game would look for material in the `Data\Materials\...` where `...` is anything else after the path. Path should point to the material file, and should include extension (`.mat`)

### How do I set the material path with SGB?
By setting the material path for the mesh you're exporting, you can avoid setting material path in the nif. To do that, rename first material of the object you're exporting to material path, for example: 

`Materials\MyFolder\MyMaterialFile.mat`

Path should not be full, but rather must with `Materials\` - and path should point to the material file, and should include `.mat` extension
