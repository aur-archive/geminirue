# Maintainer: Mathieu Westphal <mathieu.westphal@gmail.com>

pkgname=geminirue
pkgver=1.0.20131228
_hibver=1387557938
pkgrel=0
pkgdesc="A science-fiction dystopian adventure game "
arch=('i686' 'x86_64')
url="http://www.wadjeteyegames.com/games/gemini-rue/"
license=('custom:commercial')
depends=('libvorbis' 'libtheora' 'libxpm' 'libxxf86dga' 'sdl2' 'alsa-lib' 'freetype2' )
PKGEXT='.pkg.tar'
DLAGENTS+=('hib::/usr/bin/echo "Could not find %u. Manually download it to \"$(pwd)\", or set up a hib:// DLAGENT in /etc/makepkg.conf."; exit 1')
_installer="GeminiRue_linux_${_hibver}.sh"
source=( "hib://${_installer}"
         'geminirue.desktop' )

[ $CARCH == "i686" ] && _arch='x86' || _arch='x86_64'
[ $CARCH == "i686" ] && _libmod='' || _libmod='64'
package() {
    cd $srcdir
    _installdir=/opt/GeminiRue; _target="$pkgdir"$_installdir; _libdir="$_target/lib$_libmod"

# Install game files
        mkdir -p "$_target"
        cp ./data/noarch/* $_target
        cp ./data/$_arch/GeminiRue.bin.$_arch $_target
        mkdir -p "$_libdir"
        cp ./data/$_arch/lib$_libmod/*alleg* $_libdir

# Install icon & desktop entry
        install -Dm644 ./data/noarch/GeminiRue.png \
                 "$pkgdir"/usr/share/pixmaps/geminirue.png
        install -Dm644 $pkgname.desktop \
                 "$pkgdir"/usr/share/applications/$pkgname.desktop


# Install launcher symlink
        install -d "$pkgdir"/usr/bin
        ln -s $_installdir/GeminiRue.bin.$_arch "$pkgdir"/usr/bin/geminirue
}

md5sums=('06e70af3712d04568951000aa59c5d63'
         'd594f0f5bf91adf00cfae447cba6ef45')
