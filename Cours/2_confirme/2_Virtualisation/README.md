# La virtualisation
- [I. Qu'est ce que la virtualisation ?](#i-quest-ce-que-la-virtualisation-)
- [II. Pourquoi virtualiser ?](#ii-pourquoi-virtualiser-)
  - [Est-il possible de tous virtualiser ?](#est-il-possible-de-tout-virtualiser-)
- [III. Comment ça fonctionne ?](#iii-comment-ça-fonctionne-)
- [IV. Les types de virtualisation](#iv-les-types-de-virtualisation)
  - [La virtualisation de serveur](#la-virtualisation-de-serveur)
  - [La virtualisation de poste de travail](#la-virtualisation-de-poste-de-travail)
  - [La virtualisation logicielle](#la-virtualisation-logicielle)
  - [La virtualisation du réseau](#la-virtualisation-du-réseau)
  - [La virtualisation des données](#la-virtualisation-des-données)
  - [Les hyperviseurs](#les-hyperviseurs)


# I. Qu'est ce que la virtualisation ?
**Virtualisation :** faire fonctionner, sur une même machine physique, plusieurs systèmes comme s'ils fonctionnaient sur des machines physiques distinctes. La virtualisation est donc **une abstraction des ressources informatiques physiques**.

> Attention à ne pas confondre avec **simulation** et **émulation**. 

> La **simulation** se réfère à la reproduction "complète" d'un système. "Complète" car non seulement les fonctions sont imitées en interaction avec d’autres systèmes, mais tous les composants du système et leur logique interne sont également simulés. Les simulateurs sont utilisés pour compiler des programmes qui ont été développés pour un certain système à des fins d’analyse sur un autre système.

> Alors que la simulation vise à répliquer les systèmes, l’**émulation** fournit les fonctions des composants matériels ou logiciels, et non leur logique interne. Le but de l’émulation est d’obtenir les mêmes résultats avec le système simulé qu’avec son pendant réel.

Les composants matériels et logiciels peuvent être **abstraits**. Un composant informatique créé dans le cadre de la virtualisation est appelé _composant virtuel_ ou _logique_ et peut être utilisé de la même manière que son équivalent physique.

# II. Pourquoi virtualiser ?

Objectifs de la virtualisation :
- Réduire les coûts
- Réduire le nombre d'équipement matériels
- Réduire les délais de mise à disposition des nouveaux serveurs
- Simplifier l'administration de la gestion
- Améliorer le niveau de service et la disponibilité des applications
- Créer des environnement de tests et de préproduction
- S'adapter aux changement des applications et évolutions du business
- Simplifier la migration des applications sur de nouveau serveurs
- Mettre en place un PRA
- Moderniser le Système d'Information de l'entreprise
- Initiative et démarche Green IT 

**L'économie sur le matériel** : Une machine physique gère une dizaine de machines virtuelles. Grâce à cela, l'entreprise réduit le nombre de serveurs, de matériels informatiques, sa **consommation électrique** ainsi que la **maintenance** du parc informatique. **Réduction** du **besoin de climatisation**. Prend moins de place si location d’une salle.

**Meilleur gestion** : En effet, le **Provisioning Instantané** permet de mettre rapidement un nouveau serveur en service et se fait en quelques clics et quelque minutes. Plus besoin, d’installer au préalable le matériels ainsi que les tâches sous jacente lors d’un déploiement d’un serveur physique. D’autre part, la virtualisation permet une **gestion centralisé** de toutes les machines.

**Meilleur qualité et niveau de services** : Contrairement aux machines physiques, il est plus facile de mettre en place de la **redondance** et donc de la **disponibilité** sur les machines virtuelles. Grâce notamment au **clustering** que proposé les **hyperviseur**. D’autre part, la virtualisation permet d’optimiser la **répartition de la charge de travail** entre les différents serveurs.

**Environnement de test et préproduction** : cela contribue aussi à l’amélioration du niveau de service. Ces environnements sont souvent utilisé afin de **tester** et **jouer** les mises à jours ou autres changements avant de mettre en production.

---

## Est-il possible de tout virtualiser ?

Techniquement, il est aujourd’hui possible de virtualiser la très grande majorité des serveurs en sachant que VMware peut apporter de l’aide dans les cas de serveurs à priori plus difficiles à virtualiser.

Les **meilleurs candidats** (serveur) à virtualiser, c’est-à-dire ceux que l’on va privilégier :

- En priorité ceux utilisés pour des **tests** ou du **développement**. Ce sont des serveurs **non critiques** qui ne mettent pas en péril le Système d’Information.

- Les serveur qui sont proches de la **fin de garanties** doivent être virtualisés afin de ne pas a avoir à investir dans des extensions de garantie.

- Les serveurs d’**impressions** ou de **fichiers** dont le passage en virtuel est simple.

- Les serveurs **collaboratifs** tel que intranet, serveur web, etc…

- Les serveurs critiques d’infrastructure tel que l’AD, le DHCP et le DNS

- Les serveurs qui tourne sur des vieux OS, puisque leur passage en virtuel sont plus aléatoire. Ils nécessitent une attention particulière lors de leur migration.

- Enfin, les serveurs stratégiques pour l’entreprise : **base de données**, ERP (Entreprise Ressource Planning ou PGI Progiciel de Gestion Intégré, exemple : gestion de temps de travail), CRM, SAP, **application métiers**…

Les **moins bons** pour être virtualiser :

- Les serveurs ayant des **périphériques spéciaux** non validés dans la liste de compatibilité des serveurs avec : **cartes fax**, d’acquisitions numérique ou de montages vidéo, cartes sons, modem, port parallèles ou Dongle. Il est cependant possible de demander un développement spécial de drivers à VMware si cela est nécessaires. Ou passer par la communauté.

### Les résultats attendus

**Pour l’entreprise dans son ensemble** : c’est un investissement pour le futur. L’objectif pour une entreprise est de **rester compétitive** face à la concurrence et de pouvoir **adapter son Système d’Information** rapidement en cas de rachat, de fusion/acquisition ou de création de nouvelles entités. Cela peut entrer dans une **démarche Green IT**.

**Pour les financiers et dirigeants de l’entreprise** : un objectif réaliste de **réduction de 20% à 40%** des coûts lié à l’infrastructure peut être envisagé, éventuellement plus dans certaines cas.

**Pour les administrateurs et responsable IT** : l’objectif est de **faciliter** leur tâches quotidiennes, **améliorer** les niveaux de service, mettre en place un **PRA** et de leur libérer du temps pour **moderniser** le Système d’Information de l’optimisation de l’infrastructure.

**Pour les utilisateurs** : l’objectif est qu’ils aient de **meilleurs niveaux de services** et qu’ils puissent avoir à disposition de nouveaux serveurs en fonction de leurs besoin.

# III. Comment ça fonctionne ?

Pour rappel, un serveur physique est décomposé en 3 couches :
- Hardware
- OS
- Application

La virtualisation consiste alors a utiliser le hardware et donc les ressources de la machine pour faire tourner plusieurs systèmes comme si chaque systèmes tournait sur une machine séparée avec ses propres ressources matérielles.

Avec la virtualisation sur cette même machine, on aura donc plusieurs OS sur les quels tournent des applications. Il s'agit d'un exemple de virtualisation mais il en existe d'autres.

Screenshot

# IV. Les types de virtualisation

Il existe plusieurs types de virtualisation :
- La virtualisation de serveur
- La virtualisation de poste de travail
- La virtualisation logicielle
- La virtualisation du réseau
- La virtualisation des données

## La virtualisation de serveur

La virtualisation des serveurs permet à plusieurs systèmes d'exploitation de s'exécuter sur un seul serveur d'hébergement.

|Avantages|Inconvénients|
|-----------|---------|
|Les ressources matérielles peuvent être allouées dynamiquement et utilisées plus efficacement|Les performances d’une machine virtuelle peuvent être affectées par d’autres machines virtuelles sur le même système hôte.|
|peut être plus économe en énergie que des ordinateurs séparés|La réplication d’un environnement matériel avec le système d’exploitation augmente l’overhead.|

>**Overhead** : Temps d’attente pour les VM afin d'être planifiées sur un processeur.

Dans la virtualisation de serveur, les ressources du serveur physique sont abstraites de manière logique pour créer et exécuter des machines virtuelles. (ESXi, KVM, Hyper-V).

## La virtualisation de poste de travail

La virtualisation des postes de travail est un concept dans lequel **les environnements de bureau sont fournis de manière centralisée** et accessibles via un réseau. Ainsi cela permet de simplifier l’informatique des l'utilisateurs finals.

|Avantages|Inconvénients|
|-----------|---------|
|La virtualisation des postes de travail permet l’administration centralisée des environnements de bureau.|La virtualisation des postes de travail est principalement adaptée aux infrastructures homogènes.|
|Les utilisateurs peuvent accéder à leur bureau virtuel à partir d’une multitude de périphériques.|Certaines approches nécessitent une connexion constante au réseau.|
|La virtualisation des postes de travail permet des sauvegardes centralisées.|Nécessite des exigences élevées en matière de performances des serveurs, de capacité de stockage et de bande passante réseau.|
|Les clients légers permettent de réduire les coûts d’acquisition et d’exploitation.||

Il existe 2 types de virtualisation de poste de travail :
- Le **V**irtual **D**esktop **I**nfrastructure
- Le **Streaming d'OS** : 

---

Dans le cas du **VDI**, le poste de travail est hébergé dans un datacenter. L'utilisateur utilise alors son poste par accès distant et déport l'affichage comme s'il était présent localement sur son poste.

L'environnement de travail est alors directement associé au profil utilisateurs et l'utilisateur à la même vue sur son environnement quel que soit le terminal utilisé.

C'est la forme la plus courante de virtualisation de poste de travail.

Exemple de produit sur le marché : VMware Horizon, XenDesktop, etc…

---

Dans le cas du **Streaming d'OS**, le système démarre à partir d'un disque installé sur le réseau et charge de façon sélective les contenus et les applications demandés par l'utilisateur depuis un serveur distant.

Exemple de produit sur le marché : VMware ThinApp, Citrix Provisionning Server, HP Neoware Image Manager

## La virtualisation logicielle

La virtualisation des applications est l’abstraction d’applications individuelles du système d’exploitation sous-jacent.

Les systèmes de virtualisation d’applications tels que VMware ThinApp, Microsoft App-V ou Citrix XenApp permettent aux programmes de s’exécuter dans des environnements d’exécution isolés et de se répartir sur plusieurs systèmes sans avoir à modifier les systèmes d’exploitation locaux, les systèmes de fichiers ou le registre.

VMware ThinApp permet par exemple de convertir les fichiers du package Windows Installer (tels que les fichiers MSI) de programmes complexes en fichiers EXE autonomes. Ceux-ci contiennent toutes les bibliothèques et tous les fichiers de configuration nécessaires à l’exécution de l’application dans n’importe quel environnement du système d’exploitation Windows.

|Avantages|Inconvénients|
|-----------|---------|
|Les logiciels d’application peuvent être déployés, gérés et maintenus de manière centralisée.|-Les applications qui sont intégrées étroitement au système d’exploitation ou qui nécessitent l’accès à des pilotes périphériques spécifiques ne peuvent pas être virtualisées.|
|En isolant l’application, le système sous-jacent est protégé des codes malveillants.|La virtualisation des applications soulève des questions de licence.|
|Le logiciel peut être retiré du système sans restes.||

## La virtualisation du réseau

La virtualisation du réseau implique diverses approches qui abstraient les ressources réseau aux niveaux matériel et logiciel à partir de leur fondement physique. En règle générale, ce type de virtualisation est utilisé dans le cadre de concepts de sécurité.

Deux objectifs sont au premier plan :
- Les ressources physiques du réseau doivent être combinées en une unité logique grâce à la virtualisation.

- Les ressources physiques du réseau doivent être divisées en différentes unités virtuelles grâce à la virtualisation.

Un **VPN** est un réseau virtuel basé sur un réseau physique. Dans la pratique, les VPN sont utilisés pour établir des connexions sécurisées via des lignes non sécurisées - par exemple, si un employé en déplacement souhaite accéder au réseau privé de son entreprise via Internet.

En tant que réseau public, Internet ne peut assurer une connexion sécurisée entre deux ordinateurs. Pour assurer la confidentialité des données lors de leur transmission, il est donc conseillé d’utiliser la virtualisation. Différents éditeurs de logiciels proposent des solutions de virtualisation permettant d’abstraire les réseaux virtuels des réseaux physiques et de les sécuriser à l’aide de méthodes de chiffrement et d’authentification. La transmission de données d’un ordinateur à un autre s’effectue donc dans un réseau privé, également appelé **tunnel**.

Un autre exemple de virtualisation de réseau est **le réseau local virtuel (VLAN)**. Les VLAN sont des sous-réseaux virtuels basés sur un réseau informatique physique.

**Le Software Defined Networking (SDN)** est un concept qui permet de gérer les ressources du réseau virtuel de manière centralisée sans avoir à accéder manuellement aux composants physiques du réseau. Le SDN est basé sur le découplage du plan de contrôle virtuel (le Control Plane) du plan de réseau physique qui est responsable de la transmission des paquets de données (plan de commutation ou data plane).

|Avantages|Inconvénients|
|-----------|---------|
|Réduction des coûts grâce à l’utilisation multiple de l’infrastructure physique du réseau.|L’exploitation de plusieurs sous-réseaux virtuels sur un réseau physique nécessite des composants matériels puissants.|
|Les ressources réseau peuvent être gérées à un niveau virtuel de manière centralisée, elles sont facilement évolutives et sont réparties dynamiquement.|Une infrastructure de réseau physique redondante peut être nécessaire pour assurer une certaine fiabilité.|
|La virtualisation du réseau offre différentes approches qui permettent de mettre en œuvre des concepts de sécurité pour le réseau du côté logiciel et donc de manière plus rentable.||

## La virtualisation des données

La virtualisation des données est courant. Cela dépend du type de stockage et du fournisseur. La virtualisation du stockage permet de regrouper plusieurs disques de stockage physiques dans un stockage logique unique et il sera présenté comme un stockage unique à tous les serveurs.

Dans un contexte d’entreprise, la virtualisation du stockage est généralement mise en œuvre par blocs.

Les données sont alors divisées en blocs de taille égale et une adresse unique est attribuée à chaque bloc de données.

Cette dernière est stockée par le logiciel de virtualisation dans la table de mappage centrale.

La table de mappage contient donc toutes les métadonnées nécessaires pour localiser l’emplacement physique d’un bloc de données.

Ce mappage vous permet de gérer les données virtuelles indépendamment du contrôleur du support de stockage physique, par exemple, pour les déplacer, les copier, les mettre en miroir ou les répliquer.

En pratique, la virtualisation par blocs peut être mise en œuvre selon trois approches différentes :

- Basée sur l’hôte
- Basée sur l’appareil
- Basée sur le réseau

La virtualisation des ressources de stockage **basée sur l’hôte** est une approche généralement utilisée **en combinaison avec les machines virtuelles**. Avec ce concept, un système hôte présente à un niveau abstrait des lecteurs virtuels à un ou plusieurs systèmes invités (voir la virtualisation matérielle), qui sont implémentés soit par un gestionnaire de volume interne au système d’exploitation, soit par un logiciel séparé (appelé hyperviseur de stockage). Le matériel (disques durs et autres supports de stockage) est accessible par les pilotes de périphériques du système hôte. Le gestionnaire de volume ou **hyperviseur de stockage** est utilisé comme couche logicielle au-dessus des pilotes de périphériques et gère les entrées et sorties (Input/Output, abrégé I/O), les tables de mappage des I/O et la recherche de métadonnées.

Les fonctions natives qui permettent de créer des lecteurs virtuels sont disponibles dans presque tous les systèmes d’exploitation modernes.

- Windows : Logical Disk Manager (LDM)
- macOS : CoreStorage (depuis OS X Lion)
- Linux : Logical Volume Manager (LVM)
- Solaris et FreeBSD : zPools du système de fichiers Z File Systems (ZFS)

La virtualisation du stockage basée sur l’hôte ne nécessite aucun matériel additionnel, prend en charge n’importe quel périphérique de stockage et peut être mise en œuvre sans trop d’effort.

De plus, l’approche offre les meilleures performances par rapport à d’autres concepts, car chaque périphérique de stockage est traité immédiatement.

Cependant, les utilisateurs doivent accepter que la virtualisation du stockage (et donc la capacité d’optimiser l’utilisation du stockage) est limitée par l’hôte.

Des **schémas RAID** sont alors utilisés (abréviation de Redundant  Array of Independent Disks). Il s’agit d’un concept de stockage de données dans lequel plusieurs disques physiques sont combinés pour former une plateforme de stockage virtuel. L’objectif de la virtualisation du stockage est d’assurer une certaine sécurité grâce à la redondance. Pour ce faire, les données sont mises en miroir dans une matrice de disques et distribuées sur différents disques durs.

Les matrices de disques modernes offrent également la possibilité de connecter d’autres périphériques de stockage et de combiner ainsi les ressources de stockage de plusieurs matrices de disques au niveau virtuel tout en les gérant de manière centralisée. Les **contrôleurs de stockage** des unités de stockage connectées sont subordonnés à un contrôleur primaire qui se charge de l’administration centrale de la table de mappage et de la transmission des demandes d’I/O.

La virtualisation du stockage **basée sur les périphériques** offre également de bonnes performances grâce à **une faible latence des I/O**. En dehors des matrices de disques à fusionner, aucun autre composant matériel n’est nécessaire. Pour pouvoir intégrer des mémoires externes, ces appareils doivent toutefois disposer d’interfaces adéquates. La migration ou la réplication de données sur plusieurs systèmes peut échouer car de nombreux fabricants s’appuient sur des protocoles propriétaires pour les périphériques de stockage. Il convient également de noter que le contrôleur de stockage primaire peut saturer en cas de charge importante.

La virtualisation du stockage en réseau est particulièrement adaptée lorsque les ressources de stockage de systèmes hétérogènes doivent être combinées dans un pool de stockage virtuel. Dans un contexte d’entreprise, cette approche est généralement utilisée dans le cadre d’un réseau de stockage SAN.

L’avantage principal de l’approche réseau est que **les ressources de stockage de systèmes hétérogènes peuvent être gérées via une interface centrale**. Si la virtualisation du stockage en réseau est implémentée en mode hors bande (out of band), un logiciel spécial doit être implémenté côté hôte pour accéder aux périphériques de stockage disponibles dans le SAN. La méthode in band ne nécessite pas un tel logiciel, mais elle est plus complexe à mettre en œuvre et est généralement associée à une latence I/O plus élevée.

Les fournisseurs de solutions renommés pour la virtualisation du stockage sont EMC, HP, IBM, LSI et Oracle.

|Avantages|Inconvénients|
|-----------|---------|
|Les ressources physiques de stockage sont utilisées plus efficacement.|La virtualisation du stockage est toujours associée à un overhead du fait de la nécessité de générer et traiter des métadonnées.|
|L’utilisation des ressources de stockage n’est pas liée aux limites physiques des supports de stockage sous-jacents.|Le traitement des demandes d’I/O sous forte charge peut faire ralentir l’ensemble du système de stockage.|
|Les ressources physiques de stockage combinées dans un lecteur logique peuvent être gérées de manière centralisée.||
|Les ressources de stockage physique peuvent être étendues et restructurées indépendamment du pool de stockage virtuel.||

## Les hyperviseurs

L'hyperviseur est un processus qui crée et exécute des machines virtuelles. Il permet à un serveur physique d'héberger plusieurs machines virtuelles en partageant des ressources matérielles telles que CPU, mémoire, GPU, réseau, etc. L'hyperviseur est également appelé Virtual Machine Monitor (VMM). Il s'assure que ces VM n'interfèrent pas l'une avec l'autre.

Il existe principalement deux types d'hyperviseur :

- un hyperviseur de _type 1_ "**Bare metal**" : est un logiciel qui s'exécute directement sur le hardware, l'hyperviseur est ainsi l'outil de contrôle du système d'exploitation. Un système d'exploitation secondaire ou OS invités est alors exécuté au dessus du hardware. Il offre des performances élevées et une faible utilisation des ressources. C'est le modèle d'hyperviseur le plus répandu en entreprise.

Exemple: VMware ESXi, serveurs Xen, Hyper-V

- un hyperviseur de _type 2_  "**Host metal**" : est un logiciel qui s'exécute à l'intérieur d'un autre système d'exploitation l'OS de l'hôte. Un système d'exploitation invité s'exécute donc au troisième niveau au dessus du matériel. Il offre des performances modérées. Mais la configuration et la gestion de l’environnement sont très simples.

Exemple: VMware Workstation, Oracle Virtual Box.
