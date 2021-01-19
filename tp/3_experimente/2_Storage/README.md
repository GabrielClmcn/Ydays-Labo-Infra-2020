# TP n°2 - Stockage :

Ce TP a pour but de prendre en main une infrastructure de virtualisation avec un stockage mutualisé. De nos jours, beaucoup d'entreprises utilisent cette architecture, notamment pour l'hébergement des données de l'entreprise.

L'objectif est de vous présenter les différentes fonctionnalités et technologies que cette infrastructure peut proposer.

### Sommaire

[1. Choix de la technologie de stockage](#1-choix-de-la-technologie-de-stockage)  
[2. Mise en place du stockage](#2-mise-en-place-du-stockage)  
[3. Mise en fonctionnement avec l'ESXi](#3-mise-en-fonctionnement-avec-lesxi)  
[4. Rendu](#4-rendu)  

Le TP est organisé par groupe de **2 personnes** par rendu. D'autre part, il est réparti sur 2 séances. Le TP demande beaucoup de ressource une fois l'architecture montée. Dans le cas où vous n'avez pas beaucoup de ressources, il est possible de monter le TP sur 2 machines en bridge. 

> Ex : la partie stockage sur un PC et l'ESXi sur l'autre puis interconnecté le tout.

Enfin, vous pouvez ajouter de la valeur en montant des qualités supplémentaires au lab. Par exemple, si vous monitorez le tout ou que vous ajoutez des fonctionnalités de sécurité cela sera valorisé.

## 1. Choix de la technologie de stockage

Mettre en place un stockage de données en réseau qui est fonctionnel. Parmi la liste fournie ci-dessous vous devez décrire **2 au minimum techno** qui permet de faire fonctionner le **stockage en réseau**. Vous êtes libre de choisir les technologies et le mode de stockage associé, mais essayer de me présenter plusieurs choses (par exemple pas 3 fois de l'iSCSI, essayer de varier).

La liste non exhaustive des technologies de stockage, en gras les technologies assez maniables que j'ai testées. Attention, toutes les technologies ne marchent pas, à vous de faire des recherches. Bien sûr vous serez valorisé si vous utilisez une technologie peu commune :

- **FreeNAS VSA** 
- **StarWind Virtual SAN VSA (mais 30 jours d'évaluation)** 
- **OSNexux QuantaStor Community Edition VSA**  
- **Synology DSM XPEnology Simulator** 
- **Windows Server**
- Open Media Vault VSA 
- OpenFiler Unified Storage VSA 
- NetApp ONTAP Simulator 
- HPE 3PAR StoreServ Simulator
- HPE StoreVirtual VSA 
- Dell EMC UnityVSA  
- Oracle ZFS Storage Simulator 
- HPE Nimble Virtual Array VSA 
- Nutanix Community Edition  

D'autre part, une infrastructure de stockage disposant de réplication (dans le cadre d'un PCA & PRA) sera fortement valorisée.

1. Quel est le nom de cette technologie ? Expliquer pourquoi vous l'avez choisi, ainsi que les avantages et inconvénients autour de celle-ci.
2. Quel type de format et protocoles de stockages utilisés ?
3. Expliquez le plan d'adressage et les points importants qui doivent être soulignés et mis en place. Si besoin expliqué avec un schéma ou un tableau d'adressage complémentaire. 
4. Certains points seront particulièrement étudiés :
    - Possibilité de HA
    - Disques RAID
    - Interfaces HeartBeat, Witness
    - Multipathing
    - Etc,...

## 2. Mise en place du stockage

1. Mettre en place la solution. Détailler les points qui vous semblent importants.
2. Valider les avantages ou inconvénients de la solution à travers la mise en place de celle-ci
3. **[Bonus]** Ajouter de la plus-value. (Sécurité, monitoring, HA, etc...)

## 3. Mise en fonctionnement avec l'ESXi

1. Une fois le stockage en réseau effectué, connectez votre ESXi dessus et crée un Datastore. 
2. Expliquer les différentes procédures et points importants pendant la mise en service (Ajout de carte supplémentaire sur l'ESXi, fonctionnalité peu courante, etc...) 
3. Crée une VM sur le datastore.

Cela demande beaucoup de recherche, de pratique et de test. Choisissez bien votre techno et exploitez là au maximum.

## 4. Rendu

- Compte-rendu papier à rendre avant le **Dimanche 24 Janvier à 23h59**
- Présentation **orale 20 min** par groupe (10 min présentation techno et démo. 10min question), le **Mercredi 27 Janvier**

N’oubliez pas dans le compte-rendu de notifier quand le produit fonctionne, mais aussi les problèmes et erreurs que vous avez pu rencontrer lors du déroulement de votre TP. 

Barème :

- _Écrit_
  - **Choix de la technologie de stockage /8**
    - Présentation /4
    - Format & protocoles /1
    - Plan d'adressage /1
    - Fonctionnalité /2
  - **Mise en place de la technologie /5**
    - Installation + guide /4
    - Avantages/Inconvénients /1
    - Bonus valeur ajoutée +
  - **Mise en fonctionnement avec l'ESXi /4**
    - Liaison Stockage + Datastore /2
    - Installation VM + Benchmark /2
  - **Rendu /3**
    - Qualité du rendu /2
    - Orthographe /1
- _Oral_
  - **Présentation /10**
    - Qualité du support /2
    - Gestion du temps /1
    - Posture professionnelle /1
    - Accessibilité /3
    - Contenu /3
  - **Démonstration /4**
  - **Question-réponse /6**

