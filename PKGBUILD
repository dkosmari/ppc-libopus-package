_pkgname=opus
pkgname=ppc-lib${_pkgname}
pkgver=1.6.1
pkgrel=1
pkgdesc='The reference implementation of the Opus Codec.'
arch=('any')
url='https://opus-codec.org'
license=("BSD")
options=(!buildflags !strip libtool staticlibs)
source=("https://downloads.xiph.org/releases/${_pkgname}/${_pkgname}-${pkgver}.tar.gz")
makedepends=('ppc-pkg-config' 'dkp-toolchain-vars')
groups=('ppc-portlibs')

build() {
    source "${DEVKITPRO}/ppcvars.sh"

    cd "${_pkgname}-${pkgver}"

    ./configure \
        --host="powerpc-eabi" \
        --prefix="${PORTLIBS_PREFIX}" \
        --disable-shared \
        --enable-static \
        --disable-doc \
        --disable-extra-programs

    make V=1
}

package() {
    cd "${_pkgname}-${pkgver}"

    make install DESTDIR="${pkgdir}"
}

sha256sums=('6ffcb593207be92584df15b32466ed64bbec99109f007c82205f0194572411a1')
