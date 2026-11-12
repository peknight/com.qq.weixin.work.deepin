# Maintainer: NekoLOvO <nekolyin@qq.com>
# Maintainer: peknight <JKpeknight@gmail.com>

# pkgname 跟随 deb 的 Package 字段（appid），保持稳定；上游 run.sh 里的
# BOTTLENAME 会随版本回跳（com.qq.weixin.work.deepin <-> Deepin-WXWork），
# 只影响 WINEPREFIX 目录 ~/.deepinwine/<BOTTLENAME>，不跟着改包名
pkgname=com.qq.weixin.work.deepin
pkgver=5.0.10.6015deepin3
pkgrel=1
pkgdesc="Deepin Wine 版企业微信 | Deepin-wine Wecom"
arch=('x86_64')
url="https://com-store-packages.uniontech.com/appstorev23/pool/appstore/c/com.qq.weixin.work.deepin/"
license=('custom')
depends=(
        'spark-dwine-helper'
        'deepin-wine10-stable'
)
source=(
    "${url}${pkgname}_${pkgver}_amd64.deb"
    "https://nexus.peknight.com/repository/raw-group/v1/https/github.com/anthonyfok/fonts-wqy-microhei/raw/refs/heads/master/wqy-microhei.ttc"
)
sha256sums=('8bc669b50eaaec9a3a4d327893fe9bd20d71e8dc1f10abb6b595da8cda589840'
            'e4bca8df123ce01b104780f576ea1a58b9a5ff1662a91124b6d3180cb6c88212')
install="wecom.install"

package() {
    bsdtar -xf "${srcdir}/data.tar.xz" -C "${pkgdir}/"
    install -Dm644 "wqy-microhei.ttc" "${pkgdir}/usr/share/fonts/truetype/wqy/wqy-microhei.ttc"
    cp -rf "${pkgdir}/opt/apps/${pkgname}/entries/"* "${pkgdir}/usr/share/"
    # 上游改用 deepin-wine-helper 的 run_v4.sh，Arch 侧由 spark-dwine-helper 提供等价脚本
    sed -i 's#^START_SHELL_PATH=.*#START_SHELL_PATH="/opt/deepinwine/tools/spark_run_v4.sh"#' \
        "${pkgdir}/opt/apps/${pkgname}/files/run.sh"
    # pre_run.sh 里的 gl-wine 探测同样指向 deepin-wine-helper，改到 spark-dwine-helper 的实际路径
    sed -i 's#/opt/deepinwine/tools/gl-wine/#/opt/spark-dwine-helper/spark_gl-wine/#g' \
        "${pkgdir}/opt/apps/${pkgname}/files/pre_run.sh"
}
