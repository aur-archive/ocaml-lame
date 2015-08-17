# Maintainer: Charles E. Hawkins <charlesthehawk at yahoo dot com>
# Contributor: Thomas S Hatch <thatch45 at gmail dot com>
# Contributor: Luciano A. Ferrer <laferrer@gmail.com>
pkgname=ocaml-lame
pkgver=0.3.2
pkgrel=1
arch=('i686' 'x86_64')
license=('GPL')
pkgdesc="OCaml Bindings to the lame library"
url="http://savonet.sourceforge.net/"
depends=('lame')
makedepends=('ocaml' 'ocaml-findlib' 'lame')
source=("http://downloads.sourceforge.net/savonet/${pkgname}-${pkgver}.tar.gz")
md5sums=('b11c12e1f7dbc2f15da7030484eb2d82')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  ./configure --prefix=/usr
  make all
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  mkdir -p ${pkgdir}/usr/share/doc/${pkgname}/examples
  cp -a examples/*.ml ${pkgdir}/usr/share/doc/${pkgname}/examples
  mkdir -p ${pkgdir}$(ocamlfind printconf destdir)
  make \
    OCAMLFIND_DESTDIR=${pkgdir}$(ocamlfind printconf destdir) \
    OCAMLFIND_LDCONF=ignore \
    install
}
