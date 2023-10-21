# Installation de QEMU et Virt Manager

Nous avons appris à personnaliser un noyau, ajouter des modules et les configurer, puis à les installer dans WSL 2. À quoi cela nous sert-il ? Grâce à la virtualisation KVM imbriquée, nous pouvons utiliser des outils comme minikube pour exécuter des conteneurs [Kubernetes](https://kubernetes.io/). 

#### `Objectif 3 : Installer QEMU et Virt Manager`

De plus, avec [QEMU](https://www.qemu.org/), nous pouvons faire fonctionner des systèmes d'exploitation complets, y compris Linux, macOS, [Arca Noae](https://www.arcanoae.com/), OpenIndiana et Haiku. 

> [!NOTE]
> Ce qui est particulièrement intéressant, c'est que nous avons la possibilité d'ajouter directement des images [Cisco](https://www.cisco.com/) à QEMU.

1. La première étape consiste à installer tous les `packages` nécessaires :

```bash
# Mettez à jour les paquets disponibles
sudo apt update
# Installons les paquets nécessaires pour QEMU, KVM, Virt Manager et d'autres utilitaires
sudo apt install qemu quem-kvm virt-manager virt-viewer dnsmasq vde2 bridge-utils netcat-openbsd dmidecode
# Vérifions les ports en cours d'utilisation, y compris le port 53 (peut être utile pour DNS)
sudo lsof -i :53
```

2. Installer `libguestfs` sur Ubuntu

[libguestfs](https://www.libguestfs.org/) est un ensemble d'outils utilisés pour accéder et modifier les images disque de machines virtuelles (VM) :

```bash
# Activer le compte utilisateur standard pour utiliser KVM
sudo useradd -g $USER libvirt
sudo useradd -g $USER libvirt-kvm
# installer libguestfs
sudo apt install libguestfs-tools
```

3. Démarrons le service [libvirt](https://libvirt.org/index.html) pour qu'il démarre au démarrage :

```bash
sudo systemctl status libvirtd.service
```
![libvirtd.service](../images/libvirtd.png)

4. Puisque nous souhaitons utiliser notre compte utilisateur Linux standard pour gérer KVM, configurons KVM pour permettre cela. Ouvrez le fichier `/etc/libvirt/libvirtd.conf` pour le modifier.

```bash
sudo vim /etc/libvirt/libvirtd.conf
```

```ini
# Set - la propriété du groupe de sockets de domaine UNIX sur libvirt
unix_sock_group = "libvirt"
# Set - les autorisations du socket UNIX pour le socket R/W
unix_sock_rw_perms = "0770"
```

5. Redémarrez le démon libvirt.

```bash
sudo systemctl restart libvirtd.service
```
![groups](../images/groups.png)

Nous avons installé avec succès KVM, QEMU et Virt Manager sur Ubuntu.

![virt-manager](../images/virt-manager.png)

## Ressources supplémentaires

- Pour plus de détails, vous pouvez consulter le lien suivant: [Welcome to QEMU’s documentation!](https://www.qemu.org/docs/master/index.html)

## Mots techniques

`QEMU, Virt Manager, KVM, quem-kvm, Virtualisation, UDNSMasq, groups, libguestfs, Bridge-Utils`.