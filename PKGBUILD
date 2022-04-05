# Maintainer: Jigsaw <j1g5aw@foxmail.com>

pkgname=simpread-sync-git
pkgver=0.6.5.r0.g15c2c8e
pkgrel=1
pkgdesc="A simple cli to sync simpread config"
arch=("i686" "x86_64" "armv7h" "aarch64")
url="https://github.com/j1g5awi/simpread-sync"
license=("MIT")

optdepends=('pandoc: support epub output')
makedepends=("git" "go")

source=("$pkgname::git+https://github.com/j1g5awi/simpread-sync")

sha512sums=("SKIP")

pkgver() {
  cd "$pkgname"
  git describe --long --tags | sed "s/^v//;s/\([^-]*.g\)/r\1/;s/-/./g"
}

build(){
    cd "$pkgname"
    go build -trimpath -ldflags "-s -w"
}

package() {
    cd "$pkgname"
    install -Dm755 "simpread-sync" "${pkgdir}/usr/bin/simpread-sync"
    install -Dm644 systemd/simpread-sync@.service  ${pkgdir}/usr/lib/systemd/system/simpread-sync@.service
}
