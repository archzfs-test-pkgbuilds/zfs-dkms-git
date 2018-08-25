# Maintainer: Jan Houben <jan@nexttrex.de>
# Contributor: Jesus Alvarez <jeezusjr at gmail dot com>
#
# This PKGBUILD was generated by the archzfs build scripts located at
#
# http://github.com/archzfs/archzfs
#
pkgname="zfs-dkms-git"
pkgdesc="Kernel modules for the Zettabyte File System."

pkgver=2018.08.23.r4692.g55972a672
pkgrel=1
makedepends=("git")
arch=("x86_64")
url="http://zfsonlinux.org/"
source=("git+https://github.com/zfsonlinux/zfs.git#commit=55972a6724ca49d98d67a47fe0f0b28ad21260d5" 
        "upstream-ac09630-Fix-zpl_mount-deadlock.patch"
        "upstream-9f64c1e-Linux-4.18-compat-inode-timespec_timespec64.patch"
        "upstream-9161ace-Linux-compat-4.18-check_disk_size_change.patch")
sha256sums=("SKIP" 
            "1799f6f7b2a60a23b66106c9470414628398f6bfc10da3d0f41c548bba6130e8"
            "03ed45af40850c3a51a6fd14f36c1adc06501c688a67afb13db4fded6ec9db1d"
            "afbde4a2507dff989404665dbbdfe18eecf5aba716a6513902affa0e4cb033fe")
license=("CDDL")
depends=("zfs-utils-common-git=2018.08.23.r4692.g55972a672" "lsb-release" "dkms")
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
