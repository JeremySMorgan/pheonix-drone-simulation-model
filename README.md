# Pheonix Drone Simulation 

## Requirements
1) Ubuntu 16.04 or 18. (not tested with 18.)

2) Gazebo 8, install from [[http://gazebosim.org/tutorials?cat=install&tut=install_ubuntu&ver=8.0](http://gazebosim.org/tutorials?cat=install&tut=install_ubuntu&ver=8.0)]. The ardupilot gazebo plugin failed to build for Gazebo7 and Gazebo9. Installation instructions:

```
sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
sudo apt update
sudo apt install gazebo8 libgazebo8-dev
```


## Setup

1) 
Install and build the gazebo ArduPilot plugin, use the forked version from [https://github.com/SwiftGust/ardupilot_gazebo](https://github.com/SwiftGust/ardupilot_gazebo).  I encountered a number of errors when building from the original package from [khancyr](https://github.com/khancyr).

Add the following lines to your .bashrc:

```
export GAZEBO_MODEL_PATH=<path to>/pheonix-drone-simulation-model/models:${GAZEBO_MODEL_PATH}
export GAZEBO_RESOURCE_PATH=<path to>/pheonix-drone-simulation-model/worlds:${GAZEBO_RESOURCE_PATH}
```
 *dont forget to `source ~/.bashrc` after making changes :)*


2)
Download ArduPilot ([https://github.com/ArduPilot/ardupilot](https://github.com/ArduPilot/ardupilot)). Overview: [https://ardupilot.org/dev/docs/setting-up-sitl-on-linux.html](https://ardupilot.org/dev/docs/setting-up-sitl-on-linux.html). Save an alias to the sim_vehicles.py script by adding the following line to .bashrc:

```
alias sv="python3.6 <path to>/ardupilot/Tools/autotest/sim_vehicle.py"
```

Also, install pymavlink and MAVProxy:

```python3.6 -m pip install --upgrade pymavlink MAVProxy --user```



## Running


***launch gazebo:*** <br />
In first terminal: <br />
`gazebo --verbose motherdrone_ardupilot.world` <br />


***run  ardupilot sitl:*** <br />
In second terminal: <br />
`sv -f Gazebo -v ArduCopter --map --console` <br />

If everything works, the MAV terminal should open. in the terminal, run: <br />
`mode guided`    # enable manual control. <br />
`param load <relative path to>/pheonix-drone-simulation-model/configs/motherdrone.parm`    # load PID values <br />
*wait 45s-1m for drone to calibrate* <br />
`arm throttle`  # arm the drone <br />
`takeoff 1`           # takeoff and hover at 1m. Must be run within 10 seconds of arming or drone will disarm <br />

At this point the drone should takeoff! 

see https://ardupilot.org/dev/docs/copter-sitl-mavproxy-tutorial.html for a list of commands. 


## Demo

See https://www.youtube.com/watch?v=qSprZL5BsmU&t=1s for a demo of the simulation running