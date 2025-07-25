---
{"dg-publish":true,"permalink":"/nerf-studio/"}
---

---
# Context
Nerfstudio provides a simple API that allows for a simplified end-to-end process of creating, training, and testing NeRFs. The library supports a **more interpretable implementation of NeRFs by modularizing each component.** With more modular NeRFs, we hope to create a more user-friendly experience in exploring the technology.
# Start Interactive container

> [!IMPORTANT] Important
> C:\nerf_projects\ to /workspace/

```
docker run --gpus all `
    -u root `
    -v "C:\nerf_projects:/workspace/" `
    -v "C:\.cache:/home/user/.cache/" `
    -p 7007:7007 `
    --rm `
    -it `
    --shm-size=12gb `
    ghcr.io/nerfstudio-project/nerfstudio:latest
```


> [!WARNING] WARNING
> Our script uses C:\nerf_projects\ which is the SYSTEM PATH TO AVOID COMPATIBILITY ISSUES INVOLVING THE WINDOWS USERNAME

# Update repository and install dependencies

```
apt update
apt install -y git
python3 -m pip install git+https://github.com/kerrj/lerf
```

ns-train nerfacto --data /workspace/camera_pose/
# Run colmap analysis
```

```
