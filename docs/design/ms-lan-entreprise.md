# Modèles hiérarchiques

La conception hiérarchique des réseaux divise le réseau en différentes couches avec des fonctions spécifiques pour simplifier la conception, la gestion, et la croissance. Au lieu de tout gérer sur une seule plateforme, cette approche répartit les tâches de manière organisée.

> [!NOTE] 
> Ces modèles sont applicables à la fois aux réseaux LAN et aux réseaux WAN.

## Avantages du modèle hiérarchique

Éléments | Détails
-----            | ----                   
*`Économies de coûts`* | *Évite d'investir dans un seul appareil coûteux et complexe, réduisant les coûts et optimisant la bande passante.* 
*`Facilité de compréhension`* | *Simplifie chaque couche, réduisant les coûts de formation et de gestion.*
*`Croissance modulaire`* | *Facilite l'ajout de nouvelles couches ou la réplication des éléments existants.* 
*`Amélioration de l'isolation des pannes`* | *Facilite la localisation des problèmes en cas de panne.* 

> [!NOTE] 
> Cette conception est essentielle pour les protocoles de routage dynamiques tels qu'OSPF et EIGRP, qui peuvent résumer les routes (combiner plusieurs routes similaires en une seule), économisant ainsi de la bande passante.

## Conception de Réseau Hiérarchique

Couche | Fonction
-----            | ----                   
*`Noyau (Core)`* | *Transport rapide entre les switches de distribution (To Enterprise Edge Modules).* 
*`Distribution`* | *Connectivité basée sur des politiques.*
*`Accès`* | *Accès des groupes de travail (workgroup) et des utilisateurs au réseau (Endpoint).*

## Fonctions des couches hiérarchiques

Les fonctions des couches hiérarchiques dans la conception de réseaux sont essentielles pour organiser, gérer et optimiser les performances des réseaux informatiques. 

## `Caractéristiques: "Backbone"`

Caractéristique | Description
-----            | ----                   
*`Transport Rapide`* | *Achemine efficacement les données à haute vitesse.* 
*`Haute Fiabilité`* | *Garantit des performances réseau constantes.*
*`Redondance`* | *Fournit des chemins de secours en cas de défaillance.*
*`Tolérance aux Pannes`* | *Résiste aux pannes sans perturbations majeures des services.* 
*`Faible Latence et Facilité de Gestion`* | *Offre une transmission rapide et une gestion aisée.*
*`Éviter Manipulations Intensives par le CPU`* | *Concentre sur les fonctions de routage et de commutation.*
*`Diamètre Limité et Cohérent`* | *Maintient un nombre cohérent de sauts pour des performances équilibrées.*
*`QoS (Qualité de Service)`* | *Priorise le trafic critique.*

> [!NOTE]
> `Bonne pratique` : Maintenir un diamètre constant (nombre de sauts : From edge to edge, endpoint to endpoint ou endpoint to Serve à travers Core) est essentiel pour garantir la stabilité, des performances prévisibles, la facilité de gestion, et l'évolutivité tout en offrant une connectivité ininterrompue aux utilisateurs de l'entreprise.

> [!WARNING]
> Une grande entreprise adopte un réseau hiérarchique avec une couche core, distribution, et accès. Lors de la croissance, elle étend le modèle en ajoutant des sous-réseaux locaux intermédiaires à la couche de distribution, tout en maintenant le nombre de sauts constant vers la couche core. Cette expansion permet une connectivité stable et efficace sans perturber la couche core, simplifiant la gestion du réseau.

## `Caractéristiques: "Distribution"`

La couche de distribution d'un réseau constitue un point d'isolation entre les couches d'accès et de core. Cette couche a divers rôles et fonctions, dont notamment :

Rôles et Fonctions | Explications
-----            | ----                   
*`Connectivité basée sur des politiques`* | *Par exemple, l'acheminement du trafic d'un réseau particulier par une interface spécifique tandis que tout autre trafic passe par une autre interface.* 
*`Redondance et load balancing`* | *Elle assure la redondance pour garantir la disponibilité du réseau en cas de défaillance. De plus, elle équilibre la charge entre les différents composants du réseau pour une meilleure utilisation des ressources.*
*`Agrégation des armoires de câblage des réseaux locaux (LAN)`* | *agrège les connexions de plusieurs armoires de câblage locales, ce qui simplifie la gestion du réseau en centralisant les connexions.*
*`Agrégation des connexions de réseaux étendus (WAN)`* | *Elle agrège les connexions provenant de différents réseaux étendus, ce qui peut réduire le nombre de connexions WAN nécessaires et améliorer l'efficacité de la communication entre les sites distants.*
*`Qualité de service (QoS)`* | *Elle gère la qualité de service en attribuant des priorités et en appliquant des politiques de qualité de service pour assurer que les types de trafic critiques bénéficient de performances optimales.* 
*`Filtrage de sécurité`* | *La couche de distribution filtre le trafic pour des raisons de sécurité, en s'assurant que seuls les flux de données autorisés sont autorisés à traverser.*
*`Agrégation ou résumé (summarization) d'adresses ou de zones`* | *Elle agrège ou résume des plages d'adresses IP ou des zones pour réduire la complexité du routage et économiser de la bande passante.*
*`Accès aux départements ou groupes de travail`* | *Elle gère l'accès aux différents départements ou groupes de travail au sein de l'entreprise, contrôlant qui peut accéder à quelles ressources.*
*`Définition de domaines de diffusion ou de multidiffusion`* | *Elle définit les limites des domaines de diffusion ou de multidiffusion pour contrôler la portée des diffusions de données.*
*`Routage entre les réseaux locaux virtuels (VLAN)`* | *La couche de distribution permet le routage entre différents réseaux locaux virtuels (VLAN), ce qui isole le trafic entre les différents groupes d'utilisateurs.*
*`Traductions de média`* | *Elle peut effectuer des traductions de média pour permettre la communication entre différents types de médias, tels qu'Ethernet et Token Ring.*
*`Redistribution entre des domaines de routage`* | *Elle permet la redistribution du trafic entre différents domaines de routage, par exemple, entre deux protocoles de routage distincts.* 
*`Distinguer les protocoles de routage statiques et dynamiques`* | *Elle peut servir de point de démarcation entre des protocoles de routage statiques (configurés manuellement) et dynamiques (configurés automatiquement).*

