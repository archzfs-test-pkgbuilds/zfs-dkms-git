# Maintainer: Jan Houben <jan@nexttrex.de>
# Contributor: Jesus Alvarez <jeezusjr at gmail dot com>
#
# This PKGBUILD was generated by the archzfs build scripts located at
#
# http://github.com/archzfs/archzfs
#
pkgname="zfs-dkms-git"
_commit='762f9ef3d9d897b5baf7c91d6e8a7bf371a9b02f'
pkgdesc="Kernel modules for the Zettabyte File System."

pkgver=2019.03.02.r4984.g762f9ef3d
pkgrel=1
makedepends=("git")
arch=("x86_64")
url="http://zfsonlinux.org/"
source=("git+https://github.com/zfsonlinux/zfs.git#commit=${_commit}")
sha256sums=("SKIP")
license=("CDDL")
depends=("zfs-utils-git=${pkgver}" "lsb-release" "dkms")
provides=("zfs" "zfs-headers" "spl" "spl-headers")
groups=("archzfs-dkms-git")
conflicts=("zfs" "zfs-headers" "spl" "spl-headers")
replaces=("spl-dkms-git")

build() {
    cd "${srcdir}/zfs"
    ./autogen.sh
}

package() {
    dkmsdir="${pkgdir}/usr/src/zfs-git"
    install -d "${dkmsdir}"
    cp -a ${srcdir}/zfs/. ${dkmsdir}
    cd "${dkmsdir}"
    find . -name ".git*" -print0 | xargs -0 rm -fr --
    scripts/dkms.mkconf -v git -f dkms.conf -n zfs
    chmod g-w,o-w -R .
}
