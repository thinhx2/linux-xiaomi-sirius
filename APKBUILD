# Maintainer: thinhx2 <nthinh1102@gmail.com>

# Reference: <https://postmarketos.org/vendorkernel>
# Kernel config based on: arch/arm64/configs/sirius_user_defconfig

pkgname=linux-xiaomi-sirius
pkgver=4.9.228
pkgrel=1
pkgdesc="Xiaomi MI 8 SE kernel fork"
arch="aarch64"
_carch="arm64"
_flavor="xiaomi-sirius"
url="https://kernel.org"
license="GPL-2.0-only"
options="!strip !check !tracedeps pmb:cross-native"
makedepends="bash bc bison devicepkg-dev flex openssl-dev perl"

# Source
_repository="msm-4.99"
_commit="cddc756a0a27137870c8b625c39b1565ceb95537"
_config="config-$_flavor.$arch"
source="
	$pkgname-$_commit.tar.gz::https://github.com/thinhx2/$_repository/archive/$_commit.tar.gz
	$_config
"
builddir="$srcdir/$_repository-$_commit"
_outdir="out"

prepare() {
	default_prepare
	REPLACE_GCCH=0
	. downstreamkernel_prepare
}

build() {
	unset LDFLAGS
	make ARCH="$_carch" CC="${CC:-gcc}" \
		KBUILD_BUILD_VERSION="$((pkgrel + 1 ))-postmarketOS" \
		O="$_outdir"
}

package() {
	downstreamkernel_package "$builddir" "$pkgdir" "$_carch" "$_flavor" "$_outdir"
}

sha512sums="43937966464b12c05a083dcdf4a46e7437a705dc993ec16ae049aa3d2895ecdd9b603947d845711cd2a4fd8b04ce061bfaff7ca3c49dd60a39cf7a5f9bf357e3  linux-xiaomi-sirius-cddc756a0a27137870c8b625c39b1565ceb95537.tar.gz
af0e448b60195b97e98e76ac5b5f36ccf333deef439dbd8b84b7388edc47c8d3b252207f7dbd5888389fb2f714bd51b1e519167330d92d9836dbe6454ec2052c  config-xiaomi-sirius.aarch64"
