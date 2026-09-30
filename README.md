# aliengo-training
provides instructions on how to reproduce the aliengo training I have done.

# How to install
## Pre-requisites
* Ubuntu 24.04 LTS
* miniforge
* [Isaaclab 2.3.2 (use conda installation)](https://isaac-sim.github.io/IsaacLab/v2.3.2/index.html)
* git
# Installation
## basic-locomotion-isaaclab
Clone the repo with submodules somewhere in your home folder
```
git clone --recurse-submodules https://github.com/Y32CODE/aliengo-training.git
```
Install git-lfs
```
sudo apt install git-lfs
```
Using a python interpreter that has Isaac Lab installed, install the library
```
python -m pip install -e source/basic_locomotion_isaaclab
```
## unitree-ros2-dls
g
