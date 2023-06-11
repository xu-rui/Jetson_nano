# Jetson_nano
通过jetson nano配置yoolov5s的使用环境，并使用TensorRT模型进行加速



//借鉴了一个现有的开源项目开源项目:《CDR（cv-detect-robot）》https://github.com/guojianyang/cv-detect-robot
所需软件环境：
    Jetpack4.5(ubuntu 18.04)
    TensorRT7.1
    CUDA 10.2
    cuDNN 8.0
    OpenCV 4.1.1
    deepsteaam 5.0

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

第二步：安装DeepStream On Jetson nano(根据自己的版本进行安装)
https://developer.nvidia.com/embedded/deepstream-on-jetson-downloads-archived
我下载的是deepstream5.0
![image](https://github.com/xu-rui/Jetson_nano/assets/73344517/5867f8a1-8e86-42e4-bc52-7b9847aca8f2)
<br>安装依赖项<br>

sudo apt install \
libssl1.0.0 \
libgstreamer1.0-0 \
gstreamer1.0-tools \
gstreamer1.0-plugins-good \
gstreamer1.0-plugins-bad \
gstreamer1.0-plugins-ugly \
gstreamer1.0-libav \
libgstrtspserver-1.0-0 \
libjansson4=2.11-1

安装DeepStream SDK
(1)进入官网https://developer.nvidia.com/embedded/deepstream-on-jetson-downloads-archived选择deep stream 5.0 for Jetson并下载
![image](https://github.com/xu-rui/Jetson_nano/assets/73344517/1b98f83b-d2dd-4f22-81af-6ee6cd3038ae)
（2）下载后得到压缩文件deepstream_sdk_5.0_jetson.tbz2，输入以下命令以提取并安装DeepStream SDK
sudo tar -xvf deepstream_sdk_5.0_jetson.tbz2 -C /
cd /opt/nvidia/deepstream/deepstream-5.０
sudo ./install.sh
sudo ldconfig
(3)DeepStream测试
cd /opt/nvidia/deepstream/deepstream-5.０/sources/objectDetector_Yolo
执行编辑命令
sudo  CUDA_VER=10.2 make -C nvdsinfer_custom_impl_Yolo
![image](https://github.com/xu-rui/Jetson_nano/assets/73344517/6b7e97f5-719e-433b-a52c-bb6634e51981)


