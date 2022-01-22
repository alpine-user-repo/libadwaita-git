pkgname=libadwaita-git
pkgver=_git
pkgrel=0
pkgdesc="Building blocks for modern GNOME applications"
provides="libadwaita=${pkgver}"
url="https://gitlab.gnome.org/GNOME/libadwaita"
arch="all !s390x !riscv64"
license="LGPL-2.1-or-later"
makedepends="git meson sassc gtk4.0-dev gobject-introspection-dev vala"
subpackages="$pkgname-dev $pkgname-lang"
source=""
builddir="$srcdir/${pkgname}"
options="!check"

prepare() {
	default_prepare
	cd "${srcdir}"
	git clone --depth=1 "${url}" "${pkgname}"
}

build() {
	cd ${builddir}
	abuild-meson . output -Dgtk_doc=false -Dexamples=true
	meson compile ${JOBS:+-j ${JOBS}} -C output
}

package() {
	DESTDIR="$pkgdir" meson install --no-rebuild -C output
}
