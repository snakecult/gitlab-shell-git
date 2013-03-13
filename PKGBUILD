# Maintainer: David Andersen <arch@davidandersen.us>
pkgname=gitlab-shell-git
pkgver=1.1.0
pkgrel=1
pkgdesc="gitlab-shell: ssh access and repository management"
arch=(any)
url="https://github.com/gitlabhq/gitlab-shell"
license=('AGPLv3')
 
depends=('ruby' 
)
makedepends=('git')
optdepends=(
)
provides=('gitlab-shell')
backup=('home/git/gitlab-shell/config.yml')
install=.install
_gitname="gitlab-shell"

build() {
	if [ ! -d "$_gitname" ] 
	then
		git clone https://github.com/gitlabhq/gitlab-shell.git --depth=1
	fi
}

package() {
    mkdir -p "$pkgdir/home/git"
    cp -r "$srcdir/gitlab-shell" "$pkgdir/home/git"
    cp "$srcdir/gitlab-shell/config.yml.example" "$pkgdir/home/git/gitlab-shell/config.yml"
    rm -rf "$pkgdir/home/git/gitlab-shell/.git"
    rm "$pkgdir/home/git/gitlab-shell/.gitignore"
    chown -R git:git "$pkgdir/home/git"
}

