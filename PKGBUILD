pkgname=libdbusmenu-gtk3
pkgver=12.10.2
pkgrel=1
pkgdesc="A library for passing menus over DBus"
arch=('x86_64')
url="https://launchpad.net/libdbusmenu"
license=('GPL3')
depends=('gtk3' 'libdbusmenu-glib')
makedepends=('gnome-doc-utils' 'gobject-introspection' 'gtk3' 'intltool' 'vala')
source=("http://launchpad.net/dbusmenu/${pkgver%.?}/${pkgver}/+download/libdbusmenu-${pkgver}.tar.gz")
sha256sums=('9d6ad4a0b918b342ad2ee9230cce8a095eb601cb0cee6ddc1122d0481f9d04c9')

build() {
  cd libdbusmenu-${pkgver}
  export HAVE_VALGRIND_TRUE='#'
  export HAVE_VALGRIND_FALSE=''
  ./configure --prefix='/usr' --sysconfdir='/etc' --localstatedir='/var' --disable-{dumper,static,tests}
  make
}

package() {
  cd libdbusmenu-${pkgver}
  make -C libdbusmenu-glib DESTDIR="${pkgdir}" install
  make -C libdbusmenu-gtk DESTDIR="${pkgdir}" install
  make -C libdbusmenu-glib DESTDIR="${pkgdir}" uninstall
}

