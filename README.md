# crazyflie_simulation

Hi! Welkom to the crazyflie simulation repo. This repo is still at the early stages and still in development so just ask if you are looking for anything in particular.

Currently it contains low resolution meshes based on the design of the actual [crazyflie 2.1](https://www.bitcraze.io/products/crazyflie-2-1/) but heavily simplified to contain as little vertices as possible, so it can be used to simulate a lot of them!

## Content

Currently contains:
* Meshes
    * Blender files
    * STL files
* [Webots](https://cyberbotics.com/) simulation files
    * Currently only attitude control with fixed height
* [Gazebo ignition](https://ignitionrobotics.org/) 
    * sdf files

So the mesh files looks a bit like this:


<img src="/meshes/blender_files/cf2_render.png" width="400" />

And the webots simulation looks like this:

![webots](crazyflie_webots.gif)

Near future plans:

Wish list (?):
* SITL and or HITL
* Simple physics model
* Deck models
* Intergration with Crazyflie-lib
* ?? (let us know in the issue tracker for any feature requests)

# Webots

Install webots from the [cyberbotics' website](https://cyberbotics.com/). We use version 2022a version.

Then just run the following

    webots webots/worlds/crazyflie_world.wbt
## Python controller
Go into the crazyflie_simulation/controllers/ folder and run the following:

    swig -python pid_controller.i
    python setup.py build_ext --inplace

Change controller in crazyflie robot model to crazyflie_controller_py to try it out. 
    

# Ignition Gazebo

1- First install ignition gazebo: https://ignitionrobotics.org/docs/fortress/install

2- Clone this repo: 
    git clone https://github.com/bitcraze/crazyflie_simulation.git

3- Put this repo in your ~/.bashrc and source it in your terminal

    export IGN_GAZEBO_RESOURCE_PATH="path/to/crazyflie_simulation/gazebo-ignition/"

4- Try out the crazyflie world with: 
    ign gazebo crazyflie_world.sdf

5- Spin motors and take off

    ign topic -t /crazyflie/gazebo/command/motor_speed --msgtype ignition.msgs.Actuators -p 'velocity:[2500,2500,2500,2500]'



## Measurements Crazyflie Assembly

The location of the parts

* Propeller origin from center (0.031, 0.031, 0.022) m
    * Mirrored in the x and y axis
* Motor mount + motor mounts (0.031, 0.031, 0.014) m
    * Mirrored in the x and y axis
* Body origin height from center ( 0, 0, 0.015) m
* Battery holder height ( 0, 0,0.025) m
* Battery height (0,0,0.02) m
* Pin headers (0, 0.011, 0.014) m
    * Mirrored in the y axis
