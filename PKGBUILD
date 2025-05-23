# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributor: Pierre Schmitz <pierre@archlinux.de>
# Contributor: Bartłomiej Piotrowski <bpiotrowski@archlinux.org>

# shellcheck disable=SC2034
if [[ ! -v "_offline" ]]; then
  _offline="true"
fi
_distro="life"
pkgbase="${_distro}-keyring"
pkgname=(
  "${pkgbase}"
)
_tag="20220731" # git rev-parse ${pkgver}
pkgver="${_tag}" # "$(date +%Y.%m.%d)"
pkgrel=1
pkgdesc='Life PGP keyring.'
arch=(
  'any'
)
_url="ssh://${_distro}_local_git/home/git/${pkgbase}"
url="https://gitlab.${_distro}.org/${_distro}/${pkgbase}"
license=(
  'GPL3'
)
groups=(
  'base-devel'
  'hip'
)
install="${pkgname}.install"
depends=(
  'pacman'
)
makedepends=(
  'git'
  'python'
  'sequoia-sq'
)
checkdepends=(
  'python-coverage'
  'python-pytest'
)
source=(
  "${pkgname}::git+${_url}#tag=${_tag}?signed"
)
sha256sums=(
  'SKIP'
)
validpgpkeys=(
  # Pellegrino Prevete
  '3D115DD206D92A0656C827BC8B686E3C22E4C2FA'
)

build() {
  cd \
    "${pkgname}" || \
    exit
  make \
    build
}

check() {
  cd \
    "${pkgname}" || \
    exit
  make \
    check
}

package() {
  cd \
    "${pkgname}" || \
    exit
  # shellcheck disable=SC2154
  make \
    PREFIX='/usr' \
    DESTDIR="${pkgdir}" \
    install
}

# vim:set sw=2 sts=-1 et:
