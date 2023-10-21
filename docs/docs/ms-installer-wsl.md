---
title: Install WSL
auteur: Mehdi sellami
---

# Windows Subsystem for Linux 2

La configuration d'un environnement de test avec EVE-NG, KVM/QEMU et WSL 2 sur un hôte Windows 11 peut sembler complexe, mais avec des étapes spécifiques, elle peut être réalisée avec succès.

#### `Objectif 1 : Installer WSL 2 sur Windows`

Cet objectif se concentre sur l'installation de WSL 2 sur notre système Windows, une étape essentielle pour créer cet environnement de test.

## Étapes d'Installation

Ci-dessous, nous présentons un aperçu des étapes d'installation ainsi que des problèmes potentiels que vous pourriez rencontrer :

#### `1. Installation de WSL`

Pour exécuter WSL 2, nous devons utiliser Windows 10 version 1903 ou ultérieure, avec la version 18362 ou ultérieure du système d'exploitation. 

```powershell
# Vérification de la version Windows requise
Key + R puis tapez winver
```
Si vous utilisez une version antérieure, veuillez accéder à Windows Update sur votre ordinateur et installer toutes les mises à jour en attente.

```powershell
# Ouvrez PowerShell en tant qu'administrateur, puis entrez cette commande
Wsl.exe --install
```

```powershell
# Définir la version 2 de WSL comme version par défaut
wsl --set-default-version 2
```

#### `2. Utilisation de .wslconfig`

Dans ce projet, nous travaillons avec WSL 2, donc nous n'avons pas besoin de "wsl.conf" (qui correspond à la version 1 de WSL). Nous allons directement configurer le fichier ".wslconfig". 

> [!Note]
> Vous pouvez le trouver dans: (`"C:\\Users\\nom_user\\.wslconfig"`).

Voici la configuration que nous ajoutons à ce fichier :

```ini
[wsl2]
# Active la récupération automatique de mémoire
autoMemoryReclaim=enable
# Définit la quantité de mémoire allouée (12 Go)
memory=12GB
# Définit le nombre de processeurs virtuels (6)
processors=6
# Définit la taille de la mémoire de swap (4 Go)
swap=4GB
# Définit le chemin du fichier de mémoire de swap
swapfile=C:\\wslswap.vhdx
# Autorise la redirection locale (localhost forwarding)
localhostForwarding=true
# Active la virtualisation imbriquée (nested virtualization)
nestedVirtualization=true
```

#### `3. Contrôle de WSL`

Pour gérer WSL, nous pouvons utiliser diverses commandes. Voici quelques exemples :

```powershell
# Pour obtenir de l'aide sur WSL :
wsl --help
# Pour obtenir la liste des distributions en cours d'exécution
wsl --list
# Pour obtenir la liste des distributions en cours d'exécution :
wsl --list --running
# Pour obtenir une liste détaillée des distributions WSL : 
wsl --list –verbose
# Pour exécuter des commandes Linux avec la commande wsl
wsl ls ~
wsl cat /etc/issue
wsl -d Ubuntu-20.04 cat /etc/issue
wsl whoami
# Pour arrêter une distribution WSL spécifique : 
wsl --terminate Ubuntu-20.04
# Pour arrêter toutes les distributions WSL en cours d'exécution :
wsl --shutdown
```
## Problèmes Potentiels et Solutions

Lors de la configuration de WSL 2, nous pourrions rencontrer certains problèmes, mais voici les solutions proposées :

Problème | Description | Statut
-----    | ----            | ----
*Problème* | *- Utilisation excessive de la mémoire*. | *VmmemWSL*
*Solution* | *- autoMemoryReclaim=`enable` et memory=`12GB`*. | *.wslconfig*

## Ressources supplémentaires

- Pour plus de détails, vous pouvez consulter le lien suivant sur *Learn Microsoft* : [How to install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install#requirements).

## Mots techniques

`Microsoft, WSL 2, wsl.conf, .wslconfig, Récupération automatique de mémoire (libérer), Mémoire de swap, localhost forwarding (port), nested virtualization, Windows 11, Ubuntu-20.04, PowerShell, Windows Update.`