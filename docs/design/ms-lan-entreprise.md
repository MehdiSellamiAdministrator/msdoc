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

## Les fonctions des couches hiérarchiques

La couche Core est cruciale pour les communications d'entreprise :

##### `Caractéristiques de la Couche "Backbone"`

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