# Maintainer: Jan Houben <jan@nexttrex.de>
# Contributor: Jesus Alvarez <jeezusjr at gmail dot com>
#
# This PKGBUILD was generated by the archzfs build scripts located at
#
# http://github.com/archzfs/archzfs
#
pkgname="zfs-dkms-git"
_commit='b8a90418f3a9c23b89c5d2c729a4dd0fea644508'
pkgdesc="Kernel modules for the Zettabyte File System."

pkgver=2018.09.07.r4720.gb8a90418f
pkgrel=1
makedepends=("git")
arch=("x86_64")
url="http://zfsonlinux.org/"
source=("git+https://github.com/zfsonlinux/zfs.git#commit=${_commit}")
sha256sums=("SKIP")
license=("CDDL")
depends=("zfs-utils-common-git=${pkgver}" "lsb-release" "dkms")
provides=("zfs")
groups=("archzfs-dkms-git")
conflicts=('zfs-dkms' 'spl-dkms-git' 'zfs-archiso-linux' 'zfs-archiso-linux-git' 'zfs-linux-hardened' 'zfs-linux-hardened-git' 'zfs-linux-lts' 'zfs-linux-lts-git' 'zfs-linux' 'zfs-linux-git' 'zfs-linux-vfio' 'zfs-linux-vfio-git' 'zfs-linux-zen' 'zfs-linux-zen-git'  'zfs-archiso-linux-headers' 'zfs-archiso-linux-git-headers' 'zfs-linux-hardened-headers' 'zfs-linux-hardened-git-headers' 'zfs-linux-lts-headers' 'zfs-linux-lts-git-headers' 'zfs-linux-headers' 'zfs-linux-git-headers' 'zfs-linux-vfio-headers' 'zfs-linux-vfio-git-headers' 'zfs-linux-zen-headers' 'zfs-linux-zen-git-headers' )
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
