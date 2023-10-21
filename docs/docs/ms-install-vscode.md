# Installer VS Code (Microsoft)

**Visual Studio Code** est un `éditeur` de code léger, extensible et très populaire. Il est largement utilisé par les développeurs pour divers langages de programmation et fournit de nombreuses fonctionnalités pour `améliorer` notre productivité.

#### `Objectif 6 : Installer Visual Studio Code`

## Installation et configuration

Pour installer Visual Studio Code (VS Code), suivons ces étapes :

1. Accédons au site officiel de [Visual Studio Code](https://code.visualstudio.com/).

![Visual Studio Code](/images/vscode.png)

2. Téléchargeons la version appropriée de VS Code pour notre système d'exploitation. Il est disponible pour `Windows`, macOS et `Linux`.

![Visual Studio Code](/images/vscode-exe.png)

> [!NOTE]
> Assurons-nous de choisir la version qui correspond à notre système.

3. Une fois le téléchargement terminé, ouvrons le fichier d'installation.

4. Suivons les instructions d'installation spécifiques à notre système d'exploitation pour terminer le processus d'installation. Sur la plupart des systèmes, il s'agit d'un processus simple de type **suivant**, **accepter les termes** et **installer**.

![Visual Studio Code](/images/vscode.gif)

5. Une fois l'installation terminée, lançons `Visual Studio Code`.

![Visual Studio Code](/images/vscode-wsl.png)

> [!NOTE]
> Nous pouvons maintenant personnaliser VS Code selon nos besoins en installant des extensions, en configurant des paramètres et en créant des projets pour commencer à travailler.

## Ajouter Extension SSH

Pour ajouter une `extension SSH` à Visual Studio Code, suivons ces étapes :

1. Lançons Visual Studio Code si ce n'est pas déjà fait. Dans la barre latérale gauche, recherchons et cliquons sur l'icône de l'onglet **Extensions** (représenté par des carrés empilés).

![Visual Studio Code](/images/extension-vscode.png)

2. Dans le champ de recherche en haut, tapez **SSH** et appuyons sur "Entrée". Cela affichera les extensions liées à SSH. Parcourons la liste des extensions SSH disponibles. Nous pouvons trouver des extensions telles que **Remote - SSH** qui nous permettent de nous connecter à des hôtes distants via SSH.

![Visual Studio Code](/images/remote-ssh.png)

3. Cliquez sur l'extension "Remote - SSH", pour accéder à sa page d'extension. Cliquons sur le bouton **Installer** à côté de l'extension. Visual Studio Code commencera à télécharger et installer l'extension.

![Visual Studio Code](/images/remote-ssh-install.png)

Une fois l'extension installée, elle sera activée automatiquement.

4. Nous pouvons maintenant utiliser l'extension SSH pour vous `connecter à des hôtes distants` depuis Visual Studio Code. Pour ce faire, Nous pouvons sur l'icône de l'extension dans la barre latérale, puis suivons les instructions pour configurer et établir des connexions SSH.

![Visual Studio Code](/images/ssh-con.png)

5. Entrons notre mot de passe et connectons-nous :

![Visual Studio Code](/images/ssh-pass.png)

## Connexion à EVEng via SSH

Après l'installation d'EVEng, le service SSH est directement disponible pour établir des connexions. Nous pouvons nous connecter à EVEng via SSH.

![Alt text](/images/ssh-eve.png)

L'extension SSH nous permettra de travailler de manière `transparente` avec des systèmes distants et de gérer des projets à distance depuis Visual Studio Code.

![Visual Studio Code](/images/eve-ssh-z.png)

## Ressources supplémentaires

- Pour plus de détails, nous pouvons consulter les liens suivants: [Visual Studio Code in Action](https://code.visualstudio.com/docs)

## Mots Techniques

#VS Code #éditeur #NetDevOps #Programmation #Extension #SSH