# Maintainer: Helle Vaanzinn < glitsj16 AT riseup DOT net >

_pkgname=fdns
pkgname=${_pkgname}-git
pkgver=0.9.62.6+39+g87bccbe
pkgrel=1
pkgdesc="Firejail DNS-over-HTTPS proxy server - git version"
arch=(x86_64)
license=(GPL2)
url="https://github.com/netblue30/fdns"
depends=('libseccomp' 'openssl')
makedepends=('git')
optdepends=('apparmor: support for apparmor profiles'
    'bash-completion: bash completion'
    'firejail: seamless integration support'
    'systemd: run fdns as a systemd service')
provides=("$_pkgname")
conflicts=("$_pkgname")
source=("git+https://github.com/netblue30/fdns.git")
sha256sums=('SKIP')

pkgver() {
    cd "$_pkgname"
    git describe --tags | sed -e 's/-/+/g' -e 's/^v//'
}

build() {
    cd "$_pkgname"
    ./configure --prefix=/usr
    make
}

package() {
    cd "$_pkgname"
    make DESTDIR="$pkgdir" install

    # license
    install -Dm0644 "${pkgdir}/usr/share/doc/${_pkgname}/COPYING" \
        "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    rm -f "${pkgdir}/usr/share/doc/${_pkgname}/COPYING"
}
