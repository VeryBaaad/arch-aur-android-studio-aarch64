# Contributor:  danyf90 <daniele.formichelli@gmail.com>
# Contributor: Philipp 'TamCore' B. <philipp [at] tamcore [dot] eu>
# Contributor: Jakub Schmidtke <sjakub-at-gmail-dot-com>
# Contributor: Christoph Brill <egore911-at-gmail-dot-com>
# Contributor: Lubomir 'Kuci' Kucera <kuci24-at-gmail-dot-com>
# Contributor: Tad Fisher <tadfisher at gmail dot com>
# Contributor: Philippe Hürlimann <p@hurlimann.org>
# Contributor: Julian Raufelder <aur@raufelder.com>
# Contributor: Dhina17 <dhinalogu@gmail.com>
# Contributor: Kordian Bruck <k@bruck.me>
# Maintainer: VeryBaaad <verybaaad@outlook.com>

pkgname=android-studio-aarch64
pkgver=2026.1.2.10
_vername="quail2"
_jbrpkgver="25.0.3"
_jbrvername="b508.16"
pkgrel=2
pkgdesc="The official Android IDE (Stable branch)"
arch=('aarch64')
url="https://developer.android.com/"
license=('APACHE')
makedepends=()
depends=('alsa-lib' 'freetype2' 'libxrender' 'libxtst' 'which')
optdepends=('gtk2: GTK+ look and feel'
            'libgl: emulator support'
            'ncurses5-compat-libs: native debugger support')
options=('!strip')
source=("https://dl.google.com/dl/android/studio/ide-zips/$pkgver/android-studio-$_vername-linux.tar.gz"
        "https://cache-redirector.jetbrains.com/intellij-jbr/jbr_jcef-$_jbrpkgver-linux-aarch64-$_jbrvername.tar.gz"
        "$pkgname.desktop"
        "license.html")
sha256sums=('64445a54092e7056c6eb7f1a89ad116d0feec2ef5f965b8e594d62abdb58590f'
            'SKIP'
            '75de77113d7b34f1f08fbfc0886bda8605c785d05007b2ce21be6b141f2e6655'
            '9a7563f7fb88c9a83df6cee9731660dc73a039ab594747e9e774916275b2e23e')

package() {
  cd $srcdir/android-studio

  # Install the application
  install -d $pkgdir/{opt/$pkgname,usr/bin}
  cp -a bin lib plugins license LICENSE.txt build.txt product-info.json $pkgdir/opt/$pkgname
  ln -s /opt/$pkgname/bin/studio.sh $pkgdir/usr/bin/android-studio

  # Replace JBR
  mv $srcdir/jbr_jcef-$_jbrpkgver-linux-aarch64-$_jbrvername $pkgdir/opt/$pkgname/jbr

  # Copy licenses
  install -Dm644 LICENSE.txt "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.txt"
  install -Dm644 $srcdir/license.html "${pkgdir}/usr/share/licenses/${pkgname}/license.html"

  # Add the icon and desktop file
  install -Dm644 bin/studio.png $pkgdir/usr/share/pixmaps/$pkgname.png
  install -Dm644 $srcdir/$pkgname.desktop $pkgdir/usr/share/applications/$pkgname.desktop

  chmod -R ugo+rX $pkgdir/opt
}
