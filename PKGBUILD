# Maintainer: Jack O'Connor <oconnor663@gmail.com>

pkgname=keybase-git
pkgdesc='the Keybase Go client, filesystem, and GUI'
license=('BSD')
url='https://keybase.io'
pkgver=1.0.16+8881.92767fa
pkgver() {
  "$srcdir/client/packaging/linux/arch/version.sh"
}
pkgrel=1
arch=('i686' 'x86_64')
depends=(fuse gconf)
makedepends=(go npm git rsync)
# keybase-release is a deprecated AUR package
conflicts=(keybase keybase-release keybase-bin)
source=(
  'git+https://github.com/keybase/client'
  'git+https://github.com/keybase/kbfs'
)
md5sums=('SKIP' 'SKIP')
install=keybase.install

build() {
  "$srcdir/client/packaging/linux/build_binaries.sh" prerelease "$srcdir/build_dir"
}

package() {
  if [ "$CARCH" = x86_64 ] ; then
    debian_arch=amd64
  else
    debian_arch=i386
  fi
  cp -r "$srcdir/build_dir/binaries/$debian_arch"/* "$pkgdir"
}
