FROM osrf/ros:melodic-desktop

RUN apt-get update
RUN apt-get install -y git && apt-get install -y python3-pip  
RUN cd  home
RUN mkdir -p spot_ws/src && cd spot_ws/src
RUN git clone https://github.com/Unity-Technologies/ROS-TCP-Endpoint.git
RUN git clone -b spot_control https://github.com/SoftServeSAG/spot_simulation.git
RUN git clone https://github.com/SoftServeSAG/teleop_legged_robots.git
RUN apt-get install -y ros-melodic-catkin python-catkin-tools
RUN cd ..
#RUN catkin_make
RUN echo "Successfull"


