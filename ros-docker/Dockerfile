FROM balenalib/raspberry-pi-python:3.8-buster

RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu buster main" > /etc/apt/sources.list.d/ros-latest.list' && \
    apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

RUN apt update && \
    apt-get install python3-rosdep python3-rosinstall-generator python3-vcstool build-essential -y

RUN rosdep init -y && \
    rosdep update -y

RUN mkdir -p ros_catkin_ws/src && \
    cd /ros_catkin_ws && \
    rosinstall_generator perception --rosdistro noetic --deps --tar > perception.rosinstall && \
    vcs import --input perception.rosinstall ./src && \
    apt update && \
    rosdep install --from-paths ./src --ignore-packages-from-source --rosdistro noetic --skip-keys="libpcl-all-dev libpcl-all" -y

RUN apt install libpcl-dev

RUN python3 -m pip install catkin-pkg
RUN cd /ros_catkin_ws && \
    ./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release -DPYTHON_EXECUTABLE=/usr/bin/python3

SHELL ["/bin/bash", "-c"]

RUN mkdir -p /catkin_ws/src && \
    source /ros_catkin_ws/devel_isolated/setup.bash && \
    cd /catkin_ws && \
    catkin_make
