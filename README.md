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
Reopen your terminal
## unitree-ros2-dls
After finishing basic-locomotion-isaaclab installation, go to back to the folder for the repo.
Create the conda environment for unitree-ros2-dls
```
cd unitree-ros2-dls
conda env create -f installation/mamba_environment_humble.yaml
```
Use a text editor to change the unitree_legged_sdk/CMakeLists.txt and add this after line 5:
```
find_package(lcm REQUIRED CONFIG
  PATHS
    /usr/lib/${CMAKE_LIBRARY_ARCHITECTURE}/lcm/cmake
    /usr/lib/x86_64-linux-gnu/lcm/cmake
)
if(EXISTS "/usr/include/lcm/lcm-cpp.hpp")
  add_compile_options($<$<COMPILE_LANGUAGE:CXX>:-I/usr/include>)
endif()
```
Then go to the unitree_legged_sdk root folder and compile the library:
```
rm -rf build
cmake -S . -B build -DCMAKE_POLICY_VERSION_MINIMUM=3.5 -DCMAKE_CXX_COMPILER=/usr/bin/g++ -DCMAKE_C_COMPILER=/usr/bin/gcc -DCMAKE_CXX_FLAGS="-I/usr/include"
cmake --build build -j$(nproc)
```
After compilation, compile aliengo_hal.cpp in unitree-ros2-dls/ros2_ws folder
```
rm -rf build install log
colcon build --symlink-install
source install/setup.bash
```
# Deploying
## Deploying
Open aliengo-training/unitree-ros2-dls and run the bash script
```
./unitree_ros2_connect.bash
```
(You will have to run this bash script everytime





