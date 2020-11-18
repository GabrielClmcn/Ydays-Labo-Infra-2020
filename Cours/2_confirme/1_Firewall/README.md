# Les Firewalls
**Définition :** un logiciel ou un matériel dont la principale fonction est d'assurer la sécurité d'un réseau.

L'année dernière vous aviez vu la partie firewall logiciel avec la manipulation de Firewalld sur des machines CentOS. Cette année nous allons plutôt voir l'aspect d'une architecture avec un firewall en coeurs de réseau.

Quel utilité par rapport au firewall traditionnel ?

- Performance égales en routages (tout en analysant)
- Prix en baisse
- Analyse des flux Est-Ouest
- Vue sur l'état du réseau
- Accès distants

Images

## 1. Définitions
**`UTM`** : **U**nified **T**hreat **M**anagement

**`NGFW`** : **N**ext **G**eneration **F**ire**W**all

**`USG`** : **U**nified **S**ecurity **G**ateway

> Ces 3 termes désignent la même chose : Un firewall "amélioré". En outre, le fait d'être un pare-feu traditionnel, on cite généralement ces fonctionnalité associés, le filtrage anti-spam, un logiciel antivirus, un système de détection ou de prévention d'intrusion (IDS ou IPS), et un filtrage de contenu applicatif (filtrage URL).

**`NAT`** : **N**etwork **T**ranslation **A**ddress, permet a des adresses privées de communiquer avec extérieur en utilisant des adresses IP Public. L'avantage est de limiter l'utilisation des adresse IP public. D'autre part cela permet de masquer le réseau Local au reste du monde
- Il existe 3 configurations possibles :
	- NAT 1 pour 1
	- NAT Overload
	- NAT Pool

**`SNAT`** : **S**ource **NAT**, change l'adresse IP source des paquets de la communication

**`DNAT`** : **D**estination **NAT**, change l'adresse IP destination des paquets de la communication

**`PAT`** : **P**ort **A**ddress **T**ranslation, permet d'associer de façon statique/fixe (et non pas dynamique comme dans le NAT de base) un port TCP ou UDP sur l'interface du routeur côté Internet à un hôte interne à partir du couple d'informations : adresse IP et port TCP/UDP.

**`VPN`** : **V**irtual **P**rivate **N**etwork
- **`VPN SSL`** : Préféré pour les connexions Client à Site. Utilise SSL. Peut s'utiliser en Clientless
- **`VPN IPSEC`** : Préféré pour les connexions Sites à Sites. Utilise IKE. Nécessite des clients particuliers

## 2. Les Fonctionnalités
- Firewall (ACLs  / IPTable) : autorise/refuse les flux entrants et sortants
- Routeur (DHCP, DNS server, NAT, NTP server…) : peut faire du routage inter-vlan et fournir les principaux services qu'a besoin une infrastructure
- VPN Site à Site // Site à Utilisateur : permettre le VPN SSL ou IPSEC
- Filtre URL / IPS / Antispam / Antivirus / Application Control / : Filtrage des flux en analysant la couches 5 à 7 du modèle OSI
- SD-WAN : 
- Borne / Contrôleur de Borne WiFi

## 3. Les marques
- **Fortinet**
- **Checkpoint**
- **Palo Alto**

![Les différentes marques de Firewall sur le marché](https://github.com/GabrielClmcn/Ydays-Labo-Infra-2020/blob/master/Cours/2_confirme/1_Firewall/image/gartner-firewall.png)

## 4. Les types
> Rappel définition : une appliance est un appareil informatique généralement discret, spécifiquement conçu pour exécuter un logiciel destiné à fournir une ressource informatique distincte.

Les firewall peut etre utilisé sous différentes formes :
- Appliance : un boitier que vous acheter chez l'éditeur et qui souvent prêt à l'emploi. Vous avez juste a branchez et faire de la configuration. Cependant, vous restez limité au niveau hardware.
- Machine virtuelle :  une machine virtuelle que l'éditeur vous vends et installé dans votre infrastructure virtuelle. L'avantage est que vous pouvez modifié les spécificité de la machine a tous moment (ex : plus de RAM, plus de CPU, etc...). Le désavantage est perdez de la performance au niveau des prot hardware.
- Open Server : l'éditeur vous donne la solution à installé sur une machine physique. Vous contrôler donc la partie hardware tout en ayant l'avantage des performances physiques des ports.

