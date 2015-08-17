# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - rqt_pose_view provides a GUI plugin for visualizing 3D poses."
url='http://ros.org/wiki/rqt_pose_view'

pkgname='ros-hydro-rqt-pose-view'
pkgver='0.3.7'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-catkin)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-rqt-gui-py
  ros-hydro-rospy
  ros-hydro-rostopic
  ros-hydro-rqt-gui
  ros-hydro-python-qt-binding
  ros-hydro-geometry-msgs
  ros-hydro-tf)
depends=(${ros_depends[@]}
  python2-pyqt4-10
  python2-rospkg
  python2-opengl)

_tag=release/hydro/rqt_pose_view/${pkgver}-${_pkgver_patch}
_dir=rqt_pose_view
source=("${_dir}"::"git+https://github.com/ros-gbp/rqt_robot_plugins-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
