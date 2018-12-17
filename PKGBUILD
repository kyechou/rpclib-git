pkgname=rpclib-git
pkgver=r525.568cc62
pkgrel=1
pkgdesc="c++ msgpack-rpc server and client library"
arch=(any)
url='http://rpclib.net'
license=('MIT')
depends=()
makedepends=(git cmake make)
provides=(rpclib)
conflicts=(rpclib)
source=("$pkgname"::'git://github.com/kyechou/rpclib.git')
md5sums=('SKIP')

pkgver() {
  # from https://wiki.archlinux.org/index.php/VCS_package_guidelines#Git
  cd "$srcdir/$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/$pkgname"
  mkdir -p build && cd build
  cmake ..
  cmake -DCMAKE_INSTALL_PREFIX="$pkgdir/usr/" --build .
  make
}

package() {
  cd "$srcdir/$pkgname/build"
  make install
  sed s#$pkgdir##g -i "$pkgdir/usr/lib/pkgconfig/rpclib.pc"
}
