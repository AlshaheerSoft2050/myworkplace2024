Step-by-Step Guide for Installing ROS Noetic and ROS 2 Foxy on Ubuntu 20.04
1. Setting Up ROS Noetic
1.1 Update and Upgrade the System
bash
Copy code
sudo apt update
sudo apt upgrade
1.2 Setup Sources
bash
Copy code
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
1.3 Setup Keys
bash
Copy code
sudo apt install curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
1.4 Install ROS Noetic
bash
Copy code
sudo apt update
sudo apt install ros-noetic-desktop-full
1.5 Initialize rosdep
bash
Copy code
sudo rosdep init
rosdep update
1.6 Setup Environment
Add the following line to your .bashrc file:
bash
Copy code
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
1.7 Install Dependencies for Building Packages
bash
Copy code
sudo apt install python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
1.8 Create a Catkin Workspace
bash
Copy code
mkdir -p ~/ros_noetic_ws/src
cd ~/ros_noetic_ws/
catkin_make
2. Setting Up ROS 2 Foxy
2.1 Update and Upgrade the System
bash
Copy code
sudo apt update
sudo apt upgrade
2.2 Setup Sources
bash
Copy code
sudo apt update && sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2-latest.list'
2.3 Install ROS 2 Foxy
bash
Copy code
sudo apt update
sudo apt install ros-foxy-desktop
2.4 Setup Environment
Add the following line to your .bashrc file:
bash
Copy code
echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
source ~/.bashrc
2.5 Install Dependencies for Building Packages
bash
Copy code
sudo apt install python3-colcon-common-extensions
2.6 Create a ROS 2 Workspace
bash
Copy code
mkdir -p ~/ros2_foxy_ws/src
cd ~/ros2_foxy_ws/
colcon build
3. Managing Workspaces
To manage the environment between ROS Noetic and ROS 2 Foxy, you can source the appropriate setup files:
For ROS Noetic:
bash
Copy code
source ~/ros_noetic_ws/devel/setup.bash
For ROS 2 Foxy:
bash
Copy code
source ~/ros2_foxy_ws/install/setup.bash
This setup ensures you have isolated workspaces for both ROS versions, allowing you to work on projects specific to each ROS version without interference.
