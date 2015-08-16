# Maintainer: Andreas Wagner <AndreasBWagner@pointfree.net>
# Contributor: Stijn Segers <`echo 'moc tod liamg ta skcuneeltog' | rev`>

pkgname=libsocket
pkgver=1.8
pkgrel=3
pkgdesc="Generic C++ socket library"
arch=('i686' 'x86_64')
depends=('gcc-libs')
url="http://www.happycoders.org/software/libsocket.php"
license=('LGPL2.1')
source=("http://www.speedblue.org/conf/$pkgname-$pkgver.tar.gz"
        'includes.patch')
sha1sums=('410c48dc97a9508cf87d5bafb32eec3e4b1f68f1'
          'bd71bfe775f3d6ca714f0abcf23aacc97452eddf')

build() {
	cd $srcdir/$pkgname-$pkgver

	# Fix includes
	patch -Np1 -i $srcdir/${source[1]}
	# Fix the paths; another subdir might be handy for their own
	# projects but not for external software
	sed -i 's|happycoders/||' $srcdir/$pkgname-$pkgver/src/Makefile.in

	./configure --prefix=/usr #LIBS=-lsocket
	make
}

package() {
	cd $srcdir/$pkgname-$pkgver
	make install DESTDIR=$pkgdir

	# License file
	install -D -m644 COPYING $pkgdir/usr/share/licenses/$pkgname/COPYING
}

