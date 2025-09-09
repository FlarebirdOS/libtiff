pkgname=libtiff
pkgver=4.7.0
pkgrel=2
pkgdesc="Library for manipulation of TIFF images"
arch=('x86_64')
url="http://www.simplesystems.org/libtiff"
license=('libtiff')
depends=(
    'gcc-libs'
    'glibc'
    'jbigkit'
    'libdeflate'
    'libjpeg-turbo'
    'libwebp'
    'zlib'
    'xz'
    'zstd'
)
makedepends=(
    'freeglut'
    'cmake'
    'ninja'
)
source=(https://download.osgeo.org/libtiff/${pkgname#lib}-${pkgver}.tar.gz)
sha256sums=(67160e3457365ab96c5b3286a0903aa6e78bdc44c4bc737d2e486bcecb6ba976)

build() {
    cd ${pkgname#lib}-${pkgver}

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D CMAKE_INSTALL_LIBDIR=lib64
        -D CMAKE_POLICY_VERSION_MINIMUM=3.5
        -D CMAKE_INSTALL_DOCDIR=/usr/share/doc/${pkgname}-${pkgver}
    )

    cmake "${cmake_args[@]}"

    cmake --build flarebird-build
}

package() {
    cd ${pkgname#lib}-${pkgver}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}
