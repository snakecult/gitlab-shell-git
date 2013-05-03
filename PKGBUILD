# Maintainer: David Andersen <arch@davidandersen.us>
pkgname=gitlab-shell-git
pkgver=1.1.0
pkgrel=2
pkgdesc="gitlab-shell: ssh access and repository management"
arch=(any)
url="https://github.com/gitlabhq/gitlab-shell"
license=('AGPLv3')

depends=('ruby'
)
makedepends=('git')
optdepends=(
)
install='gitlab-shell.install'
provides=('gitlab-shell')
backup=('etc/gitlab-shell/config.yml')
install=.install
_gitname="gitlab-shell"

build() {
	if [ ! -d "$_gitname" ]
	then
		git clone -b v$pkgver https://github.com/gitlabhq/gitlab-shell.git
	fi
}

_homedir="/home/git/gitlab-shell"

package() {
	mkdir -p "${pkgdir}/$_homedir"
	cp -rT "$srcdir/gitlab-shell" "${pkgdir}/$_homedir"
	#    rm -rf "${pkgdir}/$_homedir/.git"
	rm "${pkgdir}/$_homedir/.gitignore"

	chmod 750 "$pkgdir/$_homedir"
	chown -R git:git "${pkgdir}/$_homedir"

	install -Dm0644 "$srcdir/gitlab-shell/config.yml.example" "$pkgdir/etc/gitlab-shell/config.yml"
	#    mkdir -p "$pkgdir/etc/gitlab-shell"
	#    cp "$srcdir/gitlab-shell/config.yml.example" "$pkgdir/etc/gitlab-shell/config.yml"
	ln -s "/etc/gitlab-shell/config.yml" "${pkgdir}/$_homedir/config.yml"

	#    chown -R git:git "$pkgdir/etc/gitlab-shell"
}

