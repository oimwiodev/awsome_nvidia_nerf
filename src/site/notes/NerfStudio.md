---
{"dg-publish":true,"permalink":"/nerf-studio/"}
---


# Context
Nerfstudio provides a simple API that allows for a simplified end-to-end process of creating, training, and testing NeRFs. The library supports a **more interpretable implementation of NeRFs by modularizing each component.** With more modular NeRFs, we hope to create a more user-friendly experience in exploring the technology.

This is a contributor-friendly repo with the goal of building a community where users can more easily build upon each other’s contributions. Nerfstudio initially launched as an opensource project by Berkeley students in [KAIR lab](https://people.eecs.berkeley.edu/~kanazawa/index.html#kair) at [Berkeley AI Research (BAIR)](https://bair.berkeley.edu/) in October 2022 as a part of a research project ([paper](https://arxiv.org/abs/2302.04264)). It is currently developed by Berkeley students and community contributors.

We are committed to providing learning resources to help you understand the basics of (if you’re just getting started), and keep up-to-date with (if you’re a seasoned veteran) all things NeRF. As researchers, we know just how hard it is to get onboarded with this next-gen technology. So we’re here to help with tutorials, documentation, and more!

Have feature requests? Want to add your brand-spankin’-new NeRF model? Have a new dataset? **We welcome [contributions](https://docs.nerf.studio/reference/contributing.html)!** Please do not hesitate to reach out to the nerfstudio team with any questions via [Discord](https://discord.gg/uMbNqcraFc).

Have feedback? We’d love for you to fill out our [Nerfstudio Feedback Form](https://forms.gle/sqN5phJN7LfQVwnP9) if you want to let us know who you are, why you are interested in Nerfstudio, or provide any feedback!

We hope nerfstudio enables you to build faster 🔨 learn together 📚 and contribute to our NeRF community 💖.
# Start Interactive container

> [!WARNING] MAKE SURE TO UPDATE USER TO YOUR WINDOWS USERNAME

```
docker run --gpus all `
    -u root `
    -v "C:\Users\USER\nerf_projects:/workspace/" `
    -v "C:\Users\USER\.cache:/home/user/.cache/" `
    -p 7008:7007 `  # <--- CHANGED THIS PORT
    --rm `
    -it `
    --shm-size=12gb `
    ghcr.io/nerfstudio-project/nerfstudio:latest
```

# Update repository and install dependencies
```
apt update
```

```
apt install -y git
```

```
python3 -m pip install git+https://github.com/kerrj/lerf
```

###### Combined command:
```
apt update
apt install -y git
python3 -m pip install git+https://github.com/kerrj/lerf
```


# Run colmap analysis
```

```