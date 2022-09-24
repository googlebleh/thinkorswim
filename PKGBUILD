# Maintainer: Colin Wee <2gbleh@gmail.com>

pkgname=thinkorswim
pkgver=8fda7cc
pkgrel=1
pkgdesc="Stocks and options trade client"
arch=(i686 x86_64)
url="https://www.thinkorswim.com"
depends=('zulu-11-bin')
license=('Copyright')
source=(
  "https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh"
  "thinkorswim.desktop"
)
sha256sums=(
  'b032cddfa145a3b7d5e23c8b3fdb780c613f9c357c811710809366d393f463ce'
  'dbc96c5c4d37df00481e84610e7ce4ff8d3db93fd5b68531f541e0b88a835aa5'
)

pkgver ()
{
  sha256sum thinkorswim_installer.sh | head -c 7
}

check ()
{
  if ! archlinux-java get | grep -q "^zulu-11$"; then
    echo "unsupported JRE detected. use:"
    echo "$ archlinux-java set zulu-11"
    return 1
  fi
}

# install()
# {
#   PATH=/usr/lib/jvm/java-7-jre/jre/bin:${PATH}
#   export PATH
#
#   JAVA_HOME=/usr/lib/jvm/java-7-jre/jre
#   export JAVA_HOME 
#   ./thinkorswim_installer.sh -q -dir /opt/thinkorswim
# }

post_remove ()
{
  sh /home/cwee/thinkorswim/uninstall
}

package ()
{
  # mkdir -p "$pkgdir/home/cwee/thinkorswim"
  # chmod 777 "$pkgdir/home/cwee/thinkorswim"

  # find ${pkgdir}
  unset _JAVA_OPTIONS
  sh thinkorswim_installer.sh -q -dir /home/cwee/thinkorswim
  install -D -m 755 thinkorswim.desktop "$pkgdir/usr/local/share/applications/thinkorswim.desktop"
}

