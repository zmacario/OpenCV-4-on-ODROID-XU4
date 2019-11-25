# OpenCV 4.1 on ODROID-XU4
## How to compile and install OpenCV 4.1.2 on Ubuntu 18.04.3 LTS (Bionic Beaver with Python 3.6.8) on the ODROID-XU4 platform.

### 1. Start updating your system with the following commands on terminal:
```bash
sudo apt update
sudo apt upgrade
```
### 2. Install these tools:
```bash
sudo apt -y install build-essential cmake gfortran pkg-config unzip software-properties-common doxygen
```
### 3. Update/install Python, Pip and Numpy with:
```bash
sudo apt -y install python-dev python-pip python3-dev python3-pip python3-testresources
sudo apt -y install python-numpy python3-numpy
```
### 4. Install a plenty of stuff that will guarantee or add features to your OpenCV:
```bash
sudo apt -y install libblas-dev libblas-test liblapack-dev libatlas-base-dev libopenblas-base libopenblas-dev
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
Be patient, that will take a long time...
### 5. Install legacy libraries from Ubuntu 16.04 (it is necessary):
```bash
sudo add-apt-repository "deb http://ports.ubuntu.com/ubuntu-ports xenial-security main"
sudo apt -y update
sudo apt -y install libjasper-dev libjasper
```
### 6. Create a folder that should receive your (future) compiled OpenCV 4.1.2 package:
```bash
mkdir opencv_package
```
You can create that folder in any place you want but you must have to remeber its full path when you start the compiler configuration step.

Observation: All next steps (including this one) I executed from my "/home/odroid/Desktop/".
### 7. Download official OpenCV 4.1.2 zipped source files:
```bash
wget -O opencv.zip https://github.com/opencv/opencv/archive/4.1.2.zip
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.1.2.zip
```
### 8. Unzip downloaded source files:
```bash
unzip opencv.zip
unzip opencv_contrib.zip
```
### 9. Rename unzipped folders for your convenience:
```bash
mv opencv-4.1.2 opencv
mv opencv_contrib-4.1.2 opencv_contrib
```
### 10. Go into unziped OpenCV source folder and create a temporary work folder that should be used by the compiler:
```bash
cd opencv
mkdir build
cd build
```
### 11. Configure the compiler with the following command:
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
Observation: I decided to explicitly enable all OpenCV features I knew so far and exclude its documentation and examples.
### 12. Start compilation:
```bash
make -j4
```
Observation: As ODROID-XU4 has 8 cores you will use half of them with "-j4" argument.

Now, be patient again! The compilation will take a long time...
### 13. Finish by installing your compiled OpenCV 4.1.2:
```bash
sudo make install
sudo ldconfig
sudo apt update
```
### Last considerations:
At the end of compilation, the binary object created that really matters will be 'cv2.cpython-36m-arm-linux-gnueabihf.so' located at 'opencv_package' folder. Don't delete it!

Odroid XU4 manufacturer official link for Ubuntu download I used:
https://odroid.in/ubuntu_18.04lts/XU3_XU4_MC1_HC1_HC2/ubuntu-18.04.3-4.14-mate-odroid-xu4-20190929.img.xz

Don't forget to delete/remove files and folders you downloaded or created on steps 7 to 10, respectively.

Clean your system with the following commands:
```bash
sudo apt autoremove
sudo apt clean
```
