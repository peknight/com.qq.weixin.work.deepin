# Maintainer: NekoLOvO <nekolyin@qq.com>
# Maintainer: peknight <JKpeknight@gmail.com>

pkgname=com.qq.weixin.work.deepin
pkgver=5.0.0.8002deepin1
pkgrel=1
pkgdesc="Deepin Wine 版企业微信 | Deepin-wine Wecom"
arch=('i686' 'x86_64')
url="https://nexus.peknight.com/repository/raw-group/v1/https/mirrors.sdu.edu.cn/spark-store-repository/store/chat/com.qq.weixin.work.deepin/"
license=('custom')
depends=(
        'spark-dwine-helper'
        'deepin-wine10-stable'
        'wqy-microhei'
)
source=(
    "${url}${pkgname}_${pkgver//_/-}_all.deb"
)
sha256sums=('a462be7eb76218e9bea55a3ffa656669768de8fa6b224dcaba86c148265f2bc8')
install="wecom.install"

package() {
    cp -r ${srcdir}/opt "${pkgdir}/"
    cp -rf ${pkgdir}/opt/apps/${pkgname}/entries/* "${pkgdir}/usr/share/"
}
