# Maintainer: Alexander Rødseth <rodseth@gmail.com>
pkgname=shedskin
pkgver=0.9
pkgrel=2
pkgdesc="A Python to C++ compiler"
arch=('any')
url="http://code.google.com/p/shedskin/"
license=('GPL2')
depends=('pcre' 'gc' 'python2')
conflicts=('shedskin-svn')
source=("http://shedskin.googlecode.com/files/shedskin-$pkgver.tgz")
md5sums=('4ae94c01ce84e85052ea9438e32c461c')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  # Python 2 fix
  echo "#!/usr/bin/python2" > run
  echo "import shedskin" >> run
  echo "shedskin.main()" >> run
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  # Install the wrapperscript
  mkdir -p "$pkgdir/usr/bin"
  install -Dm755 run "$pkgdir/usr/bin/shedskin"

  # Install using setup.py
  python2 setup.py install --prefix="$pkgdir/usr"

  # Install the license
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
