# Maintainer: Samantha Baldwin <fuhsaz 'plus' aur 'at' cryptic 'dot' li>
pkgname=tabbed-git
_pkgname=tabbed
pkgver=0.6.36.gdabf6a2
pkgrel=1
pkgdesc="Simple generic tabbed fronted to xembed aware applications"
arch=('i686' 'x86_64')
url="http://tools.suckless.org/tabbed/"
license=('MIT/X')
depends=('libxft')
makedepends=('git')
provides=('tabbed')
conflicts=('tabbed')
source=("$_pkgname::git+http://git.suckless.org/tabbed" "wid.patch")
md5sums=('SKIP'
         'c232995f2b9d439a854d55ca84bb33a6')

pkgver() {
  cd $_pkgname
  git describe --tags | sed 's+[-_]+.+g'
}

prepare() {
  if [[ -f $SRCDEST/config.h ]]; then
    cp $SRCDEST/config.h $srcdir/$_pkgname/config.h
  fi
  cd "$_pkgname"
  patch --forward --strip=1 --input="${srcdir}/wid.patch"
}

build() {
  cd $_pkgname
  make PREFIX=/usr
}

package() {
  cd $_pkgname
  make DESTDIR="$pkgdir/" PREFIX=/usr install
  install -Dm0644 LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
}

# vim:set ts=2 sw=2 et:
