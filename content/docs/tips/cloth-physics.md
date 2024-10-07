---
title: "Cloth physics bin file"
description: "Tips: Cloth Physics bin file"
summary: "Tips: Cloth Physics bin file"
draft: false
weight: 10
toc: true
---

Cloth physics `.bin` file contains binary cloth physics data.

---

## FAQ

### Is it possible to create a custom cloth physics .bin file?
Yes, it is currently possible to create a custom cloth physics .bin file. You can refer to [Cloth Physics Guide](/user-manual/cloth-physics-guide/).

### Where are cloth physics .bin files?
In nifs containing physics data, cloth physics bin files are located next to the BSGeometry, in the BSClothExtraData.

```mermaid
flowchart LR
  subgraph NiNode
      subgraph BSClothExtraData
        Physics["Physics .bin file"]
      end
    BSGeometry
    Other["Other data..."]
  end
```

### How to open cloth physics .bin file?
Currently, it is impossible to import the data from the physics .bin file to the editable physics graph. However, it is possible to visualize some of the data it contains (see [Cloth Physics Guide](/docs/user-manual/cloth-physics-guide/#inspecting-how-vanilla-does-it))