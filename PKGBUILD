# Maintainer: Aleksy Grabowski <hurufu+arch@gmail.com>

pkgname=nexoid-nexui-flask-git
pkgver=0.0.1
pkgrel=2
pkgdesc='NEXO-in-the-cloud demo'
arch=(any)
license=('AGPL')
groups=(nexoid)
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
    nexoid-nexui-flask
)
source=(
    git+ssh://git@github.com:/hurufu/nexoid-nexui-flask.git
    git+ssh://git@github.com:/hurufu/nexoid-protocol-collection.git
    git+git://github.com/AlainCouthures/declarative4all.git
)
md5sums=(
    SKIP
    SKIP
    SKIP
)

pkgver() {
    git -C "$srcdir/nexoid-nexui-flask" describe | awk -F - '{ print substr($1,2) ( $2 ? ".r"$2"."$3 : "") }'
}

build() {
    cd "$srcdir/nexoid-nexui-flask"
    git submodule init
    git config submodule.'XSLTForms1.5'.url "$srcdir/declarative4all"
    git config submodule.nexoid-protocol-collection.url "$srcdir/nexoid-protocol-collection"
    git submodule update
    python setup.py build
}

package() {
    cd "$srcdir/nexoid-nexui-flask"
    python setup.py install -O1 --root="$pkgdir" --skip-build
}
