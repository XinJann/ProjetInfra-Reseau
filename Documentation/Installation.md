# **Installation**
### Remarque (pour mieux comprendre les commandes lors de l'installation ):
 - L'IP globale du LAN est 192.168.0.0/16
 - le réseau est composé de 3 VLANs avec les IP suivantes :
   - VLAN 10 , 192.168.10.0/24 , gateway : 192.168.10.254
   - VLAN 20 192.168.20.0/24 , gateway : 192.168.20.254
   - VLAN 30 192.168.30.0/28 , gateway : 192.168.30.14
 - Le nom de domaine du LAN est projetinfra.net avec 2 sous-domaines :
   - web.projetinfra.net  , 192.168.30.2
   - debian-DNS.projetinfra.net , 192.168.30.1

### Installation

1) Placer les machines et les brancher comme sur l'image
   - Remarque : Pour changer les titres visible des appareils, clique droit sur l'appareil -> General settings -> Changer la valeur de "Name:" 

![Schema](/Documentation/Images/SchemaInfra.PNG)

2) Configurer les différents Switch en recopiant [les commandes](/Documentation/CommandesSwitchs.md) pour chacun d'entre eux

3) Faire glisser l'élément "NAT" (forme de nuage) de GNS3 puis le brancher au router sur l'interface f1/0

4) Configurer le router en recopiant [les commandes](/Documentation/CommandesRouter.md)

5) S'assurer que le 'Network adapter' de notre VM debian (Aller dans les Settings de la VM) est en mode "Host-Only"  

**DEBUT CONFIGURATION DE LA VM DEBIAN**

6) Suivre ce [tuto](https://www.thegeekstuff.com/2014/01/install-dns-server/) jusqu'à l'étape 3 (inclus)

7) Editer le fichier "named.conf.options" dans /etc/bind/ comme l'image :  
 ![named.conf.options](/Documentation/Images/named_conf_options.PNG)  

8) Effectuer la commande : **sudo cp /etc/bind/db.local /etc/bind/db.projetinfra.net**

9) Editer le fichier "db.projetinfra.net" dans /etc/bind/ comme l'image :  
![db.projetinfra.net](/Documentation/Images/db_projetinfra_net.PNG)

10) Effectuer la commande : **sudo cp /etc/bind/db.127 /etc/bind/db.10**

11) Editer le fichier "db.10" dans /etc/bind/ comme l'image :  
![db.10](/Documentation/Images/db_10.PNG)  

**FIN CONFIGURATION VM DEBIAN**

12) Importer la VM debian dans GNS3, documentation [ici](https://docs.gns3.com/docs/emulators/adding-vmware-vms-to-gns3-topologies/)
    - Une fois importée, clique droit -> Configure Template -> Network -> cocher la case en bas "Allow GNS3 to override non custom VMware adapter"

    - Faire glisser le template de la VM dans l'infra et la brancher au Switch Access_5 sur l'interface e0/0

    - S'il y a un message d'erreur lors de l'activation de la VM via GNS3
      - redémarrer la machine Host
      - S'il y a toujours le même problème, taper **sc config npf start= auto** dans le Terminal (Ici Powershell) de la machine Host, puis redémarrer

13) Faire glisser un VPCS dans l'infra GNS3, et la brancher au Switch Access_5 sur l'interface 0/1, allumer la machine pour accéder à la Console et taper les commandes suivantes :  
    - ip 192.168.30.2 255.255.255.0 192.168.30.14
    - ip dns 192.168.30.1
    - set pcname web
    - wr

[Suivant](/Documentation/Utilisation.md)  
[Retour](/README.md)
