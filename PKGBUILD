# Maintainer: John Gleezowood <psyrccio@gmail.com>
# Contributor: Christopher Arndt <aur -at- chrisarndt -dot- de>
# Maintainer: Clarence <xjh.azzbcc@gmail.com>
_pkgname=ocenaudio
pkgname="$_pkgname-bin"
pkgver=3.11.16
pkgrel=1
pkgdesc="Cross-platform, easy to use, fast and functional audio editor"
arch=('i686' 'x86_64')
url="https://www.ocenaudio.com/"
license=('custom')
depends=('hicolor-icon-theme' 'jack' 'libpulse' 'qt5-base')
provides=("$_pkgname")
conflicts=("$_pkgname")
sha256sums_i686=('516d4a7eca166c692fa36fb2be3a76e9146b6c8cfa12d7b5f1d2e4cf3141989e')
sha256sums_x86_64=('0fe63a6476434537a9df16c5e1a7732956d45d3d0de3d61d6bea676e54e8eccc')
source_i686=("${_pkgname}-${pkgver}_i686.deb::https://www.ocenaudio.com/downloads/index.php/ocenaudio_debian32.deb?version=v${pkgver}")
source_x86_64=("${_pkgname}-${pkgver}_x86_64.tar.xz::https://www.ocenaudio.com/downloads/index.php/ocenaudio_archlinux.pkg.tar.xz?version=v${pkgver}")

build() {
  echo "ocenaudio "$pkgver
}

package() {
  if [ $CARCH == "i686" ]; then
    tar -xJf ${srcdir}/data.tar.xz -C "${pkgdir}"
    rm -rf "${pkgdir}/var"
  else
    cp -rLnf ${srcdir}/* ${pkgdir}/
    rm -f ${pkgdir}/${_pkgname}-${pkgver}_x86_64.tar.xz
  fi
  install -dm755 "${pkgdir}/usr/bin"
  install -dm755 "${pkgdir}/usr/share/licenses"
  install -Dm644 "${pkgdir}/opt/$_pkgname/bin/ocenaudio_license.txt" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE.txt"

  ln -sf "/opt/$_pkgname/bin/${_pkgname}" "${pkgdir}/usr/bin"
  sed -i 's|^Exec=/opt/ocenaudio/bin|Exec=/usr/bin|' "$pkgdir/usr/share/applications/ocenaudio.desktop"

  rm -f "${pkgdir}/opt/$_pkgname/bin/ocenaudio_license.txt"
}
