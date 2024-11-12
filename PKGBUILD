# Maintainer: Evan Greenup <_>

_name=hlint
pkgname=hx-${_name}
pkgver=3.8
pkgrel=1
pkgdesc="Source code suggestions"
url="https://github.com/ndmitchell/hlint"
license=("BSD-3-Clause")
arch=('x86_64')
provides=('hlint')
conflicts=('hlint')
depends=(libyaml)
makedepends=('stack')
source=("${_name}-${pkgver}.tar.gz::https://github.com/ndmitchell/${_name}/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('70082004f954acdf63a5c76ccd6ee229295c5667c89d6085bc8c79756b238f2f')

_stack_resolver=lts-21.6

build() {
  cd "$srcdir/$_name-$pkgver"

  stack --resolver=${_stack_resolver} build hlint:exe:hlint
}

package() {
  cd "$srcdir/$_name-$pkgver"
  mkdir -m755 -p "${pkgdir}/usr/bin/"
  install -m755 "$(stack --resolver=${_stack_resolver} path --local-install-root)/bin/hlint" "${pkgdir}/usr/bin/hlint"
  install -D -m644 LICENSE -t "$pkgdir"/usr/share/licenses/$pkgname/
}