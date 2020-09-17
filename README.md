# turtlebot3 installation with ROS melodic in Ubuntu 18.04
This instruction is adapted from https://automaticaddison.com/how-to-launch-the-turtlebot3-simulation-with-ros/

1. Make sure that you have installed ROS already. If not, please see http://wiki.ros.org/melodic/Installation/Ubuntu

2.TurtleBot3 simulator installation:

-(1) Open a terminal window under yourhome folder,Create a workspace: 
```bash
    mkdir turtle_ws
    cd turtle_ws/
    mkdir src
    cd src
 ```
 -(2) git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
 
 -(3) git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
 
 -(4) back to the turtle_ws and catkin_make
 ```bash
     cd ~turtle_ws
     catkin_make
 ```
 -(5) TurtleBot3 has three models, Burger, Waffle, and Waffle Pi, so you have to set which model you want to use before you launch TurtleBot3. Type this command to open the bashrc file to add this setting:
 ```bash
     gedit ~/.bashrc
 ```
     Add this line at the bottom of the file:
 ```bash
     export TURTLEBOT3_MODEL=burger
 ```
  Save the file and close it. And re-source it usiing:
  ```bash
     source ~/.bashrc
  ```
 -(6) Now, we need to download the TurtleBot3 simulation files.
 ```bash
      cd ~/turtle_ws/src/
      git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
      cd ~/turtle_ws && catkin_make
 ```
      
 3. Simulate TurtleBot3 using RViz
 
    Before everything, first 
    ```bash
    source ~turtle_ws/devel/setup.bash
    ```
    
    you can run this in the terminal or put it to the ~/.bashrc and re-source the bashrc
 
    Now that we have the TurtleBot3 simulator installed, let’s launch the virtual robot using RViz. Type this command in your terminal window:
    ```bash
    roslaunch turtlebot3_fake turtlebot3_fake.launch
    ```

    If you want to move TurtleBot3 around the screen, open a new terminal window, and type the following command (everything on one line in the terminal):
    ```bash
    roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
    ```
    
    
4. Simulate TurtleBot3 using Gazebo

 
 Now let’s use Gazebo to do the TurtleBot3 simulation.

 First, let’s launch TurtleBot3 in an empty environment. Type this command (everything goes on one line):
 ```bash
 roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
 ```
 

5. How to Change the Simulation Environment for TurtleBot3

   Let’s look at our TurtleBot3 in a different environment. This environment is often used for testing SLAM and navigation algorithms. Simultaneous localization and mapping (SLAM) concerns the problem of a robot building or updating a map of an unknown environment while simultaneously keeping track its location in that environment.

In a new terminal window type:
```bash
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

We can also simulate TurtleBot3 inside a house. Type this command and wait a few minutes for the environment to load.
```bash
roslaunch turtlebot3_gazebo turtlebot3_house.launch
```

To move the TurtleBot with your keyboard, use this command in another terminal tab:
```bash
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

We can open RViz to visualize the LaserScan topic while TurtleBot3 is moving about in the world. In a new terminal tab type:
```bash
roslaunch turtlebot3_gazebo turtlebot3_gazebo_rviz.launch
```
 
 
 
