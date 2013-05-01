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
backup=('etc/gitlab-shell/config.yml')
install=.install
_gitname="gitlab-shell"

build() {
	if [ ! -d "$_gitname" ] 
	then
		git clone https://github.com/gitlabhq/gitlab-shell.git --depth=1
	fi
}

_homedir="$pkgdir/home/git/gitlab-shell"

package() {
    mkdir -p "$_homedir"
    cp -rT "$srcdir/gitlab-shell" "$_homedir"
    rm -rf "$_homedir/.git"
    rm "$_homedir/.gitignore"

    chown -R git:git "$_homedir"

    install -Dm0644 "$srcdir/gitlab-shell/config.yml.example" "$pkgdir/etc/gitlab-shell/config.yml"
#    mkdir -p "$pkgdir/etc/gitlab-shell"
#    cp "$srcdir/gitlab-shell/config.yml.example" "$pkgdir/etc/gitlab-shell/config.yml"
    ln -s "/etc/gitlab-shell/config.yml" "$_homedir/config.yml"

#    chown -R git:git "$pkgdir/etc/gitlab-shell"
}

