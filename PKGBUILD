# Maintainer: ava1ar <mail(at)ava1ar(dot)info>

pkgname=mseide-msegui
pkgver=3.2.0
pkgrel=1
pkgdesc="RAD IDE for Free Pascal"
arch=('i686' 'x86_64')
url="http://msegui.org/"
license=('GPL')
depends=('fpc>=2.6.2')
if [ "$CARCH" == x86_64 ]; then
	source=(http://www.msegui.org/sites/default/files/downloads/${pkgname}_${pkgver}-64bit.tar.gz)
	sha1sums=('6e6f63f0e064b9138b0ce9e961f48916d2b8777c')
elif [ "$CARCH" == i686 ]; then
	source=(http://www.msegui.org/sites/default/files/downloads/${pkgname}_${pkgver}-32bit.tar.gz)
	sha1sums=('7b2565df6c165b45b124769e9037b023303e16cf')
fi
 
package() {
  cd ${srcdir}/${pkgname}_${pkgver}
  mkdir -p ${pkgdir}/usr/{bin,lib/mseide-msegui/bin,share/applications}
  
  # main executable
  install -Dm 755 mseide.sh ${pkgdir}/usr/lib/mseide-msegui/bin
  ln -s /usr/lib/mseide-msegui/bin/mseide.sh ${pkgdir}/usr/bin/mseide
  
  # libraries
  bsdtar -xzf apps.tar.gz -C ${pkgdir}/usr/lib/mseide-msegui
  bsdtar -xzf lib.tar.gz -C ${pkgdir}/usr/lib/mseide-msegui
  bsdtar -xzf units.tar.gz -C ${pkgdir}/usr/lib/mseide-msegui
  
  # docs 
  mkdir -p ${pkgdir}/usr/share/doc/mseide-msegui
  install -Dm 644 CONFIG.TXT LICENSE README.TXT VERSION.TXT ${pkgdir}/usr/share/doc/mseide-msegui
  
  # icon and application file
  install -Dm 644 msegui_24.png ${pkgdir}/usr/share/doc/mseide-msegui/mseide_24.png
  install -Dm 644 mseide-msegui.desktop ${pkgdir}/usr/share/applications
}
