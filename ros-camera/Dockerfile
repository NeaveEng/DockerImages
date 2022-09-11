FROM balenalib/raspberry-pi-python:3.7-buster-build

RUN apt update && apt install python3-numpy
RUN python3 -m pip install picamera 
RUN python3 -m pip install picamera[array]
RUN python3 -m pip install --extra-index-url https://rospypi.github.io/simple/ rospy rosbag sensor_msgs
RUN python3 -m pip install --extra-index-url https://rospypi.github.io/simple/ geometry_msgs

WORKDIR /stereopi_node
COPY . ./

CMD [ "python3", "stereopi_node.py" ]
