# OpenCV 4.1 on ODROID-XU4
## How to compile and install OpenCV 4.1.2 on Ubuntu Mate 18.04 LTS with Python 3.6.8 under ODROID XU4.

### 1. Start updating the system packages manager with the following commands on terminal:

```bash
sudo apt update
sudo apt upgrade
```

### 2. Install these tools:

```bash
sudo apt -y install build-essential cmake gfortran pkg-config unzip software-properties-common doxygen
```

### 3. Update/install Python2/Python3 and Numpy developing libraries with:

```bash
sudo apt -y install python-dev python-pip python3-dev python3-pip python3-testresources
sudo apt -y install python-numpy python3-numpy
```
  
### 4. 

```bash
sudo apt -y install libblas-dev libblas-test liblapack-dev libatlas-base-dev libopenblas-base libopenblas-dev
```
  
### 5. 

```bash
sudo apt -y install libjpeg-dev libpng-dev libtiff-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt -y install libxvidcore-dev libx264-dev
sudo apt -y install libgtk2.0-dev libgtk-3-dev libcanberra-gtk*
sudo apt -y install libtiff5-dev libeigen3-dev libtheora-dev libvorbis-dev sphinx-common libtbb-dev yasm libopencore-amrwb-dev
sudo apt -y install libopenexr-dev libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev libavutil-dev libavfilter-dev
sudo apt -y install libavresample-dev ffmpeg libdc1394-22-dev libwebp-dev
sudo apt -y install libjpeg8-dev libxine2-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libprotobuf-dev
sudo apt -y install protobuf-compiler libgoogle-glog-dev libgflags-dev libgphoto2-dev libhdf5-dev
sudo apt -y install qt5-default v4l-utils
sudo apt -y install libtbb2
```
  
### 6. Install legacy libraries from Ubuntu 16.08

```bash
sudo add-apt-repository "deb http://ports.ubuntu.com/ubuntu-ports xenial-security main"
sudo apt -y update
sudo apt -y install libjasper-dev libjasper
```

### 7. Download official OpenCV 4.1.2 sources

```bash
wget -O opencv.zip https://github.com/opencv/opencv/archive/4.1.2.zip
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.1.2.zip
```
