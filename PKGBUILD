# Maintainer: Rodrigo Arias <rodarima@gmail.com>

pkgname=racosync
pkgver=0.0.1
pkgrel=1
pkgdesc="Syncronize files from raco.fib.upc.edu"
url="https://github.com/rodarima/racosync/"
arch=('any')
license=('GPL3')

depends=('python' 'python-requests-oauthlib' 'python-dateutil')

source=("$pkgname-$pkgver::git+https://github.com/rodarima/racosync/")
md5sums=('SKIP')

package() {
  cd "$srcdir/$pkgname-$pkgver"
  install -m755 "racosync" "$pkgdir/${PREFIX}/bin/"
  install -Dm622 "racosync.service" "$pkgdir/${PREFIX}/lib/systemd/user/racosync.service"
  install -Dm622 "racosync.timer" "$pkgdir/${PREFIX}/lib/systemd/user/racosync.timer"
  install -Dm644 "racosync.1" "${DESTDIR}${MANPREFIX}/man1/racosync.1"
}

# vim:set ts=2 sw=2 et: