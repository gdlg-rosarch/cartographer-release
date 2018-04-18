# Script generated with Bloom
pkgdesc="ROS - Cartographer is a system that provides real-time simultaneous localization and mapping (SLAM) in 2D and 3D across multiple platforms and sensor configurations."
url='https://github.com/googlecartographer/cartographer'

pkgname='ros-lunar-cartographer'
pkgver='0.2.0_6'
pkgrel=1
arch=('any')
license=('Apache 2.0'
)

makedepends=('boost'
'cairo'
'ceres-solver'
'eigen3'
'gcc'
'gflags'
'gmock'
'google-glog'
'libwebp'
'lua52'
'protobuf'
'python2-sphinx'
'ros-lunar-catkin'
)

depends=('boost'
'cairo'
'ceres-solver'
'eigen3'
'gflags'
'google-glog'
'libwebp'
'lua52'
'protobuf'
)

conflicts=()
replaces=()

_dir=cartographer
source=()
md5sums=()

prepare() {
    cp -R $startdir/cartographer $srcdir/cartographer
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

