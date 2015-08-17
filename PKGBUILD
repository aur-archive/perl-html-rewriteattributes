# Maintainer: Maxwell Pray a.k.a. Synthead <synthead@gmail.com>

pkgname='perl-html-rewriteattributes'
_cpanname='HTML-RewriteAttributes'
pkgver='0.05'
pkgrel=1
pkgdesc='Concise attribute rewriting'
arch=('any')
url="http://search.cpan.org/~tsibley/$_cpanname-$pkgver/"
license=(
	'GPL'
	'PerlArtistic'
)
depends=(
	'perl-regexp-common'
	'perl>=5.5.0'
)
options=('!emptydirs')
source=("http://search.cpan.org/CPAN/authors/id/T/TS/TSIBLEY/$_cpanname-$pkgver.tar.gz")
md5sums=('808ac50716f778f410a87658bd00f40c')

# Function to change to the working directory and set
# environment variables to override undesired options.
prepareEnvironment() {
	cd "$srcdir/$_cpanname-$pkgver"
	export \
		PERL_MM_USE_DEFAULT=1 \
		PERL_AUTOINSTALL=--skipdeps \
		PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'" \
		PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
		MODULEBUILDRC=/dev/null
}

build() {
	prepareEnvironment
	/usr/bin/perl Makefile.PL
	make
}

check() {
	prepareEnvironment
	make test
}

package() {
	prepareEnvironment
	make install

	# Remove "perllocal.pod" and ".packlist".
	find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
