---
title: "Setting up addon"
description: ""
summary: ""
draft: false
weight: 1000
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
aliases:
  - /docs/guides/hello-world/
---

# Setting Up Your Plugin

## **Installation**
1. Download Blender from its [official website](https://www.blender.org/). **Make sure to download a version that is higher than 3.5 and lower than 4.0**!
2. Download the latest Starfield Geometry Bridge plugin from [GitHub](https://github.com/SesamePaste233/StarfieldMeshConverter/raw/master/dist/tool_export_mesh/tool_export_mesh.zip)
3. Open Blender and Navigate to "Edit -> Preferences -> Addons -> Install".

![Image 1](/hello/image1.png)

![Image 2](/hello/image2.png)

4. Install the Starfield Geometry Bridge plugin you just downloaded in the installation window.
5. Enable the plugin as is shown in Image 3.

![Image 3](/hello/image3.png)

## Set Up Your Assets

![Image 4](/hello/image4.png)

1. We only care about two folder paths for now. They are "**Export Folder**" and "**Assets Folder**".
 - - **Default Export Path** is the default folder that holds your exported files if their export paths are not specified. **Set this path to somewhere you won't forget**!

 - - **Assets Folder** is the folder that has all the **loose files** extracted from ba2 archive files. The plugin will look for game assets as loose files in this folder. 

Since **Assets Folder** requires loose files, you should first **extract ba2 archives as loose files in a folder**, and then **set Assets Folder path to this folder**. Extract the assets you need. If you want to use vanilla assets, they are located in the `meshes01.ba2` and `meshes02.ba2`.

**Your Assets Folder should look like on image below:**

![Image 5](/hello/image5.png)
___

### What's next?
**Depending on what you plan to do next, here is some knowledge you might find useful:**

{{< card-grid >}}
{{< link-card title="Mesh" href="/docs/tips/mesh" >}}
{{< link-card title="Nif" href="/docs/tips/nif" >}}
{{< link-card title="Morph" href="/docs/tips/morph" >}}
{{< /card-grid >}}

{{< card-grid >}}
{{< link-card title="Exporting model" href="/docs/user-manual/exporting-data" >}}
{{< /card-grid >}}

___