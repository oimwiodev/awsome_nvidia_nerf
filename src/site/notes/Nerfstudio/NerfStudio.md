---
{"dg-publish":true,"permalink":"/nerfstudio/nerf-studio/"}
---

---
![logo-dark.png](/img/user/Assets/logo-dark.png)
# Context

> [!INFORMATION] About
> "Nerfstudio provides a simple API that allows for a simplified end-to-end process of creating, training, and testing NeRFs. The library supports a **more interpretable implementation of NeRFs by modularizing each component.** With more modular NeRFs, we hope to create a more user-friendly experience in exploring the technology."
> From: https://docs.nerf.studio/

> [!DANGER] Important step if you plan to use a video
> It's important move slowly while shooting a video to be processed as colmap is very picky about the blurriness of photos and videos

# Setup Docker Desktop 

[Link to docker's official website](https://www.docker.com/products/docker-desktop/)

# Requirements:

* An x86 machine running windows
* An Nvidia Graphics card
## Step 1: Click the "Download Docker Desktop" Button

![Pasted image 20250726111336.png](/img/user/Assets/Pasted%20image%2020250726111336.png)

## Step 2: Choose the appropriate version for your Windows PC

![Pasted image 20250726111701.png](/img/user/Assets/Pasted%20image%2020250726111701.png)

> [!WARNING] Warning
> Currently We haven't made a macOS (due to lack of official support) or Linux guide (due to lack of experience)! Please do not report issues involving those setups!

## Step 3: Install it

![Pasted image 20250726112642.png](/img/user/Assets/Pasted%20image%2020250726112642.png)

## Step 4: Agree to [[Assets/UAC\|UAC]]

![{10638988-A9DF-466A-BAD2-22A6A2539BCC}.png](/img/user/Assets/%7B10638988-A9DF-466A-BAD2-22A6A2539BCC%7D.png)

## Step 5: Follow wizard through install

![Pasted image 20250726113250.png](/img/user/Assets/Pasted%20image%2020250726113250.png)

## Step 6: Open Docker Desktop

![{AF97A6D9-732B-4623-BD3A-D82B478665F8}.png](/img/user/Assets/%7BAF97A6D9-732B-4623-BD3A-D82B478665F8%7D.png)

## Step 7: Click Skip or Sign in

> [!WARNING]  Information about Docker accounts
> From what we can tell, creating a Docker account doesn't add any features

![Pasted image 20250726113601.png](/img/user/Assets/Pasted%20image%2020250726113601.png)
# Start Interactive container (First time install)

## Step 1: Open Terminal

![{327A8E63-A85B-4E22-B43C-1138D9763317}.png](/img/user/Assets/%7B327A8E63-A85B-4E22-B43C-1138D9763317%7D.png)

> [!IMPORTANT] Important note about mounted folders and where they point
> C:\nerf_projects\ points to /workspace/
> C:\nerf_outputs points to /outputs/
> C:\nerf_renders points to /renders/
> This makes accessing Nerfstudio's input and output folders easier.
# Step 2: Run the following command

> [!Question] Why?
> To create a new docker container called nerfstudio with the required permitions

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
## Update repository and install dependencies

```
apt update
apt install -y git
```
# Launching it

Next time you want to launch it, use the following command:


> [!DANGER] Important READ
> If running the below command gives out this error:
> 
> `PS C:\Users\oimwio> docker start nerfstudio; docker exec -it nerfstudio bash`
`error during connect: Post "http://%2F%2F.%2Fpipe%2FdockerDesktopLinuxEngine/v1.51/containers/nerfstudio/start": open //./pipe/dockerDesktopLinuxEngine: The system cannot find the file specified.`
`Error: failed to start containers: nerfstudio`
`error during connect: Get "http://%2F%2F.%2Fpipe%2FdockerDesktopLinuxEngine/v1.51/containers/nerfstudio/json": open //./pipe/dockerDesktopLinuxEngine: The system cannot find the file specified.`
Try to open the docker desktop app and try again !


```
docker start nerfstudio; docker exec -it nerfstudio bash
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
> You should put you source video into C:\nerf_projects\sourcevideo

```
ns-process-data video --data /workspace/sourcevideo/video.mp4 --output-dir /workspace/exportedvideonerf
```
# Train and serve Web UI

> [!WARNING] WARNING
> Use the command below if you used the "Using a video (most compatible and easy but gives out possibly worse results)" method, or else it won't work!

## If you used a video

```
ns-train nerfacto --data /workspace/exportedvideonerf
```

## If you used photos

```
ns-train nerfacto --data /workspace/exportedphotonerf
```

> [!WARNING] WARNING
> Please do not close this window or else you will stop the training
> 
> ![{AEDB6E3E-A005-4BB1-B4A7-38B14922ED61}.png](/img/user/Assets/%7BAEDB6E3E-A005-4BB1-B4A7-38B14922ED61%7D.png)

# How to open Web UI?

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
> If you don't see anything on your browser, please wait until your terminal shows aa green bar at the bottom saying ![{DB684E24-8831-4CE2-95FA-3957C8F4A46B}.png](/img/user/Assets/%7BDB684E24-8831-4CE2-95FA-3957C8F4A46B%7D.png) like this:
> 
> ![{9240933E-126C-4F27-B13F-3DEA6A7CFC06}.png](/img/user/Assets/%7B9240933E-126C-4F27-B13F-3DEA6A7CFC06%7D.png)

# Understanding the command prompt

> [!NOTE] Understanding the command prompt
> The text highlighted in red shows the completion percentage of the Nerf
> 
> ![Pasted image 20250726205520.png](/img/user/Assets/Pasted%20image%2020250726205520.png)
> 
> The text highlighted in red shows the Estimated Time to Finish (Arrival) (ETA)
> 
> ![Pasted image 20250726232653.png](/img/user/Assets/Pasted%20image%2020250726232653.png)

# Official Nerfstudio Viewer Tutorial (legacy)

> [!LINK] Official Nerfstudio Viewer Tutorial (legacy)
> https://youtu.be/nSFsugarWzk?t=63
> The viewer is newer in our installation and the one shown in the video can be opened using the `--vis viewer_legacy` flag so the command 
> `ns-train nerfacto --data /workspace/exportedvideonerf` becomes `ns-train nerfacto --data /workspace/exportedvideonerf --vis viewer_legacy`
> And yes video is intended to start at 1:03 to avoid repetition and possibly outdated instructions
# Compatibility

> [!QUESTION] Important note about GPU compatibility
> We are still not sure about GTX 10XX compatibility
> as well as RTX 50XX compatibility?
>As of the time of writing 7/27/2025 12:16:32 GMT+1

![IMG_20250727_010009 1.jpg](/img/user/Assets/IMG_20250727_010009%201.jpg)
ns-viewer --load-config

WIP
Made with ❤️ in [Morocco](https://www.google.com/search?q=Morocco&client=firefox-b-d&sca_esv=0c2e3acf227f4533&sxsrf=AE3TifPxQHRmqHBLU2o4tpsh0hnbHAfeew%3A1753568930760&ei=olaFaJOgLoqIkdUP2br16AM&ved=0ahUKEwiT-dOpyduOAxUKRKQEHVldHT0Q4dUDCBA&uact=5&oq=Morocco&gs_lp=Egxnd3Mtd2l6LXNlcnAiB01vcm9jY28yChAjGIAEGCcYigUyChAuGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyDhAuGIAEGMcBGMsBGK8BSP8fULAFWP8JcAF4AZABAJgBfaAB0QKqAQMwLjO4AQPIAQD4AQGYAgSgAt8CwgIKEAAYsAMY1gQYR8ICDRAAGIAEGLADGEMYigXCAgYQABgHGB7CAgcQLhiABBgKwgIHEAAYgAQYCsICDRAuGIAEGMcBGAoYrwGYAwCIBgGQBgySBwMxLjOgB7slsgcDMC4zuAfbAsIHAzItNMgHDQ&sclient=gws-wiz-serp) 
No AI chatbot was used to write these sentences (but not the commands)