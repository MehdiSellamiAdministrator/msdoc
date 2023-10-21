# Les composants Cisco SD-WAN

Le `SD-WAN` (Software-Defined Wide Area Network) de Cisco est une solution complète pour optimiser et gérer les réseaux étendus. Le SD-WAN de Cisco se compose de plusieurs composants clés, notamment : 

1. `vEdge & cEdge` (Data plan), 
2. `vSmart` (Control plan), 
3. `vManage` (Management plan), 
4. `vBond` (orchestration plan).

> [!NOTE]
> `Viptela` a été fondée en 2012 par d'anciens directeurs de Cisco, `Amir Khan` et `Khalid Raza`. En 2017, 
> Cisco a acquis Viptela pour 610 millions de dollars. Viptela correspondait parfaitement aux principes de 
> sécurité, de virtualisation, d'automatisation et d'analyse inscrits dans `DNA` (Digital Network 
> Architecture).

**Objectifs**: Examinons les différents composants qui composent le SD-WAN (Cisco) (ou SD-WAN Secure Extensible Network [SEN] comme ils l'appellent également).

## vEdge and cEdge

Le dispositif en bordure (ou **edge device**) gère la `transmission` des paquets ; ils établissent le réseau virtuel sécurisé en `superposition` (overlay) :

###### **`1. Périphériques vEdge pour les bureaux à domicile (SOHO)`**

Router/Modèle | Description 
-----    | ---- 
*[vEdge 100b](https://www.cisco.com/c/en/us/td/docs/routers/sdwan/vedge/hardware/vEdge-routers-hardware-installation-guide/vEdge-routers-hardware-installation-guide_chapter_010.html)* | *Avec une connectivité `Ethernet` uniquement*.
*[vEdge 100m](https://www.cisco.com/c/en/us/td/docs/routers/sdwan/vedge/hardware/vEdge-routers-hardware-installation-guide/vEdge-routers-hardware-installation-guide_chapter_0101.html)* | *Avec une connectivité `Ethernet` et un modem `2G/3G/4G` intégré*.
*[vEdge 100wm](https://www.cisco.com/c/en/us/td/docs/routers/sdwan/vedge/hardware/vEdge-routers-hardware-installation-guide/vEdge-routers-hardware-installation-guide_chapter_0101.html)* | *Similaire au vEdge 100m, mais avec une fonctionnalité `LAN sans fil`*.

###### **`2. Périphériques vEdge pour les grandes entreprises`**

Router/Modèle | Description 
-----    | ---- 
*[vEdge 1000](https://www.cisco.com/c/en/us/td/docs/routers/sdwan/vedge/hardware/vEdge-routers-hardware-installation-guide/vEdge-routers-hardware-installation-guide_chapter_0100.html)* | *Avec 8 ports GE SFP fixes*.
*[vEdge 2000](https://www.cisco.com/c/en/us/td/docs/routers/sdwan/vedge/hardware/vEdge-routers-hardware-installation-guide/vEdge-routers-hardware-installation-guide_chapter_01000.html)* | *Avec 2 modules d'interface enfichables*.
*[vEdge 5000](https://www.cisco.com/c/en/us/td/docs/routers/sdwan/vedge/hardware/vEdge-routers-hardware-installation-guide/vEdge-routers-hardware-installation-guide_chapter_01001.html)* | *Avec 4 modules d'interface réseau*.

###### **`3. Périphériques ISR (Integrated Services Router) basé sur IOS XE`**

Router/Modèle | Description 
-----    | ---- 
*[ISR 1100 and ISR 1100X Series](https://www.cisco.com/c/en/us/products/collateral/routers/1000-series-integrated-services-routers-isr/isr-series-br-platforms-arch.html)* | *Pour les **déploiements** de `petites` et `moyennes` succursales (4G & 6G).*.
*[ISR 1000 series](https://content.cisco.com/chapter.sjs?uri=/searchable/chapter/content/en/us/td/docs/routers/access/1100/hardware/installation/guide/b-cisco-1100-series-hig/isr1k-hig-overview.html.xml#:~:text=The%20Cisco%201000%20series%20Integrated%20Services%20Routers%20are,as%20customer%20premises%20equipment%20in%20managed%20services%20environments.)* | *Pour les `petites` et `moyennes` entreprises, les `succursales d'entreprise` et les `environnements de services gérés`*.
*[ISR 4000 series](https://www.cisco.com/c/en/us/products/routers/4000-series-integrated-services-routers-isr/index.html)* | *Adaptés aux solutions de réseau de type "`Branch-Office`"*.

> [!NOTE] 
> Mon encadreur Mr. Hamza a insisté sur l'importance de choisir des dispositifs basés sur IOS XE pour leur fiabilité, leur sécurité et leur évolutivité. Cette recommandation renforce notre confiance dans ces périphériques pour notre projet.

###### **`4. Périphériques ASR (Aggregation Services Router)`**

Router/Modèle | Description 
-----    | ---- 
*[ASR 1000 series](https://www.cisco.com/c/en/us/td/docs/routers/asr1000/install/guide/1001-x/asr1hig-book/router_overview.html)* | *Routeurs de `niveau intermédiaire` adaptés aux réseaux de `taille moyenne`*.

###### **`5. Périphériques vEdge Cloud et CSR1000v pour le cloud`**

Router/Modèle | Description 
-----    | ---- 
*[vEdge Cloud](https://www.cisco.com/c/en/us/solutions/collateral/enterprise-networks/sd-wan/nb-07-cloud-router-data-sheet-cte-en.html#:~:text=Cisco%20vEdge%20Cloud%20is%20a%20software%20router%20platform,of%20private%2C%20public%2C%20and%20hybrid%20cloud%20computing%20environments.)* | *Fonctionne sur des plateformes `hyperviseur` et dans des environnements de `cloud privé, public et hybride`*.
*[CSR1000v](https://www.cisco.com/c/en/us/products/collateral/routers/cloud-services-router-1000v-series/data_sheet-c78-733443.html)* | *`Routeur virtuel` offrant des fonctions de passerelle WAN complètes pour les environnements `virtuels` et `cloud`*.

> [!NOTE]
> Le périphérique vEdge Cloud peut fonctionner dans VMWare ESXi, KVM, AWS et Azure, et c'est cette image que utiliser le plus (avec le CSR1000v).

## vSmart devices

Périphérique | Description 
-----    | ---- 
*[vSmart](https://www.cisco.com/c/en/us/td/docs/routers/sdwan/configuration/sdwan-xe-gs-book/system-overview.html)* | * Gère `le routage et la connectivité` entre les dispositifs `vEdge` après l'authentification par l'orchestrateur `vBond`*.

## vManage devices

Périphérique | Description 
-----    | ---- 
*[vManage](https://www.cisco.com/site/us/en/products/networking/wan/vmanage/index.html#tabs-ca9b217826-item-1b113ceb83-tab)* | *Système de gestion de réseau (NMS) pour configurer et gérer le réseau SD-WAN de Cisco*.

## vBond devices

Périphérique | Description 
-----    | ---- 
*[vBond](https://www.cisco.com/site/us/en/products/networking/wan/vmanage/index.html#tabs-ca9b217826-item-1b113ceb83-tab)* | *Gère l'authentification, l'autorisation et la communication entre les dispositifs vEdge et vSmart. Il facilite l'intégration du réseau, en particulier pendant le processus d'intégration*.

> [!NOTE]
> Le SD-WAN de Cisco est une solution globale qui combine ces composants pour optimiser et gérer les réseaux étendus de manière efficace et sécurisée.

## Ressources supplémentaires

- Pour plus de détails, vous pouvez consulter les liens suivants: [Cisco Catalyst SD-WAN Getting Started Guide](https://www.cisco.com/c/en/us/td/docs/routers/sdwan/configuration/sdwan-xe-gs-book/system-overview.html).

## Mots techniques

`#SDWAN (Software-Defined Wide Area Network), #vEdge, #cEdge, #vSmart, #vManage, #vBond, #Viptela, #DNA (Digital Network Architecture), #IOSXE, #ISR, #ASR, #vEdgeCloud, #CSR1000v, #hyperviseur, #cloudprivé, #cloudpublic, #cloudhybride, #routeurvirtuel, #NMS (Network Management System).`