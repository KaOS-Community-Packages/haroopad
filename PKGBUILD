pkgname=haroopad
pkgver=0.12.2
pkgrel=1
pkgdesc="A markdown enabled document processor"
arch=('x86_64')
url="http://pad.haroopress.com/"
license=('unknown')
depends=('xdg-utils'
         'desktop-file-utils'
         'gconf'
         'nodejs'
         'python'
         'alsa-lib'
         'gtk2'
         'nss')
options=('!strip')
install=${pkgname}.install
changelog=changelog

source=("https://bitbucket.org/rhiokim/haroopad-download/downloads/${pkgname}-v${pkgver}_amd64.deb"
	    "haroopad.desktop"
	    "x-markdown.xml")
	sha256sums=('641a2a20c3991fd03cab750c833ffb89a0def96b065e9e320ec69e8b5ec07e7b'
	            '28f569d520f75e74485f1a7d55baf7b038c65fc82b4efbbef9bc882b26ddc9ed'
                    '8261b526007db35c8691b3b6bf79cf40639a5e53fa81f1dd1fa4ea1cf5c440dd')
	

build() {
	cd "${srcdir}"
	tar -zxf data.tar.gz
}

package() {
	cd "${srcdir}"
	cp -r "${srcdir}/usr" "${pkgdir}/usr"
	sed -i -e 's/libudev.so.0/libudev.so.1/g' \
	       -e 's/libc.so.1/libc.so.6/g' \
	       "${pkgdir}/usr/share/haroopad/haroopad"
	rm "${pkgdir}/usr/share/applications/mimeapps.list"
	rm "${pkgdir}/usr/share/applications/Haroopad.desktop"
	mkdir "${pkgdir}/usr/share/doc/haroopad/"
	mv "${pkgdir}/usr/share/doc/changelog" \
	   "${pkgdir}/usr/share/doc/copyright" \
	   "${pkgdir}/usr/share/doc/haroopad/"
	install -Dm644 x-markdown.xml "${pkgdir}/usr/share/mime/packages/x-markdown.xml"
	install -Dm644 haroopad.desktop "${pkgdir}/usr/share/applications/haroopad.desktop"
}