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

## 7. Close Turtlesim
You can exit the simulation by typing q in the teleop terminal and Ctrl + C in the turtlesim node terminal, respectively.
