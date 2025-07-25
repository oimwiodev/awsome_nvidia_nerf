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
Viewer running locally at: http://localhost:7007 (listening on 0.0.0.0)
╭────────────────────────────────── 🎉 Training Finished 🎉 ──────────────────────────────────╮
│                        ╷                                                                    │
│   Config File          │ outputs/camera_pose/nerfacto/2025-07-25_182644/config.yml          │
│   Checkpoint Directory │ outputs/camera_pose/nerfacto/2025-07-25_182644/nerfstudio_models   │
│                        ╵                                                                    │
╰─────────────────────────────────────────────────────────────────────────────────────────────╯
                                                   Use ctrl+c to quit
(viser) Connection opened (4, 2 total), 846 persistent messages
(viser) Connection closed (4, 1 total)
Traceback (most recent call last):
  File "/usr/local/lib/python3.10/dist-packages/viser/infra/_infra.py", line 546, in wrapped
    inner()
  File "/usr/local/lib/python3.10/dist-packages/viser/infra/_infra.py", line 366, in <lambda>
    lambda: client_connection._handle_incoming_message(
  File "/usr/local/lib/python3.10/dist-packages/viser/infra/_infra.py", line 139, in _handle_incoming_message
    cb(client_id, message)
  File "/usr/local/lib/python3.10/dist-packages/viser/_viser.py", line 521, in handle_camera_message
    camera_cb(client.camera)
  File "/usr/local/lib/python3.10/dist-packages/nerfstudio/viewer/viewer.py", line 363, in _
    self.render_statemachines[client.client_id].action(RenderAction("move", camera_state))
KeyError: 4
(viser) Connection opened (5, 2 total), 846 persistent messages
(viser) Connection closed (0, 1 total)
(viser) Connection opened (6, 2 total), 846 persistent messages