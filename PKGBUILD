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
    python-pynng-git
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
    git+git@github.com:hurufu/nexoid-nexui-flask.git
    git+git://github.com/AlainCouthures/declarative4all.git
)
md5sums=(
    SKIP
    SKIP
)

build() {
    cd "$srcdir/flask-nexui"
    git submodule init
    git config submodule.'XSLTForms1.5'.url "$srcdir/declarative4all"
    git submodule update
    python setup.py build
}

package() {
    builddir=
    cd "${srcdir}/flask-nexui"
    python setup.py install -O1 --root="$pkgdir" --skip-build
}
