# Maintainer: Kevin Slagle <kjslag at gmail dot com>

pkgname=feynarts
_pkgname=FeynArts
pkgver=3.8
pkgrel=1
pkgdesc="A Mathematica package for the generation and visualization of Feynman diagrams and amplitudes"
arch=('any')
install=feynarts.install
url="http://www.feynarts.de/"
license=('LGPL')
#depends=('')
#makedepends=('')
optdepends=('mathematica: to actually use FeynArts')
source=(http://www.feynarts.de/$_pkgname-$pkgver.tar.gz)
md5sums=('defd9ee51d8831a97b529d693549fc5e')
options=('!strip')

build() {
  dest_dir="$pkgdir/opt/$pkgname"
  mkdir -p "$pkgdir/opt"
  mv       "$srcdir/$_pkgname-$pkgver" "$dest_dir"
  
  # doesn't work :(
  #MathematicaPackages="$pkgdir/opt/Mathematica/AddOns/Packages"
  #mkdir -p "$MathematicaPackages"
  #ln    -s "../../../$pkgname" "$MathematicaPackages/FeynArts"
  
  sty_dir="$pkgdir/usr/share/texmf/tex/latex/feynarts"
  mkdir -p "$sty_dir"
  mv       "$dest_dir/feynarts.sty" "$sty_dir"
  
  # When running commands like
  # CreateTopologies[0, 3 -> 3, Adjacencies -> 4]
  # FeynArts asks you to modify the diagram, and then saves the results in /opt/feynarts/ShapeData.
  # This is a workaround so that FeynArts has permission to do this.
  # It would be nicer to save data in a new directory: ~/.conf/feynarts/ShapeData.
  # But I don't know how to do this.
  chmod a+w "$dest_dir/ShapeData"
}
