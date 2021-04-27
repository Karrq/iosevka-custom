# Maintainer: Francesco Dainese <franci[dot]dainese[at]gmail[dot]com>
pkgname=iosevka-karrq
pkgver=r2588.ac09cdbe
pkgrel=1
pkgdesc="Iosevka font with my customizations"
arch=('any')
url='https://github.com/Karrq/iosevka-custom'
license=('OFL')
makedepends=('git' 'nodejs>12.16.0' 'npm' 'ttfautohint')
source=("iosevka::git+https://github.com/be5invis/Iosevka"
        "private-build-plans.toml")
sha256sums=("SKIP"
            "a4e53e620740170efa84ec3945a95cb93f15ccf1f51fb01bf361653fc1f90f8d")

pkgver() {
    cd "$srcdir/iosevka"
    printf "r%s.%s" "(git rev-list --count HEAD)" "(git rev-parse --short HEAD)"
}
            
prepare() {
    mv "$srcdir/private-build-plans.toml" "$srcdir/iosevka"
}

build() {
	cd "$srcdir/iosevka"
	npm install
	npm run build -- ttf::iosevka-karrq
	npm run build -- ttf::iosevka-karrq-term
}

package() {
	install -D -m644 "${srcdir}/iosevka/dist/*/ttf/*.ttf" "${pkgdir}/usr/share/fonts/TTF/"
	install -D -m644 "${srcdir}/iosevka/LICENSE.md" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.md"
}
