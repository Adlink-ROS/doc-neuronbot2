# PC Setup
<!--talk shit -->

## Install Ubuntu 18.04
Ubuntu is the most compatible system to run ROS. Follow the tutorial to install Ubuntu on your PC. 

**NeuronBot2 are designed and tested on Ubuntu 18.04 (BionicBeaver).**

* [Install Tutorial](https://ipi.wiki/neuron_pi/)
* [Official Download Link](https://ubuntu.com/download/desktop)


## Install ROS2&1
NeuronBot2 is designed to run independently on both ROS1 and ROS2, which allows Users to explore the new features on ROS2 but still have the immerse supported packages on ROS1. 

**NeuronBot2 are designed and tested on** ***ROS2--Dashing*** **and** ***ROS--Melodic*** **version.**
* [Official ROS2 Installation Tutorial](https://index.ros.org/doc/ros2/Installation/Dashing/)
* [Official ROS Installation Tutorial](http://wiki.ros.org/melodic/Installation/Ubuntu)

## Install NeuronBot2 package
### ROS2 branch
Create workspace.
```
mkdir -p ~/neuronbot2_ros2_ws/src
```
Install dependencies.
```
sudo apt install python3-colcon-extensions python-rosdep2
```
Clone the package.
```
cd ~/neuronbot2_ros2_ws/
wget https://gist.githubusercontent.com/airuchen/dd5e7962706b32ffaa8d46ba905fea91/raw/d21c4fe2ca0d494202cf84c734c9e8cbca769ff1/NeuronBot2_ros2.repos
vcs import src < NeuronBot2_ros2.repos
```
Build it.
```
source /opt/ros/dashing/setup.bash
rosdep update
rosdep install --from-paths src --ignore-src -r -y # It might take some time.
cd ~/neuronbot2_ros2_ws/
colcon build --symlink-install --cmake-args -DCMAKE_BUILD_TYPE=Release
source ~/neuronbot2_ros2_ws/install/local_setup.bash
```
[***Troubleshooting: colcon: command not found***](https://index.ros.org/doc/ros2/Tutorials/Colcon-Tutorial/)

### ROS1 branch

Create workspace
```
mkdir -p ~/neuronbot2_ros1_ws/src
cd ~/neuronbot2_ros1_ws/src
```
Clone the package
```
git clone -b melodic-dev https://github.com/airuchen/neuronbot2.git
```
Install dependencies
```
cd ~/neuronbot2_ros1_ws/
rosdep update
rosdep install --from-paths src --ignore-src -r -y 
```
Catkin_make
```
cd ~/neuronbot2_ros1_ws/
source /opt/ros/melodic/setup.bash
catkin_make
source devel/setup.bash
```

## Install Bash Configuration Tool
[ADLINK bash configration tutorial](setup_pc_bash.md)