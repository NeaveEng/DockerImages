For setting permissions:
https://www.losant.com/blog/how-to-access-the-raspberry-pi-camera-in-docker

To run
`docker run --device=/dev/vchiq --privileged --rm --name stereopi -e ROS_MASTER_URL=http://192.168.1.112:11311 -e ROS_IP=192.168.1.112 ros-stereocam`
