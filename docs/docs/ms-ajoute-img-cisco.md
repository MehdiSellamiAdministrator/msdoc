# Ajouter Cisco Images (EVEng)

Une fois les fichiers téléchargés, nous allons ajouter les images Cisco `SD-WAN` et d'autres images sur EVE-NG en utilisant `SSH (Secure Shell)` et `SCP (Secure Copy Protocol)` pour transférer les fichiers vers notre instance EVE-NG.

![Alt text](./images/images-cisco-backup.png)

## Créer les fichiers

- Nous allons d’abord nous connecter à `EVE-NG via SSH`, puis créer des fichiers dans EVE-NG. 

![Alt text](./images/add-img-cisco-eve.png)

- Voici les `commandes` de création de dossiers dont nous aurons besoin, comme indiqué :

```bash
cd /opt/unetlab/addons/qemu
mkdir vtedge-20.4.1 vtbond-20.4.1 vtsmart-20.4.1 vtmgmt-20.4.1 csr1000vng-universalk9.17.03.01a-serial viosl2-adventerprisek9-m.ssa.high_iron_20200929 asav-9.17-1-7
```
![Alt text](./../images/dir-eve.png)

- Ensuite, à l'aide de la commande `scp` (Linux ou Windows), nous copions les fichiers (qcow) comme dans le tableau :

Dossier sur EVENG | Image Cisco
-----    | ----      
*vtedge-20.4.1* | *viptela-`edge`-20.4.1-genericx86-64.qcow2*.
*vtsmart-20.4.1* | *viptela-smart-20.4.1-genericx86-64.qcow2*.
*vtmgmt-20.4.1* | *viptela-vmanage-20.4.1-genericx86-64.qcow2*.
*vtbond-20.4.1* | *viptela-`edge`-20.4.1-genericx86-64.qcow2*.
*csr1000vng-ucmk9.16.12.2r-sdwan* | *csr1000v-ucmk9.16.12.2r.qcow2*.
*csr1000vng-universalk9.17.03.01a-serial* | *csr1000vng-universalk9.17.03.01a-serial.qcow2*.
*vios-adventerprisek9-m.SPA.159-3.M4* | *vios-adventerprisek9-m.spa.159-3.m4.qcow2*
*viosl2-adventerprisek9-m.ssa.high_iron_20200929* | *vios_l2-adventerprisek9-m.ssa.high_iron_20200929.qcow2*.
*asav-9.17-1-7* | *asav-9.17-1-7.qcow2*.

## Ajout d'Images sur EVE-NG

Pour ajouter les images, utilisez un `terminal` sous Linux ou Windows et tapez les commandes suivantes en remplaçant tous les noms par "virtioa" :

```bash
# Pour ASAV
scp -r asav-9.17-1-7.qcow2 root@192.168.100.128:/opt/unetlab/addons/qemu/asav-9.17-1-7/virtioa.qcow2
# Router Node
scp -r vios-adventerprisek9-m.spa.159-3.m4.qcow2 root@192.168.100.128:/opt/unetlab/addons/qemu/vios-adventerprisek9-m.SPA.159-3.M4/virtioa.qcow2
# Switch Node
scp -r vios_l2-adventerprisek9-m.ssa.high_iron_20200929.qcow2 root@192.168.100.128:/opt/unetlab/addons/qemu/viosl2-adventerprisek9-m.ssa.high_iron_20200929/virtioa.qcow2
# CSR1000
scp -r csr1000vng-universalk9.17.03.01a-serial.qcow2 root@192.168.100.128:/opt/unetlab/addons/qemu/csr1000vng-universalk9.17.03.01a-serial/virtioa.qcow2
# vEdge (viptela)
scp -r viptela-edge-20.4.1-genericx86-64.qcow2 root@192.168.100.128:/opt/unetlab/addons/qemu/vtedge-20.4.1/virtioa.qcow2
# vSmart (viptela)
scp -r viptela-smart-20.4.1-genericx86-64.qcow2 root@192.168.100.128:/opt/unetlab/addons/qemu/vtsmart-20.4.1/virtioa.qcow2
# Vbond
scp -r viptela-edge-20.4.1-genericx86-64.qcow2 root@192.168.100.128:/opt/unetlab/addons/qemu/vtbond-20.4.1/virtioa.qcow2
# Vmanager
scp -r viptela-vmanage-20.4.1-genericx86-64.qcow2 root@192.168.100.128:/opt/unetlab/addons/qemu/vtmgmt-20.4.1/virtioa.qcow2
```

> [!NOTE]
> `vBond` et `vEdge` partagent la même image (viptela-`edge`-20.4.1-genericx86-64.qcow2).

![Alt text](images/add-img.png)

- Maintenant, en utilisant `SSH` à distance sur l'instance `EVE-NG`, créons un `deuxième stockage` supplémentaire de disque dur de `100 Go` appelé "**virtiob.qcow2**" et corrigeons `les autorisations` :

```bash
/opt/qemu/bin/qemu-img create -f qcow2 virtiob.qcow2 100G
/opt/unetlab/wrappers/unl_wrapper -a fixpermissions
```

C'est fait ! Nous avons ajouté et préparé les images Cisco sur notre EVE-NG.

![Alt text](images/dash-eve.png)

## Ressources supplémentaires

- Pour plus de détails, nous pouvons consulter les liens suivants: [How to create images](https://www.eve-ng.net/index.php/documentation/howtos/)

## Mots Techniques

`#Cisco #qcow #SDWAN #Switch #Router #vtedge #vtsmart #vtmgmt #vtbond #csr1000v #ASAV #virtioa #EVE-NG #SSH #SCP #SecureShell #SecureCopyProtocol #viptela #vmanage #virtiob #disque #stockage #permissions #instance #EVE-NG #transfert #fichiers #terminal #Linux #Windows #création #dossiers #qemu-img`