Nous pouvons utiliser plusieurs fonctionnalités du `logiciel Cisco IOS` pour mettre en oeuvre une stratégie au niveau de la couche de distribution :

Rôles et Fonctions | Explications
-----            | ----                   
*`Filtrage par adresse source ou de destination`* | *Contrôle du trafic en fonction des adresses source ou de destination.* 
*`Filtrage sur les ports d'entrée ou de sortie`* | *Filtrage du trafic en fonction des ports d'entrée ou de sortie des dispositifs.*
*`Masquage des numéros de réseau internes`* | *Dissimulation des numéros de réseau internes grâce au filtrage des routes.*
*`Filtrage par adresse source ou de destination`* | *Contrôle du trafic en fonction des adresses source ou de destination.* 
*`Routage statique`* | *Configuration manuelle des entrées de routage pour des besoins spécifiques*
*`Mécanismes de qualité de service`* | *Priorisation et gestion du trafic pour un traitement préférentiel des données critiques.*

> [!NOTE]
> La couche de distribution joue également un rôle essentiel dans l'agrégation des routes en résumant les routes avant de les transmettre à la couche core. 

La couche de distribution joue un rôle central dans la gestion, le routage, la sécurité et la performance du réseau en assurant une transition fluide du trafic entre la couche d'accès et la couche core. Elle offre également une flexibilité pour l'application de politiques et la gestion des ressources réseau.

## `Caractéristiques : "Access"`

Fonctionnalité | Description
-----            | ----                   
*`Commutation (Switching) de couche 2`* | *Fournit une connectivité de couche 2 aux utilisateurs, permettant la communication au sein des segments locaux.* 
*`Haute disponibilité`* | *Assure la disponibilité continue des services en cas de panne de dispositifs.*
*`Sécurité des ports`* | *Protège les ports d'accès contre un accès non autorisé en limitant les adresses MAC autorisées.*
*`Suppression de diffusion`* | *Réduit la diffusion excessive du trafic, ce qui améliore les performances du réseau.* 
*`Classification et marquage QoS et frontières de confiance`* | *Étiquette le trafic pour une gestion de la qualité de service (QoS) et établit des frontières de confiance entre les appareils.*
*`Limitation/régulation de débit`* | *Restreint ou régule la quantité de trafic autorisée sur un port.*
*`Inspection du protocole de résolution d'adresse (ARP)`* | *Protège contre les attaques ARP en surveillant le trafic ARP.*
*`Listes de contrôle d'accès virtuel (VACL)`* | *Permet de contrôler et de filtrer le trafic sur la couche d'accès.*
*`Spanning tree`* | *Prévient les boucles dans le réseau en gérant les liaisons redondantes.* 
*`Classification de confiance`* | *Identifie les ports d'accès de confiance qui ont des exigences de sécurité particulières.*
*`Alimentation par Ethernet (PoE) et VLAN auxiliaires pour la VoIP`* | *Fournit de l'alimentation aux périphériques VoIP et utilise des VLAN auxiliaires pour leur connectivité.*
*`Contrôle d'accès au réseau (NAC)`* | *Gère l'accès au réseau en vérifiant la conformité des dispositifs et en les autorisant en conséquence.*
*`VLAN auxiliaires`* | *Utilisés pour des fonctions spécifiques, tels que la connectivité des dispositifs de gestion réseau.*

## Ressources supplémentaires

- Pour plus de détails, vous pouvez consulter le lien suivant sur *Cisco Press* : [CCNP and CCIE Enterprise Core ENCOR 350-401 Official Cert Guide, 2nd Edition (Cisco Press, 2023)](https://www.ciscopress.com/store/ccnp-and-ccie-enterprise-core-encor-350-401-official-9780138216764)

## Mots Techniques

`Conception Hiérarchique des Réseaux, Réseaux LAN, Réseaux WAN, Noyau (Core), Distribution, Accès , Fiabilité, Redondance, load balancing, Bande Passante, Latence, Qualité de Service (QoS), Routage, Filtrage, Summarization, Switching, VLAN (Virtual Local Area Network), Boucle (Loop), Alimentation par Ethernet (PoE), Contrôle d'Accès au Réseau (NAC), Liste de Contrôle d'Accès (ACL)`