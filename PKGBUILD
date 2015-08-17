# Maintainer: Panos Mavrogiorgos <pmav99@gmail.com>
pkgname=pss-hg
pkgver=95
pkgrel=1
arch=('any')
pkgdesc="An ack-like tool for grepping through source code."
url="http://bitbucket.org/eliben/pss"
license=('public domain')
depends=('python2')
optdepends=()
makedepends=('python2' 'mercurial')
install=
source=()
md5sums=()

_hgroot="http://bitbucket.org/eliben"
_hgrepo="pss"

build() {
  cd "$srcdir"
  msg "Connecting to Mercurial server...."

  if [ -d $_hgrepo ] ; then
    cd $_hgrepo
    hg pull -u || return 1
    msg "The local files are updated."
  else
    hg clone $_hgroot/$_hgrepo || return 1
  fi

  msg "Mercurial checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_hgrepo-$pkgver"
  cp -r "$srcdir/$_hgrepo" "$srcdir/$_hgrepo-$pkgver"
}

package() {
  cd "$srcdir/$_hgrepo-$pkgver"
  python2 setup.py install --root="$pkgdir/" --optimize=1
}

# vim:set ts=2 sw=2 et:
