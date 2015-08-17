# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=qtwebkit-git
pkgver=v5.1.0.beta1.3.g30fd950
pkgrel=1
pkgdesc="A cross-platform application and UI framework (QtWebKit)"
arch=('i686' 'x86_64')
url="http://qt-project.org/"
license=('GPL3' 'LGPL')
depends=('qtdeclarative-git' 'mesa' 'gstreamer0.10-base')
makedepends=('git' 'ruby' 'gperf' 'python2')
options=('!libtool' 'debug')
source=(git://gitorious.org/qt/qtwebkit.git#branch=dev
        'use-python2.patch')
md5sums=('SKIP'
         '693155751eb085ec12d578a805c9e1d9')

pkgver() {
  cd qtwebkit
  git describe --always | sed 's|-|.|g'
}

prepare() {
  cd qtwebkit
  patch -p2 -i "${srcdir}"/use-python2.patch
}

build() {
  export LD_LIBRARY_PATH=/opt/qt-git/lib

  cd qtwebkit
  /opt/qt-git/bin/qmake
  make
}

package() {
  cd qtwebkit
  make INSTALL_ROOT="${pkgdir}" install
}
