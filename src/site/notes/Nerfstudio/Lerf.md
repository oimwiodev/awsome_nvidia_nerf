---
{"dg-publish":true,"permalink":"/nerfstudio/lerf/"}
---

https://docs.nerf.studio/nerfology/methods/lerf.html
[Paper Website](https://www.lerf.io/)


> [!INFORMATION] About
> "LERF optimizes a dense, multi-scale language 3D field by volume rendering CLIP embeddings along training rays, supervising these embeddings with multi-scale CLIP features across multi-view training images. After optimization, LERF can extract 3D relevancy maps for language queries interactively in real-time. LERF enables **pixel-aligned** queries of the distilled 3D CLIP embeddings **without relying on region proposals, masks, or fine-tuning**, supporting long-tail open-vocabulary queries hierarchically across the volume."
> From: https://www.lerf.io/

python3 -m pip install git+https://github.com/kerrj/lerf