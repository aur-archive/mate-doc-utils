# Maintainer : Martin Wimpress <code@flexion.org>
# Contributor: Giovanni "Talorno" Ricciardi <kar98k.sniper@gmail.com>
# Contributor: Xpander <xpander0@gmail.com>

pkgname=mate-doc-utils
pkgver=1.6.2
pkgrel=1
pkgdesc="Documentation utilities for MATE"
url="http://mate-desktop.org"
arch=('any')
license=('GPL' 'LGPL')
depends=('libxml2' 'libxslt' 'python2' 'python2-lxml')
makedepends=('mate-common' 'rarian' 'perl-xml-parser')
options=('!emptydirs')
source=("http://pub.mate-desktop.org/releases/1.6/${pkgname}-${pkgver}.tar.xz")
sha1sums=('34eca45e5b3a4620be419772acdefc7abd20937b')

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    PYTHON=/usr/bin/python2 ./configure \
        --prefix=/usr \
        --disable-scrollkeeper
    make
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}" install
    # Remove files that conflict with `gnome-doc-utils`
    rm -rf "${pkgdir}/usr/share/xml/mallard/"
    rm -rf "${pkgdir}/usr/share/man/"
    rm -rf "${pkgdir}/usr/lib/"
    rm "${pkgdir}/usr/share/pkgconfig/xml2po.pc"
    rm "${pkgdir}/usr/bin/xml2po"
}
