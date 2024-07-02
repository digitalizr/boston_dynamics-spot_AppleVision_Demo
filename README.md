
## Build the Docker Image
go to the docker file add run this:

```sh
docker build -t spot_simulation .
```


afte that run the image

```sh
docker run --name spot_simulation_server -it -p 10000:10000 spot_ros_simulation 
```


## Insid ethe Docker Container
run this inside the docker container
```sh
docker exec -it spot_simulation_server bash
```

```sh
cd ~/spot_ws/src
git clone https://github.com/Unity-Technologies/ROS-TCP-Endpoint.git
git clone https://github.com/SoftServeSAG/teleop_legged_robots.git
apt-get install -y ros-melodic-catkin python-catkin-tools
cd ..
catkin_make
source devel/setup.bash
hostname -I
export ROS_MASTER_URI=http://172.17.0.3:11311
export ROS_IP=172.17.0.3
```



## Open 3 Terminal of the same Docker container above
```sh
roslaunch ros_tcp_endpoint endpoint.launch
```

```sh
roslaunch rs_inverse inverse.launch robot_name:="spot1"
```

```sh
roslaunch rs_base quadruped_controller.launch
```

```sh
roslaunch teleop_legged_robots teleop.launch robot_name:="spot1"
```

## Getting option 2 working better

I have found a couple things help get option two working:

1. If you activate the Subscribers gameobject in Unity, I have foot collisions as well as model states publishing to the controller scripts. This seems to make it a bit more stable.
2. With the linear velocity set to 10 and the angular velocity set to 1.5 on the teleop_legged_robot script, it moves more normally but still drifts to the left. 
3. If you are using a laptop, and are plugged into a seperate monitor, unplug it. This can sometimes make the command behavior more stable. 



## Tutorials
https://www.youtube.com/watch?v=qWuudNxFGOQ&t=370s

https://www.youtube.com/watch?v=3MYeBxFVBHI&t=6s