# Maintainer: John Gleezowood <psyrccio@gmail.com>
# Contributor: Christopher Arndt <aur -at- chrisarndt -dot- de>
# Maintainer: Clarence <xjh.azzbcc@gmail.com>
_pkgname=ocenaudio
pkgname="$_pkgname-bin"
pkgver=3.13.5
pkgrel=1
pkgdesc="Cross-platform, easy to use, fast and functional audio editor"
arch=('x86_64')
url="https://www.ocenaudio.com/"
license=('custom')
depends=('hicolor-icon-theme' 'jack' 'libpulse' 'qt5-base')
provides=("$_pkgname")
conflicts=("$_pkgname")
sha256sums=('83481de4229e8f7b687911b7c4366408a51fc75c0f372dcfd68cc5f5712b59a5')
source=("${_pkgname}-${pkgver}_x86_64.tar.xz::https://www.ocenaudio.com/downloads/index.php/ocenaudio_archlinux.pkg.tar.xz?version=v${pkgver}")

build() {
  echo "ocenaudio "$pkgver
}

package() {
  cp -rnf ${srcdir}/* ${pkgdir}/
  rm -f ${pkgdir}/${_pkgname}-${pkgver}_x86_64.tar.xz
  install -dm755 "${pkgdir}/usr/bin"
  install -dm755 "${pkgdir}/usr/share/licenses"
  install -Dm644 "${pkgdir}/opt/$_pkgname/bin/ocenaudio_license.txt" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE.txt"

  ln -sf "/opt/$_pkgname/bin/${_pkgname}" "${pkgdir}/usr/bin"
  sed -i 's|^Exec=/opt/ocenaudio/bin|Exec=/usr/bin|' "$pkgdir/usr/share/applications/ocenaudio.desktop"

  rm -f "${pkgdir}/opt/$_pkgname/bin/ocenaudio_license.txt"
}
