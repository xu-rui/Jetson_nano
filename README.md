# Jetson_nano
通过jetson nano配置yoolov5s的使用环境，并使用TensorRT模型进行加速



//借鉴了一个现有的开源项目开源项目:《CDR（cv-detect-robot）》https://github.com/guojianyang/cv-detect-robot
/**
所需软件环境：
    Jetpack4.5(ubuntu 18.04)
    TensorRT7.1
    CUDA 10.2
    cuDNN 8.0
    OpenCV 4.1.1
    deepsteaam 5.0
*/

第一步：安装ROS操作系统
- sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
- sudo apt install curl 
- curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -(**若出现`gpg: no valid OpenPGP data found`可直接跳过 **)
- sudo apt update
- sudo apt install ros-melodic-desktop-full
- echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
- source ~/.bashrc
- source /opt/ros/melodic/setup.bash
- sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
- sudo apt install python-rosdep
- sudo rosdep init
- rosdep update
在终端运行roscore命令，若出现下图所示，说明ros安装正常
![image](https://github.com/xu-rui/Jetson_nano/assets/73344517/67f674b9-6270-4bfa-befe-0abd705a1d26)
