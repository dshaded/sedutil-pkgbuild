# Maintainer: Denis Vygovskii <dshaded@gmail.com>

pkgname=sedutil-dshaded
pkgver=1.0.0
pkgrel=1
pkgdesc="TCG OPAL 2.00 SED Management Program"
arch=('i686' 'x86_64')
url="https://github.com/dshaded/sedutil"
license=('GPL3')
makedepends=('git')
source=("${pkgname}-${pkgver}::git+$url#branch=s3-sleep-support"
        'sedutil.hook'
        'sedutil.install')
sha256sums=('SKIP'
            'SKIP'
            'SKIP')

build() {
    cd "${pkgname}-${pkgver}"
    autoreconf || true
    automake --add-missing
    autoreconf
    ./configure
    make
}

package() {
    _release="Release_$CARCH"
    cd "${srcdir}/${pkgname}-${pkgver}/"
    install -Dm755 sedutil-cli "${pkgdir}/usr/bin/sedutil-cli"
    install -Dm644 "${srcdir}/sedutil.hook" "${pkgdir}/usr/lib/initcpio/hooks/sedutil"
    install -Dm644 "${srcdir}/sedutil.install" "${pkgdir}/usr/lib/initcpio/install/sedutil"
}
