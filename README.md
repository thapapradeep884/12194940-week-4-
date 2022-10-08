# Turtlesim and RQT

We must confirm that the Terminal is in ROS2 DISTRO prior to beginning a Turtlesim installation.
To check your Terminal's route (ROS1 or ROS2? Run the following code:
```
printenv | grep -i ROS
```
(![image](https://github.com/thapapradeep884/IMAGE/blob/main/t1.png)


## 1. Install Turtlesim

Source your files after confirming that you are in the ROS2 Distro, and then install the Turtlesim package.

```
sudo update
sudo apt install ros-foxy-turtlesim
```

In order to check list of installed packages:
```
ros2 pkg executables turtlesim
```
![image](https://github.com/thapapradeep884/IMAGE/blob/main/Screenshot%20from%202022-09-25%2017-02-54.png)

## 2. Start Turtlesim

To start turtlesim, enter the following command in your terminal:
```
ros2 run turtlesim turtlesim_node
```
The simulator window with a turtle will appear 

![image](https://github.com/thapapradeep884/IMAGE/blob/main/Screenshot%20from%202022-09-25%2017-03-37.png)

In the terminal under the command, you will see messages from the node:
```
[INFO] [turtlesim]: Starting turtlesim with node name /turtlesim

[INFO] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
```

## 3. Use Turtlesim
1. Open a new terminal
2. Run a new code to control the turtle
```
ros2 run turtlesim turtle_teleop_key
```
![image](https://github.com/thapapradeep884/IMAGE/blob/main/Screenshot%20from%202022-09-25%2017-12-16.png)

## 4. Install RQT
Open a new terminal to install rqt and its plugins:
```
sudo apt update
sudo apt install ~nros-foxy-rqt*
```

To run rqt:
```
rqt
```


## 5. Use RQT

Select: Plugins > Services > Service from the menu bar at the top as shown below

![image](https://github.com/thapapradeep884/IMAGE/blob/main/Screenshot%20from%202022-09-25%2017-15-39.png)

Now click on the Service dropdown list to see turtlesim’s services, and select the /spawn service.

## 5.1. Try the spawn service

The turtlesim window will spawn a new turtle when you type /spawn.
![image](https://github.com/thapapradeep884/IMAGE/blob/main/Screenshot%20from%202022-09-25%2018-11-22.png)

![image](https://github.com/thapapradeep884/IMAGE/blob/main/Screenshot%20from%202022-09-25%2018-13-53.png)

## 5.2. Try the teleport_relative service

Let's use the /teleport_relative service to assign turtle1 a special pen now:
![image](https://github.com/thapapradeep884/IMAGE/blob/main/Screenshot%20from%202022-09-25%2018-15-06.png)

## 6. Close Turtlesim
You can exit the simulation by typing q in the teleop terminal and Ctrl + C in the turtlesim node terminal, respectively.

#Using colcon to build packages
##Background
##Iterations of the ROS build tools like catkin make, catkin make isolated, catkin tools, and ament tools include colcon.
##Prerequisites
##Install colcon
```
sudo apt install python3-colcon-common-extensions
```
![image](https://github.com/thapapradeep884/IMAGE/blob/main/11.PNG)

##Install ROS 2
##You must set up ROS 2 in order to build the examples.
##Create a workspace
##To house our workspace, first create the directory ros2 ws:

```
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
```

![image](https://github.com/thapapradeep884/IMAGE/blob/main/12.PNG)
##The workspace currently only has the empty directory src:
##Add some sources

##Clone the examples repository into the workspace's src directory as follows:
```
git clone https://github.com/ros2/examples src/examples -b foxy
```

![image](https://github.com/thapapradeep884/IMAGE/blob/main/13.PNG)

##Now the workspace should have the source code to the ROS 2 examples:
```
.
└── src
    └── examples
        ├── CONTRIBUTING.md
        ├── LICENSE
        ├── rclcpp
        ├── rclpy
        └── README.md

4 directories, 3 files
```

## Build the workspace

```
colcon build --symlink-install
```

![image](https://github.com/thapapradeep884/IMAGE/blob/main/14.PNG)

We should see the build, install, and log directories once the build is complete:
```
.
├── build
├── install
├── log
└── src

4 directories, 0 files
```
## Run tests
Test the newly created packages by executing the following:

```
colcon test
```

## Source the environment

```
. install/setup.bash
```

# Try a demo
We can execute executables created by colcon using the environment supplied. Let's test one of the examples' subscriber nodes:

```
ros2 run examples_rclcpp_minimal_subscriber subscriber_member_function
```
Let's launch a publisher node in another terminal (don't forget to source the setup script):

```
ros2 run examples_rclcpp_minimal_publisher publisher_member_function
```

You should see messages from the publisher and subscriber with numbers incrementing.

SUBSCRIBER TERMINAL

![image](https://github.com/thapapradeep884/IMAGE/blob/main/17.PNG)

PUBLISHER TERMINAL

![image](https://github.com/thapapradeep884/IMAGE/blob/main/15.PNG)

# Create your own package
```
echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
echo "export _colcon_cd_root=/opt/ros/foxy/" >> ~/.bashrc
```

## Setup colcon tab completion

```
echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc
```
