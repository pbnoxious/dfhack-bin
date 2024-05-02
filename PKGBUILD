# Maintainer: Christian Krause ("wookietreiber") <christian.krause@mailbox.org>
# Co-Maintainer: Ziusudra <ziusudra.zoon@gmail.com>
# shellcheck disable=2034
# shellcheck disable=2148

pkgname=dfhack-bin
_pkgname=dfhack
pkgver=50.13
_pkgver=$pkgver-r1.1
pkgrel=9
pkgdesc="memory hacking library for Dwarf Fortress and a set of tools that use it"
arch=('x86_64' 'i686')
url="https://dfhack.readthedocs.io/en/stable/"
license=('custom')
depends=("dwarffortress=$pkgver" lua protobuf libpng12 libxrandr libjpeg6 freetype2 libglvnd libxcursor libxinerama libxcrypt-compat sdl_image sdl_ttf)

conflicts=(dfhack dfhack-git)
provides=(dfhack)

source_x86_64=("https://github.com/DFHack/dfhack/releases/download/$_pkgver/dfhack-$_pkgver-Linux-64bit.tar.bz2")
source=(dfhack.sh
        dfhack-run.sh)

md5sums=('45ab3b65cb5b01beff9fecccff777f85'
         '37421a6cf2ca420bed4420ea8e402d40')
md5sums_x86_64=('8dc29c78e2a5ca030f3d3d774b6d5b20')

prepare() {
  # shellcheck disable=2154
  sed -e 's|setarch i386 -R ||' \
      -i "$srcdir"/dfhack
}

package() {
  # shellcheck disable=2154
  install -d "$pkgdir"/opt/dwarffortress

  cp -r "$srcdir"/{dfhack,dfhack-run,hack,stonesense} "$pkgdir"/opt/dwarffortress

  install -Dm755 "$srcdir"/dfhack.sh     "$pkgdir"/usr/bin/dfhack
  install -Dm755 "$srcdir"/dfhack-run.sh "$pkgdir"/usr/bin/dfhack-run

  install -Dm644 "$srcdir"/hack/LICENSE.rst "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
