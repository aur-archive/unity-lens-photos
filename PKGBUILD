# Maintainer: Charles Bos <charlesbos1 AT gmail>
# Contributor: Xiao-Long Chen <chenxiaolong@cxl.epac.to>

pkgname=unity-lens-photos
_actual_ver=1.0
_extra_ver=daily13.06.05
_source_date=20130605
_translations=20130418
pkgver=${_actual_ver}.${_source_date}
pkgrel=2
pkgdesc="Unity lens for browsing photos"
arch=('any')
url="https://launchpad.net/unity-lens-photos"
license=('GPL')
groups=('unity')
depends=('python-httplib2' 'python-gobject' 'python-oauthlib' 'dee' 'libunity' 'libsoup' 'libsoup-gnome')
makedepends=('python' 'python-distutils-extra')
source=("https://launchpad.net/ubuntu/+archive/primary/+files/unity-lens-photos_${_actual_ver}${_extra_ver}.orig.tar.gz"
        "https://dl.dropboxusercontent.com/u/486665/Translations/translations-${_translations}-unity-lens-photos.tar.gz")
sha512sums=('200b7f14c2c7263cd92c0ff710c5f12e66e69cd715d19556d06c3d5ef9c3a9f9baa9d8ecb575def501a01f2c82fcf3a2ce73814d27814091b4be7a8d4e84e907'
            '79ea835cd8c5b7c87d7129d51223ee1613589254ccde0be7d81bccd4f5916ba7a22b90fb54c18e766481a49bf6c0cbfe9dca719305627ffbe247aebb9888767f')

prepare() {
  cd "${srcdir}/${pkgname}-${_actual_ver}${_extra_ver}"

  msg "Merging translations from ${_translations}"
  rm -f po/LINGUAS po/*.pot
  mv "${srcdir}"/po/*.pot po/
  for i in "${srcdir}"/po/*.po; do
    FILE=$(sed -n "s|.*/${pkgname}-||p" <<< ${i})
    mv ${i} po/${FILE}
    echo ${FILE%.*} >> po/LINGUAS
  done
}

package() {
  cd "${srcdir}/${pkgname}-${_actual_ver}${_extra_ver}"

  python setup.py install --root="${pkgdir}/" --optimize=1
}

# vim:set ts=2 sw=2 et:
