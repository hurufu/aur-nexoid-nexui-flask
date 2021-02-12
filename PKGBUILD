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
    mailcap
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
)
md5sums=(
    SKIP
    SKIP
)

build() {
    cd "$srcdir/nexoid-nexui-flask"
    git submodule init
    git config submodule.'XSLTForms1.5'.url "$srcdir/declarative4all"
    git submodule update
    python setup.py build
}

package() {
    cd "$srcdir/nexoid-nexui-flask"
    python setup.py install -O1 --root="$pkgdir" --skip-build
}
