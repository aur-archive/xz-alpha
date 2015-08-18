# $Id$
# Maintainer: Pierre Schmitz <pierre@archlinux.de>
# Contributor: François Charette <firmicus@gmx.net>

pkgname=xz-alpha
_pkgname=xz
pkgver=5.1.2
_pkgver="${pkgver}alpha"
pkgrel=2
pkgdesc='Library and command line tools for XZ and LZMA compressed files. Alpha development version.'
arch=('i686' 'x86_64')
url='http://tukaani.org/xz/'
license=('GPL' 'LGPL' 'custom')
options=('!libtool')
conflicts=('xz')
provides=('xz')
source=("http://tukaani.org/${_pkgname}/${_pkgname}-${_pkgver}.tar.gz"
        "http://tukaani.org/${_pkgname}/${_pkgname}-${_pkgver}.tar.gz.sig")
md5sums=('9bad1e249537ce69b206815cf28ca87b'
         'a5676335e14aee96e0a6fe04238a6966')

build() {
    cd "${srcdir}/${_pkgname}-${_pkgver}"

    ./configure \
        --prefix=/usr \
        --disable-rpath \
        --enable-werror #--disable-nls
    make
}

check() {
    cd "${srcdir}/${_pkgname}-${_pkgver}"
    make check
}

package() {
    cd "${srcdir}/${_pkgname}-${_pkgver}"
    make DESTDIR=${pkgdir} install

    install -dm755 "${pkgdir}/usr/share/licenses/xz"
    ln -sf /usr/share/doc/xz/COPYING "${pkgdir}/usr/share/licenses/xz/"
    ln -sf /usr/share/licenses/common/GPL2/license.txt "${pkgdir}/usr/share/doc/xz/COPYING.GPLv2"
}
