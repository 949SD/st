# Maintainer: David K david.dk949@gmail.com
_pkgname=st
pkgname="${_pkgname}-949sd"
pkgver="unknown"
pkgrel=0
pkgdesc="simple terminal"
arch=('x86_64')
url="https://github.com/dk949/$_pkgname"
license=('MIT')
depends=(
    'fontconfig'
    'freetype2'
    'harfbuzz'
    'libx11'
    'libxft'
    'libxrender'
)
makedepends=()
provides=('st')
conflicts=()
source=("$pkgname::git+$url")
md5sums=() #autofill using updpkgsums
sha256sums=('SKIP')

pkgver() {
    ___DATE="$(git -C "$pkgname" log -1 --format='%cd' --date=format:'%F')"
    ___DATE_TIME="$___DATE 00:00"
    ___COMMIT_COUNT=$(git -C "$pkgname" rev-list --count HEAD --since="$___DATE_TIME")
    echo "$(date -d "$___DATE" +'%Y%m%d')_$___COMMIT_COUNT"
    unset ___DATE
    unset ___DATE_TIME
    unset ___COMMIT_COUNT
}

build() {
    cd "$pkgname"
    make -j
}

package() {
    cd "$pkgname"

    make DESTDIR="$pkgdir/" PREFIX="/usr" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
