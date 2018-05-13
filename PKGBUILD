# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - octovis is visualization tool for the OctoMap library based on Qt and libQGLViewer."
url='http://octomap.github.io'

pkgname='ros-melodic-octovis'
pkgver='1.9.0'
_pkgver_patch=1
arch=('any')
pkgrel=2
license=('GPLv2')

ros_makedepends=(ros-melodic-octomap)
makedepends=('cmake' 'ros-build-tools'
  ${ros_makedepends[@]}
  qt4
  libqglviewer-qt4)

ros_depends=(ros-melodic-catkin
  ros-melodic-octomap)
depends=(${ros_depends[@]}
  qt4
  libqglviewer-qt4)

# Git version (e.g. for debugging)
# _tag=release/melodic/octovis/${pkgver}-${_pkgver_patch}
# _dir=${pkgname}
# source=("${_dir}"::"git+https://github.com/ros-gbp/octomap-release.git"#tag=${_tag})
# sha256sums=('SKIP')

# Tarball version (faster download)
_dir="octomap-release-release-melodic-octovis-${pkgver}-${_pkgver_patch}"
source=("${pkgname}-${pkgver}-${_pkgver_patch}.tar.gz"::"https://github.com/ros-gbp/octomap-release/archive/release/melodic/octovis/${pkgver}-${_pkgver_patch}.tar.gz")
sha256sums=('3edf836edd904daf7f76b13dad10d4094e37a5a8c5829193fe1b583e62f2c8ef')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
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