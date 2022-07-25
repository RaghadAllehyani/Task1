# task 1
Here we explain how to install ros2 on Jetson Nano:
Steps of installing ros2 on Jetson Nano:
install xubuntu in Jetson Nano
download balena
ROS2 install
Set locale
Make sure you have a locale that supports UTF-8.
check for UTF-8:
sudo apt update && sudo apt install locales sudo locale-gen en_US en_US.UTF-8 sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 export LANG=en_US.UTF-8
verify settings:
Setup Sources
apt-cache policy | grep universe

This should output a line like the one below:
500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=amd64

If you do not see the output write the following instruction:
sudo apt install software-properties-common sudo add-apt-repository universe

add the ROS2 apt repository to your system:
sudo apt update && sudo apt install curl gnupg2 lsb-release sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

add the repository to your sources:
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

Install ROS2 packages
Update your apt repository caches after setting up the repositories:
sudo apt update

ROS2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages
sudo apt upgrade

Desktop Install (Recommended): ROS, RViz, demos, tutorials
sudo apt install ros-foxy-desktop

ROS-Base Install (Bare Bones): Communication libraries, message packages, command line tools. No GUI tools.
sudo apt install ros-foxy-ros-base

Environment setup:
Sourcing the setup script Set up your environment by sourcing the following file:
source /opt/ros/foxy/setup.bash


