# $Id$
# Maintainer: xia0er@gmail.com
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>
# Contributor: riai <riai@bigfoot.com> Ben <ben@benmazer.net>

pkgname=('python2-pyqt-x')
pkgver=4.9.6
pkgrel=1
pkgdesc="python2-pyqt that doesn't depend on python3"
#pkgdesc="PyQt: A set of Python2 bindings for the Qt toolkit"
arch=('i686' 'x86_64' 'arm')
url="http://riverbankcomputing.co.uk/software/pyqt/intro"
license=('GPL')
depends=('python2-sip' 'dbus-python')
optdepends=('phonon: enable audio and video in PyQt applications'
            'python2-opengl: enable OpenGL 3D graphics in PyQt applications'
            'qscintilla: QScintilla API'
            'qt-assistant-compat: add PyQt online help in Qt Assistant')
replaces=('python2-pyqt' 'pyqt')
provides=('python2-qt' 'python2-pyqt' 'pyqt')
makedepends=('qt' 'python2-sip' 'phonon' 'mesa'
             'python2-opengl' 'qt-assistant-compat' 'qtwebkit' 'python2-dbus')
source=("http://downloads.sourceforge.net/pyqt/PyQt-x11-gpl-${pkgver}.tar.gz")
md5sums=('514e1f9597771dc732ba75ba9fa5c6b6')

build() {
  cd "${srcdir}"
  #cp -r PyQt-x11-gpl-${pkgver} Py2Qt-x11-gpl-${pkgver}

  cd "${srcdir}/PyQt-x11-gpl-${pkgver}"

  ### Python2 version ###
  python2 configure.py \
    --confirm-license \
    -v /usr/share/sip \
    --qsci-api

  # Thanks Gerardo for the rpath fix
  find -name 'Makefile' | xargs sed -i 's|-Wl,-rpath,/usr/lib||g;s|-Wl,-rpath,.* ||g'

  make
  # INSTALL_ROOT is needed for the QtDesigner module, the other Makefiles use DESTDIR
  make DESTDIR="${pkgdir}" INSTALL_ROOT="${pkgdir}" install

}
