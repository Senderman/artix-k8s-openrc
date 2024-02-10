# Maintainer: Senderman <doletov.fyodor@yandex.ru>

pkgname=(
    kube-apiserver-openrc
    kube-controller-manager-openrc
    kube-proxy-openrc
    kube-scheduler-openrc
    kubelet
)

pkgver=1.0.0
pkgrel=1
arch=('any')
url="https://github.com/Senderman/artix-k8s-openrc/"
license=('Apache-2.0')
source=(
	kube-apiserver.initd
	kube-apiserver.confd
	kube-apiserver.logrotated

	kube-controller-manager.initd
	kube-controller-manager.confd
	kube-controller-manager.logrotated

	kube-proxy.initd
	kube-proxy.confd
	kube-proxy.logrotated

	kube-scheduler.initd
	kube-scheduler.confd
	kube-scheduler.logrotated

	kubelet.initd
	kubelet.confd
	kubelet.logrotated
)

sha256sums=(
    'd9eb05ed778cd2b34a516574d012e28cfecc8b1700ae5bf65aea98c2940968a2'
    '41c807a6b97b5cb309fb83a9c201956849d9e26da160825cc14e64aaa258e327'
    '27232cac89ee8436333872e1e89e82a3708fe25dd91c110e828387c700e9cf29'
    'cf375447de499b8013e03671e38169190ee2228e328627d67a7f865655c35801'
    'ea2466e1bb38bae00f5aed7980ede874916f09cd5e8c9dc814b9f75e5f7dd310'
    'd6a51d4753956b17c6b308a9e831bbe9553c3ea33cf9cdb47e01d1f1942e487d'
    'e7c0743815fb5dccffdda96e70c88968c21c0419bdfb4e064b292659c03249c5'
    'a64f7683e165325c7ea27d75f1072a9aab33f3bb6dbd3cde10c62e0e39cc4876'
    '30da28b2de73b267ba209ae37c63f34f7a8997b1a151795161eb728b960b2cac'
    'beaa7928565cef3b0b73f7d30f3e21b950631431c6ba6593bbaded16e7c4927f'
    '113c237335b8b103a6173ff9a01cfd5071d94880e90057f6494b61ab98d5c1a8'
    '03458ca43bf70c5991caa6a47ed8b796592a958a06eb2db6d734f196920dfd79'
    'c7b5bf2d08fe24ea418ebca691bad90f7396bc9e5a7aca44325ab0b492500010'
    'd8485ed172676093c8feb9e31471f1654709de7c1e5cb4d003bafabeb0665d1d'
    '1e2547a1ab5fe31037b6180fab1d0cda1a34c4718d99c6e3002b2db80fb3d048'
)

# $1 - package, #2 - $pkgdir
install-pkg(){
    pkg="$1"
    dest="$2"

    install -d "$dest/var/log/$1"
    install -Dm644 "$srcdir/${pkg}.logrotated" "$dest/etc/logrotate.d/$pkg"
    install -Dm755 "$srcdir/${pkg}.initd" "$dest/etc/init.d/$pkg"
    install -Dm644 "$srcdir/${pkg}.confd" "$dest/etc/conf.d/$pkg"
}

package_kube-apiserver-openrc(){
    pkgdesc='Kubernetes - kube-apiserver (OpenRC init scripts)'
    depends=('openrc' 'kube-apiserver')
    provides=('init-kube-apiserver')
    conficts=('init-kube-apiserver')
    install-pkg 'kube-apiserver' "$pkgdir"
}

package_kube-controller-manager-openrc(){
    pkgdesc='Kubernetes - kube-controller-manager (OpenRC init scripts)'
    depends=('openrc' 'kube-controller-manager')
    provides=('init-kube-controller-manager')
    conficts=('init')
    install-pkg 'kube-controller-manager' "$pkgdir"
}

package_kube-proxy-openrc(){
    pkgdesc='Kubernetes - kube-proxy (OpenRC init scripts)'
    depends=('openrc' 'kube-proxy')
    provides=('init-kube-proxy')
    conficts=('init-kube-proxy')
    install-pkg 'kube-proxy' "$pkgdir"
}

package_kube-scheduler-openrc(){
    pkgdesc='Kubernetes - kube-scheduler (OpenRC init scripts)'
    depends=('openrc' 'kube-scheduler')
    provides=('init-kube-scheduler')
    conficts=('init-kube-scheduler')
    install-pkg 'kube-scheduler' "$pkgdir"
}

package_kubelet(){
    pkgdesc="Kubernetes - kubelet (OpenRC init scripts)"
    depends=('openrc' 'kubelet')
    provides=('init-kubelet')
    conficts=('init-kubelet')
    install-pkg 'kubelet' "$pkgdir"
}
