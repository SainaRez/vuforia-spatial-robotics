Installing ROS on RPI:

System info: 
    RPI 4, 4GB
    Ubuntu 18.04 (gnome desktop)
    ROS Melodic

In order to install ROS follow the instructions in the [ROS Tutorials](http://wiki.ros.org/melodic/Installation/Ubuntu)

If there are issues with the EGL library, it might be due to the linux libraries 
not being symlinked (ex. the turtle from the rostopic tutorial not moving). To address this issue, follow the steps below by building Qt5 from source:

Install dependancies:

```
$ sudo apt-get install libxcb-xinerama0-dev flex bison gperf libicu-dev 
libxslt-dev ruby libssl-dev libxcursor-dev libxcomposite-dev 
libxdamage-dev libxrandr-dev libdbus-1-dev libfontconfig1-dev 
libcap-dev libxtst-dev libpulse-dev libudev-dev libpci-dev 
libnss3-dev libasound2-dev libxss-dev libegl1-mesa-dev gperf 
bison libasound2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev

$ sudo apt-get install '^libxcb.*-dev' libx11-xcb-dev libglu1-mesa-dev 
libxrender-dev libxi-dev
```

Then clone the qt respository:

```
git clone https://code.qt.io/qt/qt5.git
cd qt5
git submodule update --init


The steps above should fix the graphics issue. However, if there is an outdated Qt version in the packages, create a build:

```
mkdir qt-build
cd qt-build
../configure -opensource -static -confirm-license 
-release -nomake examples -openssl-runtime -prefix /usr
```

For more information refer to [this page](https://raspberrypi.stackexchange.com/questions/61078/qt-applications-dont-work-due-to-libegl)

