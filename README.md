# Docker Images

These are the build files for various useful Docker images for ROS/robotics.

- ROS-Noetic
- - A build of ROS Noetic
- ROS-Camera
- - Based on ROS-Noetic, it allows access to the camera and MMAL on the Pi running a 64bit OS


# Notes
There is an issue (at the time of writing) with running the builds on Raspberry Pi Buster, [Linux Server FAQ](https://docs.linuxserver.io/faq#my-host-is-incompatible-with-images-based-on-ubuntu-focal) has this solution listed which you need to run on the host.

``sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 04EE7237B7D453EC 648ACFD622F3D138  
echo "deb http://deb.debian.org/debian buster-backports main" | sudo tee -a /etc/apt/sources.list.d/buster-backports.list  
sudo apt update  
sudo apt install -t buster-backports libseccomp2``