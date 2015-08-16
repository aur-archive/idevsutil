# Maintainer: Nitin Mathew <nitn_mathew2000@hotmail.com>                                                                                             
                                                                                                                                                                                                                              
pkgname=idevsutil                      
pkgver=1.0.2.6                                                                                                    
pkgrel=1                                     
pkgdesc="File transfer program capable of efficient remote update via a fast differencing algorithm for IDrive"
arch=('x86_64')
url="http://evs.idrive.com/index.html"
license=('custom')
depends=('glibc' 'popt')
install=$pkgname.install
source=('http://evs.idrive.com/download/download-for-linux/idevsutil_linux64.zip' 'idevsutil.install')
sha256sums=('30cae40c94e316f58f796387b54388380a44848ff35981b6b84dafe5ca42e12a' '7f0c478dde8d960c93771efe83d3c5b1da220fac6f03539b91f6ef34f0e11031')

build() {
	#Create a License file from info from Readme since no explicit license is mentioned
	cd ${srcdir}/idevsutil_linux64
	sed -n '/\*For\ the\ TERMS\ /p' Readme.txt > LICENSE
}

package() {
	cd ${srcdir}/idevsutil_linux64
	install -D -m755 idevsutil ${pkgdir}/usr/bin/idevsutil || return 1
        install -D -m644 Readme.txt ${pkgdir}/usr/share/doc/idevsutil/Readme.txt
        install -D -m644 LICENSE ${pkgdir}/usr/share/licenses/idevsutil/LICENSE
	
	#Remove the downloaded source
	cd ../.. && rm -fr idevsutil_linux64.zip
}

