# Maintainer: josephgbr <rafael.f.f1@gmail.com>

pkgname=teeworlds-zchaos
pkgver=1.03.1
pkgrel=1
pkgdesc="A customized server by HeroiAmarelo with a lot of chaotic zombies!"
arch=('x86_64' 'i686')
url="https://www.teeworlds.com/forum/viewtopic.php?id=9682"
license=('custom') # free/not opensource
depends=(teeworlds)
depends_x86_64=(lib32-gcc-libs)
install=$pkgname.install
source=("zChaos_lnx86_$pkgver.zip::http://goo.gl/ScLLL"
         server.sh.in README server.cfg
         moonlight.map zChaos1.map ztf5.map)
md5sums=('ddfbb2f2596226eed783290c1c77d101'
         '529146a3b13993770fa414f66c67fa26'
         '35af89a29a14c0e518be2450719a801f'
         '20f2dd098460eb3235e3c516e62450fa'
         '45f8333b7c14cd5e562225424fa43e28'
         '350fbdfb64459e00d475a8efeb6ad3ab'
         '8cc23398780bd1ed64d9fadc5c2667e8')

package() {
   # create dirs
  install -dm755 "$pkgdir"/usr/bin \
                 "$pkgdir"/usr/share/$pkgname \
                 "$pkgdir"/usr/share/doc/$pkgname \
                 "$pkgdir"/usr/share/teeworlds/data/maps/

   # install files from source=()
  install -m755 zChaos_lnx86_1.03.1 "$pkgdir"/usr/share/$pkgname/teeworlds_srv
  install -m644 server.cfg "$pkgdir"/usr/share/$pkgname/
  install -m644 README "$pkgdir"/usr/share/doc/$pkgname/
  install -m755 server.sh.in "$pkgdir"/usr/bin/${pkgname}_srv
  for map in moonlight.map zChaos1.map ztf5.map; do
    install -m644 $map "$pkgdir"/usr/share/teeworlds/data/maps/
  done

   # set zChaos script
  sed -i "$pkgdir"/usr/bin/${pkgname}_srv \
      -e "s/@MODNAME@/$pkgname/"
}
