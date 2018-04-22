# Script generated with Bloom
pkgdesc="ROS - A ROS Driver for V4L USB Cameras"
url='http://wiki.ros.org/usb_cam'

pkgname='ros-lunar-usb-cam'
pkgver='0.3.6_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ffmpeg'
'ros-lunar-camera-info-manager'
'ros-lunar-catkin'
'ros-lunar-image-transport'
'ros-lunar-roscpp'
'ros-lunar-sensor-msgs'
'ros-lunar-std-msgs'
'ros-lunar-std-srvs'
)

depends=('ffmpeg'
'ros-lunar-camera-info-manager'
'ros-lunar-image-transport'
'ros-lunar-roscpp'
'ros-lunar-sensor-msgs'
'ros-lunar-std-msgs'
'ros-lunar-std-srvs'
'v4l-utils'
)

conflicts=()
replaces=()

_dir=usb_cam
source=()
md5sums=()

prepare() {
    cp -R $startdir/usb_cam $srcdir/usb_cam
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

