# OpenCV 4.1 on ODROID-XU4
## How to compile and install OpenCV 4.1.2 on Ubuntu Mate 18.04 LTS with Python 3.6.8 under ODROID XU4.

### 1. Start updating your system with the following commands on terminal:

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

### 7. Create a folder (in any place you want) that should receive the future compiled OpenCV 4.1.2 library:
```bash
mkdir opencv_package
```

### 8. Download official OpenCV 4.1.2 zipped source files:

```bash
wget -O opencv.zip https://github.com/opencv/opencv/archive/4.1.2.zip
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.1.2.zip
```

### 9. Unzip downloaded source files:
```bash
unzip opencv.zip
unzip opencv_contrib.zip
```

### 10. Rename unziped folders for your convenience:
```bash
mv opencv-4.1.2 opencv
mv opencv_contrib-4.1.2 opencv_contrib
```

### 11. Go into unziped OpenCV source folder and create a temporary folder that should be used by compiler:
```bash
cd opencv
mkdir build
cd build
```

### 12. 
```bash
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D OPENCV_ENABLE_NONFREE=ON \
-D OPENCV_EXTRA_MODULES_PATH=/home/odroid/Desktop/opencv_contrib/modules \
-D PYTHON_EXECUTABLE=/usr/bin/python3.6 \
-D PYTHON2_EXECUTABLE=/usr/bin/python2.7 \
-D PYTHON3_EXECUTABLE=/usr/bin/python3.6 \
-D PYTHON_PACKAGES_PATH=/usr/lib/python3/dist-packages \
-D PYTHON_LIBRARY=/usr/lib/python3.6/config-3.6m-arm-linux-gnueabihf/libpython3.6m.so \
-D PYTHON_INCLUDE_DIR=/usr/include/python3.6 \
-D PYTHON3_NUMPY_INCLUDE_DIRS=/usr/lib/python3/dist-packages/numpy/core/include \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D OPENCV_PYTHON3_INSTALL_PATH=/home/odroid/Desktop/opencv_package \
-D INSTALL_PYTHON_EXAMPLES=OFF \
-D INSTALL_C_EXAMPLES=OFF \
-D BUILD_DOCS=NO \
-D BUILD_TIFF=ON \
-D WITH_FFMPEG=ON \
-D WITH_GSTREAMER=ON \
-D WITH_TBB=ON \
-D BUILD_TBB=ON \
-D WITH_V4L=ON \
-D WITH_LIBV4L=ON \
-D WITH_VTK=OFF \
-D WITH_OPENGL=ON \
-D BUILD_NEW_PYTHON_SUPPORT=ON \
-D BUILD_TESTS=OFF \
-D BUILD_EXAMPLES=OFF ..
```

### 13.
```bash
make -j4
```

### 14.
```bash
sudo make install
sudo ldconfig
sudo apt update
```
