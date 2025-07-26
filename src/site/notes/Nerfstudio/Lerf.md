---
{"dg-publish":true,"permalink":"/nerfstudio/lerf/"}
---

https://docs.nerf.studio/nerfology/methods/lerf.html
[Paper Website](https://www.lerf.io/)

> [!INFORMATION] About
> "LERF optimizes a dense, multi-scale language 3D field by volume rendering CLIP embeddings along training rays, supervising these embeddings with multi-scale CLIP features across multi-view training images. After optimization, LERF can extract 3D relevancy maps for language queries interactively in real-time. LERF enables **pixel-aligned** queries of the distilled 3D CLIP embeddings **without relying on region proposals, masks, or fine-tuning**, supporting long-tail open-vocabulary queries hierarchically across the volume."
> From: https://www.lerf.io/

python3 -m pip install git+https://github.com/kerrj/lerf

Made with ❤️ in [Morocco](https://www.google.com/search?q=Morocco&client=firefox-b-d&sca_esv=0c2e3acf227f4533&sxsrf=AE3TifPxQHRmqHBLU2o4tpsh0hnbHAfeew%3A1753568930760&ei=olaFaJOgLoqIkdUP2br16AM&ved=0ahUKEwiT-dOpyduOAxUKRKQEHVldHT0Q4dUDCBA&uact=5&oq=Morocco&gs_lp=Egxnd3Mtd2l6LXNlcnAiB01vcm9jY28yChAjGIAEGCcYigUyChAuGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyDhAuGIAEGMcBGMsBGK8BSP8fULAFWP8JcAF4AZABAJgBfaAB0QKqAQMwLjO4AQPIAQD4AQGYAgSgAt8CwgIKEAAYsAMY1gQYR8ICDRAAGIAEGLADGEMYigXCAgYQABgHGB7CAgcQLhiABBgKwgIHEAAYgAQYCsICDRAuGIAEGMcBGAoYrwGYAwCIBgGQBgySBwMxLjOgB7slsgcDMC4zuAfbAsIHAzItNMgHDQ&sclient=gws-wiz-serp) 