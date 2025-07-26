---
{"dg-publish":true,"permalink":"/nerfstudio/nerf-studio/"}
---

---
# Context

> [!INFORMATION] About
> "Nerfstudio provides a simple API that allows for a simplified end-to-end process of creating, training, and testing NeRFs. The library supports a **more interpretable implementation of NeRFs by modularizing each component.** With more modular NeRFs, we hope to create a more user-friendly experience in exploring the technology."
> From: https://docs.nerf.studio/

> [!DANGER] Important step if you plan to use a video
> It's important move slowly while shooting a video to be processed as colmap is quite picky about the blurriness of photos and videos

# Setup Docker Desktop 

[Link to docker's official website](https://www.docker.com/products/docker-desktop/)

Step 1: Click the "Download Docker Desktop" Button

![Pasted image 20250726111336.png](/img/user/Assets/Pasted%20image%2020250726111336.png)

Step 2: Choose the appropriate version for your Windows PC

![Pasted image 20250726111701.png](/img/user/Assets/Pasted%20image%2020250726111701.png)


> [!WARNING] Warning
> Currently We haven't made a Macos (due to lack of hardwaare) or Linux guide (due to lack of experience)! Please do not report issues involving those setups!

Step 3: Install it

![Pasted image 20250726112642.png](/img/user/Assets/Pasted%20image%2020250726112642.png)

Step 4: Agree to [[Assets/UAC\|UAC]]

![{10638988-A9DF-466A-BAD2-22A6A2539BCC}.png](/img/user/Assets/%7B10638988-A9DF-466A-BAD2-22A6A2539BCC%7D.png)

Step 5: Follow wizard through install

![Pasted image 20250726113250.png](/img/user/Assets/Pasted%20image%2020250726113250.png)

Step 6: Open Docker Desktop

![{AF97A6D9-732B-4623-BD3A-D82B478665F8}.png](/img/user/Assets/%7BAF97A6D9-732B-4623-BD3A-D82B478665F8%7D.png)

Step 7: Click Skip or sign in


> [!WARNING]  Information about Docker accounts
> From what we can tell, creating a Docker account doesn't add any features


![Pasted image 20250726113601.png](/img/user/Assets/Pasted%20image%2020250726113601.png)
# Start Interactive container (First time install)

> [!IMPORTANT] Important
> C:\nerf_projects\ points to /workspace/
> 

```
docker run --gpus all `
    -u root `
    -v "C:\nerf_projects:/workspace/" `
    -v "C:\.cache:/home/user/.cache/" `
    -p 7007:7007 `
    -it `
    --name nerfstudio `
    -v "C:\nerf_renders:/renders/" `
    -v "C:\nerf_outputs:/outputs/" `
    --shm-size=12gb `
    ghcr.io/nerfstudio-project/nerfstudio:latest
```


> [!WARNING] WARNING
> Our script uses C:\nerf_projects\ which is the SYSTEM PATH TO AVOID COMPATIBILITY ISSUES INVOLVING THE WINDOWS USERNAME

# Update repository and install dependencies

```
apt update
apt install -y git
```

# Gather dataset
## Using photos (most compatible and easy but gives out possibly worse results)

> [!IMPORTANT] Important step while shooting
> It's important move slowly while shooting photos to be processed as colmap is quite picky about the blurriness of photos

> [!QUESTION] Where to put your photos?
> You should put you source photos into C:\nerf_projects\sourcephotos

```
ns-process-data images --data /workspace/sourcephotos --output-dir /workspace/exportedphotonerf
```

## Using a video (most compatible and easy but gives out possibly worse results)

> [!IMPORTANT] Important step while shooting
> It's important move slowly while shooting a video to be processed as colmap is quite picky about the blurriness of videos

> [!QUESTION] Where to put your videos?
> You should put you source photos into C:\nerf_projects\sourcevideo

```
ns-process-data video --data /workspace/sourcevideo/video.mp4 --output-dir /workspace/exportedvideonerf
```

# Train and server Web UI


> [!WARNING] WARNING
> Use the command below if you used the "Using a video (most compatible and easy but gives out possibly worse results)" method, or else it won't work!

```
ns-train nerfacto --data /workspace/exportedvideonerf
```


> [!WARNING] WARNING
> Please do not close this window or else you will stop the training
> 
> ![{AEDB6E3E-A005-4BB1-B4A7-38B14922ED61}.png](/img/user/Assets/%7BAEDB6E3E-A005-4BB1-B4A7-38B14922ED61%7D.png)


> [!INFORMATION] How to open Web UI?
> The Web UI runs at localhost:7007
> 
> Step 1: Locate and click one the address/search bar in your browser
> Google Chrome
![Pasted image 20250726203718.png](/img/user/Assets/Pasted%20image%2020250726203718.png)
Zen Browser
![Pasted image 20250726204006.png](/img/user/Assets/Pasted%20image%2020250726204006.png)
Step 2: Navigate to localhost:7007
Google Chrome
![Pasted image 20250726204225.png](/img/user/Assets/Pasted%20image%2020250726204225.png)
Zen Browser
![Pasted image 20250726204133.png](/img/user/Assets/Pasted%20image%2020250726204133.png)
Step 3: Press Enter
Google Chrome
![Pasted image 20250726204742.png](/img/user/Assets/Pasted%20image%2020250726204742.png)
Zen Browser
![Pasted image 20250726204752.png](/img/user/Assets/Pasted%20image%2020250726204752.png)


> [!WARNING] WARNING
> If you don't see anything on the screen, please wait until your terminal says:
> 
> ![{9240933E-126C-4F27-B13F-3DEA6A7CFC06}.png](/img/user/Assets/%7B9240933E-126C-4F27-B13F-3DEA6A7CFC06%7D.png)


> [!NOTE] Understanding the command prompt
> The text highlighted in red shows the completion percentage of the Nerf
> 
> ![Pasted image 20250726205520.png](/img/user/Assets/Pasted%20image%2020250726205520.png)
> 
> The text highlighted in red shows the Estimated Time to Finish (Arrival) (ETA)
> 
> ![Pasted image 20250726232653.png](/img/user/Assets/Pasted%20image%2020250726232653.png)

Made with ❤️ in [Morocco](https://www.google.com/search?q=Morocco&client=firefox-b-d&sca_esv=0c2e3acf227f4533&sxsrf=AE3TifPxQHRmqHBLU2o4tpsh0hnbHAfeew%3A1753568930760&ei=olaFaJOgLoqIkdUP2br16AM&ved=0ahUKEwiT-dOpyduOAxUKRKQEHVldHT0Q4dUDCBA&uact=5&oq=Morocco&gs_lp=Egxnd3Mtd2l6LXNlcnAiB01vcm9jY28yChAjGIAEGCcYigUyChAuGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyDhAuGIAEGMcBGMsBGK8BSP8fULAFWP8JcAF4AZABAJgBfaAB0QKqAQMwLjO4AQPIAQD4AQGYAgSgAt8CwgIKEAAYsAMY1gQYR8ICDRAAGIAEGLADGEMYigXCAgYQABgHGB7CAgcQLhiABBgKwgIHEAAYgAQYCsICDRAuGIAEGMcBGAoYrwGYAwCIBgGQBgySBwMxLjOgB7slsgcDMC4zuAfbAsIHAzItNMgHDQ&sclient=gws-wiz-serp) 