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

# Maintainer:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer:
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributor:
#   Pierre Schmitz
#     <pierre@archlinux.de>
# Contributor:
#   Bartłomiej Piotrowski
#     <bpiotrowski@archlinux.org>

# shellcheck disable=SC2034
if [[ ! -v "_git" ]]; then
  _git="true"
fi
if [[ ! -v "_offline" ]]; then
  _offline="true"
fi
if [[ ! -v "_ssh" ]]; then
  _ssh="false"
fi
_py="python"
_proj="hip"
_distro="life"
_component="keyring"
_pkg="${_distro}-${_component}"
pkgbase="${_pkg}-git"
pkgname=(
  "${pkgbase}"
)
_tag="20250523" # git rev-parse ${pkgver}
pkgver="${_tag}" # "$(date +%Y.%m.%d)"
pkgrel=1
_pkgdesc=(
  'Life PGP keyring.'
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://gitlab.${_proj}.org/${_proj}/${_pkg}"
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${_pkg}"
license=(
  'GPL3'
)
groups=(
  'base-devel'
  "${_proj}"
)
install="${_pkg}.install"
depends=(
  "pacman"
)
makedepends=(
  "${_py}"
  'sequoia-sq'
)
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    "git"
  )
fi
checkdepends=(
  "${_py}-coverage"
  "${_py}-pytest"
)
_branch="main"
_tag="${_branch}"
_tag_name="branch"
_tarname="${_pkg}-${_tag}"
_url="${url}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${_pkg}"
fi
if [[ "${_ssh}" == "true" ]]; then
  _url="ssh://${_distro}_local_git/home/git/${_pkg}"
fi
if [[ "${_git}" == "true" ]]; then
  _uri="git+${_url}#${_tag_name}=${_tag}"
  _src="${_tarname}::${_uri}"
elif [[ "${_git}" == "false" ]]; then
  _src="${_tarname}.tar.xz::${_uri}"
fi
source=(
  "${_src}"
)
sha256sums=(
  'SKIP'
)
validpgpkeys=(
  # Pellegrino Prevete
  #   <pellegrinoprevete@gmail.com>
  # '3D115DD206D92A0656C827BC8B686E3C22E4C2FA'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'

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
