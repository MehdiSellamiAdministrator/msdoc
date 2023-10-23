# Modèles hiérarchiques

La conception hiérarchique des réseaux est un cadre structurel qui divise un réseau en plusieurs couches distinctes, chacune ayant un ensemble spécifique de fonctions. Cette approche simplifie la conception, la gestion et la croissance des réseaux. 

En termes simples, elle consiste à répartir les tâches réseau entre différentes couches de manière organisée, plutôt que de tenter de tout gérer au sein d'une seule plateforme ou d'un seul appareil complexe.

> [!NOTE] 
> Ces modèles sont applicables à la fois aux réseaux LAN et aux réseaux WAN.

## Avantages du modèle hiérarchique

Les avantages de la conception hiérarchique incluent des économies de coûts, une facilité de compréhension, une croissance modulaire du réseau et une meilleure isolation des pannes.  

Éléments | Détails
-----            | ----                   
*`Économies de coûts`* | *Les économies de coûts proviennent de la répartition des fonctions réseau sur des appareils spécialisés, ce qui évite d'investir dans un seul appareil coûteux et complexe. Cela réduit les coûts et optimise l'utilisation de la bande passante.* 
*`Facilité de compréhension`* | *La facilité de compréhension résulte de la simplification de chaque couche, ce qui réduit les coûts de formation et de gestion du personnel.*
*`Croissance modulaire`* | *La conception modulaire permet une croissance facile du réseau en ajoutant simplement de nouvelles couches ou en répliquant les éléments de conception existants.* 
*`Amélioration de l'isolation des pannes`* | *Enfin, l'isolation des pannes est améliorée car chaque couche est facilement identifiable, facilitant la localisation des problèmes en cas de panne.* 

> [!NOTE] 
> Elle est également essentielle pour l'efficacité des protocoles de routage dynamiques tels qu'OSPF et EIGRP : Ils peuvent résumer les routes (route summarization), c'est-à-dire combiner plusieurs routes similaires en une seule, ce qui économise de la bande passante et simplifie le traitement de l'information de routage.

## Conception de Réseau Hiérarchique

Couche | Fonction
-----            | ----                   
*`Noyau (Core)`* | *Transport rapide (fast transport) entre les switches de distribution (To Enterprise Edge Modules).* 
*`Distribution`* | *Connectivité basée sur des politiques.*
*`Accès`* | *Accès des groupes de travail (workgroup) et des utilisateurs au réseau - Endpoint.*

## Les fonctions des couches hiérarchiques.

Le modèle hiérarchique consiste en trois couches principales : le Noyau (Core), la distribution et l'accès. Chacune de ces couches a des fonctions et des rôles spécifiques dans le réseau d'entreprise.

### Caractéristiques de la Couche "Backbone"

La couche Core est un élément critique d'un réseau et sert de backbone à haute vitesse pour les communications d'entreprise. Ses principales caractéristiques et considérations comprennent :

Caractéristique | Description
-----            | ----                   
*`Transport Rapide`* | *Offre un transport de données à haute vitesse pour router efficacement les données entre différentes parties du réseau.* 
*`Haute Fiabilité`* | *Elle doit être hautement fiable pour garantir des performances réseau constantes.*
*`Redondance`* | *Fournit des chemins de secours pour éviter les interruptions de service en cas de défaillance.*
*`Tolérance aux Pannes`* | *Conçue pour résister aux pannes du réseau sans perturbations majeures des services.* 
*`Faible Latence et Facilité de Gestion`* | *Offre une faible latence pour une transmission rapide des données et est facilement gérable.*
*`Éviter Manipulations Intensives par le CPU`* | *Se concentre sur les fonctions de routage et de commutation, évitant les tâches intensives pour le CPU.*
*`Diamètre Limité et Cohérent`* | *Maintient un nombre cohérent de sauts de routeurs pour une performance équilibrée.*
*`QoS (Qualité de Service)`* | *Met en place des fonctionnalités de qualité de service pour prioriser le trafic critique.*

Ces caractéristiques sont essentielles pour garantir le bon fonctionnement de cette couche.