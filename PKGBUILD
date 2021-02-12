# Maintainer: Aleksy Grabowski <hurufu+arch@gmail.com>

pkgname=nexoid-nexui-flask-git
pkgver=0.0.1
pkgrel=1
pkgdesc='NEXO-in-the-cloud demo'
arch=(any)
license=('AGPL')
group=(nexoid)
depends=(
    python-bitstruct
    python-timebudget
    python-pynng
    python-flask
    python-bitstring
    python-asn1tools
    python-gevent
    libsocket
    nexoid-fat
)
makedepends=(
    git
)
provides=(
    nexoid-nexui
)
source=(
    git+ssh://git@github.com:/hurufu/nexoid-nexui-flask.git
    git+git://github.com/AlainCouthures/declarative4all.git
    nexui.service
)
md5sums=(
    SKIP
    SKIP
    179174b2f27bc612fb35375fff9c9933
)

sha1sums=(
    SKIP
    SKIP
    e86244af11cabbb40e2b14185b675040e0674386
)

build() {
    cd "$srcdir/nexoid-nexui-flask"
    git submodule init
    git config submodule.'XSLTForms1.5'.url "$srcdir/declarative4all"
    git submodule update
    python setup.py build
}

package() {
    install -Dm444 -t "$pkgdir/usr/lib/systemd/system" nexui.service

    cd "$srcdir/nexoid-nexui-flask"
    python setup.py install -O1 --root="$pkgdir" --skip-build
}
