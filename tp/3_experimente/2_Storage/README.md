# TP n°2 - Stockage :

**Objectif :** 

Mettre en place un stockage de données en réseau qui est fonctionnel. Parmi la liste fournie ci-dessous vous devez décrire **2 au minimum technos** (**3** pour les **M1**) qui permet de faire fonctionner le **stockage en réseau**. Vous êtes libre de choisir les technologies et le mode de stockage associées, mais essayé de me présenter plusieurs choses (par exemple pas 3 fois de l'iSCSI, essayer de varier).

D'autres part, si vous pouvez monter de la **Haute Disponibilité sur le stockage**, vous gagnez beaucoup de point !

Le tp est organisé par groupe de **2 personnes** par rendu. D'autre part, il est réparti sur 2 séances. Le TP demande beaucoup de ressource une fois l'architecture monté. Dans le cas où vous n'avez pas beaucoup de ressources, il est possible de monter le TP sur 2 machines en bridge. 

Ex : la partie stockage sur un PC et l'ESXi sur l'autre puis interconnecté le tout.

Enfin, vous pouvez ajouter de la valeur en montrer des qualités supplémentaires au lab. Par exemple si vous monitorez le tout ou que vous ajoutez des fonctionnalités de sécurité cela sera valorisé.

N’oubliez pas dans le compte-rendu de notifié quand le produit fonctionne mais aussi les problèmes et erreurs que vous avez pu rencontrer lors du déroulement de votre tp. 

**/!\ POUR LE RENDU /!\\** : 
- Compte-rendu papier à rendre avant le **Mardi 26 Janvier à 23h59**
- Présentation **orale 15 min** par groupe (10 min présentation techno et démo. 5min question)

Cette note fait office d'évaluation sur le semestre avec le tp P2V.

La liste non-exhaustive des technologies de stockage, en gras les technologies assez maniables que j'ai testées. Attention, toutes les technologies ne marchent pas, à vous de faire des recherches. Bien sûr vous serais valorisé si vous utilisez une technologie peu commune :

- **FreeNAS VSA** 
- **StarWind Virtual SAN VSA (mais 30 jours eval)** 
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

## 1. Choix de la technologie de stockage

1. Quel est le nom de cette technologie ? Expliquer pourquoi vous l'avez choisi, ainsi que les avantages et inconvénients autour de celle-ci.
2. Quel type de format et protocoles de stockages utilisés ?
3. Expliquez le plan d'adressage et les points importants qui doivent être souligné et mis en place. Si besoin expliquer avec un schéma ou un tableau d'adressage complémentaires. 
4. Certains points seront particulièrement étudiés :
    - Possibilité de HA
    - Disques RAID
    - Interfaces HeartBeat, Witness
    - Multipathing
    - Etc,...

## 2. Mise en place du stockage

1. Mettre en place la solution. Détailler les points qui vous semble important.
2. Valider les avantages ou inconvénient de la solution à travers la mise en place de celle-ci
3. **[Bonus]** Ajouter de la plus-value. (Sécurité, monitoring, HA, etc...)

## 3. Mise en fonctionnement avec l'ESXi

1. Une fois le stockage en réseau effectué, connecter votre ESXi dessus et crée un Datastore. 
2. Expliquer les différentes procédures et points importants pendant la mise en service (Ajout de carte supplémentaire sur l'ESXi, fonctionnalité peu courante, etc...) 
3. Crée une VM sur le datastore.

Cela demande beaucoup de recherche, de pratique et de test. Choisissez bien votre techno et exploitez là au maximum.
