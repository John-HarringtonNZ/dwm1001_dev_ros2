# dwm1001_dev_ros2

This is a ROS2 driver for the DWM1001-Dev positioning system. Base code and README come from [ROS version repository](https://github.com/TIERS/ros-dwm1001-uwb-localization).

## Installation

This instructions are for Ubuntu 20.04 with ROS Galactic/Foxy already installed.

Clone this repo into your catkin_ws (the code below creates a new ROS2 workspace named `uwb_ws` in your home folder):
```
mkdir -p  ~/uwb_ws/src && cd ~/uwb_ws/src
git@github.com:John-HarringtonNZ/dwm1001_dev_ros2.git

and install dependencies
```
sudo apt install python-dev python-pip
sudo -H python -m pip install --upgrade pip
sudo -H python -m pip install pyserial
```

Then build the workspace

then run
```
cd ~/uwb_ws
colcon build
```

## Get Started

Follow the steps in [Decawave's DRTLS Guide](https://www.decawave.com/wp-content/uploads/2018/08/mdek1001_quick_start_guide.pdf) to setup a DRTLS system with at least 3 anchors and 1 active tag. 

We recommend setting the tag's position update rate to 10 Hz in stationary mode too.

## Scripts

This repository contains ROS nodes written in Python to interface with the two types of UWB Tags running Decawave's default RTLS firmware. The nodes communicate with the tags throught Decawave's UART API.

`ros2 launch uwb_beacon_rtls uwb_beacon_rtls.launch.py`

The tags publish their raw positions to '/uwb_beacon/raw_tags/tag_*`, where `*` is the sequential tag based on the tag ids configured in the `config` page. 