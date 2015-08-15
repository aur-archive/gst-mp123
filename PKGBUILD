# Maintainer: Alois Nespor <info at aloisnespor dot info>
 
pkgname=gst-mp123
pkgver=20120514
pkgrel=1
pkgdesc=" a MPEG audio decoder using libmpg123 as decoder library."
arch=('i686' 'x86_64')
url="https://github.com/lazka/gst-mpg123.git"
license=('LGPL')
depends=('gstreamer0.10-base' 'mpg123')
makedepends=('pkgconfig')

_gitroot="git://github.com/lazka/gst-mpg123.git"
_gitname="gst-mpg123"

build() {

  msg "Connecting to the git repository..."
  if [ -d "$srcdir/$_gitname" ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
  cd "$srcdir"
  rm -rf $_gitname-build
  git clone $_gitname $_gitname-build
  cd $_gitname-build

  ./autogen.sh
  ./configure --prefix=/usr
}
 
package() {
  cd $srcdir/$_gitname-build
  make DESTDIR="$pkgdir/" install
}