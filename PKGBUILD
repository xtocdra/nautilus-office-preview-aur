# Maintainer: xtocdra <212695089+xtocdra at users.noreply.github.com>

pkgname=nautilus-office-preview
pkgver=1.0.0
pkgrel=1
pkgdesc='DOCX, XLSX and PPTX previews for GNOME Nautilus Sushi'
arch=('any')
url='https://github.com/xtocdra/nautilus-office-preview'
license=('0BSD' 'Apache-2.0' 'BSD-3-Clause' 'ISC' 'MIT' 'MPL-2.0' 'Zlib')
depends=(
    'sushi>=51.2'
    'gjs'
    'libadwaita'
    'webkitgtk-6.0'
)

source=(
    "$pkgname-$pkgver.tar.gz::https://github.com/xtocdra/nautilus-office-preview/archive/refs/tags/v${pkgver}.tar.gz"
)

# Temporary placeholder. Replace with the verified GitHub archive checksum.
sha256sums=('544b90a38ea1a7a5f1b66d43894e76e4a0b96ca9ea9157f87a1f869e85ba1f18')

package() {
    local source_dir="$srcdir/$pkgname-$pkgver"
    local plugin_dir="$pkgdir/usr/lib/sushi/plugins-1"

    # Unified Sushi plugin.
    install -Dm644 \
        "$source_dir/office-preview.js" \
        "$plugin_dir/office-preview.js"

    # Bundled DOCX, XLSX and PPTX viewers.
    install -d "$plugin_dir/office-preview"

    cp -a \
        "$source_dir/office-preview/." \
        "$plugin_dir/office-preview/"

    # Main project license.
    install -Dm644 \
        "$source_dir/LICENSE" \
        "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

    # Third-party license texts and attribution.
    install -d \
        "$pkgdir/usr/share/licenses/$pkgname/THIRD-PARTY-LICENSES"

    cp -a \
        "$source_dir/THIRD-PARTY-LICENSES/." \
        "$pkgdir/usr/share/licenses/$pkgname/THIRD-PARTY-LICENSES/"

    # Project documentation.
    install -Dm644 \
        "$source_dir/README.md" \
        "$pkgdir/usr/share/doc/$pkgname/README.md"

    install -Dm644 \
        "$source_dir/CHANGELOG.md" \
        "$pkgdir/usr/share/doc/$pkgname/CHANGELOG.md"

    # Preserve the MPL-2.0 dependency source.
    install -d \
        "$pkgdir/usr/share/doc/$pkgname/THIRD-PARTY-SOURCES"

    cp -a \
        "$source_dir/THIRD-PARTY-SOURCES/mtx-decompressor" \
        "$pkgdir/usr/share/doc/$pkgname/THIRD-PARTY-SOURCES/"
}
