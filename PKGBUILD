# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer : Daniel Bermond < gmail-com: danielbermond >
# Contributor: Niklas <dev@n1klas.net>
# Contributor: Justin Dray <justin@dray.be>
# Contributor: David Roheim <david dot roheim at gmail dot com>
# Contributor: DrZaius <lou[at]fakeoutdoorsman[dot]com>

_os="$( \
  uname \
    -o)"
if [[ "${_os}" == "GNU/Linux" ]]; then
  _libc="glibc"
elif [[ "${_os}" == "Android" ]]; then
  _libc="ndk-sysroot"
fi
_proj="opencore-amr"
_pkg=vo-amrwbenc
pkgname="${_pkg}"
pkgver=0.1.3
pkgrel=2
_pkgdesc=(
  'Library for the VisualOn Adaptive'
  'Multi Rate Wideband (AMR-WB) audio encoder'
)
arch=(
  'i686'
  'x86_64'
  'arm'
  'aarch64'
  'armv7l'
  'armv6l'
  'mips'
  'pentium4'
  'powerpc'
)
_sf="sourceforge.net/projects"
_ns="${_proj}"
url="https://${_sf}/${_ns}"
license=(
  'APACHE'
)
depends=(
  "${_libc}"
)
_sf_dl="https://downloads.${sf}"
_tarname="${_pkg}-${pkgver}"
source=(
  "${_sf_dl}/${_ns}/${_pkg}/${_tarname}.tar.gz"
)
sha256sums=(
  '5652b391e0f0e296417b841b02987d3fd33e6c0af342c69542cbb016a71d9d4e'
)

build() {
  cd \
    "${_tarname}"
  ./configure \
    --prefix='/usr'
  make
}

package() {
  cd \
    "${_tarname}"
  make \
    DESTDIR="${pkgdir}" \
    install
  install \
    -Dm644 \
    "NOTICE" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}"
}
