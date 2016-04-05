pkgname=haroopad
pkgver=0.13.2
pkgrel=1
pkgdesc="A markdown enabled document processor"
arch=('x86_64')
url="http://pad.haroopress.com/"
license=('custom')
depends=('xdg-utils' 'desktop-file-utils' 'gconf' 'alsa-lib' 'gtk2' 'libnotify' 'nss')
options=('!strip')
install=${pkgname}.install
sha256sums=('46eddf00972e5b27fbe2da835ab0ae2c2f30e7daf2d1c615905bf603e445d1b4')
source=("https://bitbucket.org/rhiokim/haroopad-download/downloads/${pkgname}-v${pkgver}-x64.deb")

package() {

    bsdtar -xf data.tar.gz -C "${pkgdir}"
	rm -r ${pkgdir}/usr/share/{applications/mimeapps.list,doc}

    sed -i -e 's/Exec=haroopad/Exec=haroopad %F/g' "${pkgdir}/usr/share/applications/Haroopad.desktop"

    echo -en '\nMimeType=text/x-markdown;' >> ${pkgdir}/usr/share/applications/Haroopad.desktop
}
