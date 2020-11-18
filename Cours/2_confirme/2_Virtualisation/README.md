# La virtualisation
- [Définition](#i-définition)
- [Le rôle de l'hyperviseur](#ii-le-rôle-de-l'hyperviseur)
  - [1. Virtualisation de serveur](#1-virtualisation-de-serveur)
  - [2. Virtualisation de poste de travail](#2-virtualisation-de-poste-de-travail)
    - [A. Logiciel](#a-logiciels)
    - [B. Avantages](#b-avantages)
    - [C. Inconvénients](#c-inconvénients)
- [II. stockage](#ii-stockage)

# I. Définition
**Virtualisation :** faire fonctionner, sur une même machine physique, plusieurs systèmes comme s'ils fonctionnaient sur des machines physiques distinctes.

Pour rappel, un serveur normal est décomposé en 3 couches :
- Hardware
- OS
- Application

La virtualisation consiste alors a utiliser le hardware et donc les ressources de la machine pour faire tourner plusieurs systèmes comme si chaque systèmes tournait sur une machine séparée avec ses propres ressources matérielles.

Avec la virtualisation sur cette même machine, on aura donc plusieurs OS sur les quels tournent des applications. Il s'agit d'un exemple de virtualisation mais il en existe d'autres.

# II. Le rôle de l'hyperviseur
**Hyperviseur :** le rôle de l'hyperviseur est d'assurer le contrôle du processeur et des ressources de la machine hôte, il permet d'allouer alternativement à chaque machine virtuelle ce dont elle a besoin. Il s'assure que ces VM n'interfèrent pas l'une avec l'autre.

Il existe principalement deux types d'hyperviseur :
- un hyperviseur de _type 1_ **"Bare metal"** : est un logiciel qui s'exécute directement sur le hardware, l'hyperviseur est ainsi l'outil de contrôle du système d'exploitation. Un système d'exploitation secondaire ou OS invités est alors exécuté au dessus du hardware. C'est le modèle d'hyperviseur le plus répandu en entreprise.
- un hyperviseur de _type 2_ **"Host metal"** : est un logiciel qui s'exécute à l'intérieur d'un autre système d'exploitation l'OS de l'hôte. Un système d'exploitation invité s'exécute donc au troisième niveau au dessus du matériel.

Avant de passer à la suite il est important de préciser qu'il existe plusieurs types de virtualisation :

## 1. Virtualisation de serveur 
Souvent, c'est un OS de serveur qui est choisi pour être installé dans la machine.

## 2. Virtualisation de poste de travail

**VDI** : **V**irtual **D**esktop **I**nfrastructure est la forme la plus courant de virtualisation de postes de travail. Dans ce cas, le poste de travail est hébergé dans un datacenter. L'utilisateur utilise alors son poste par accès distant et déport d'affichage comme s'il était présent localement  sur son poste. L'environnement de travail est alors directement associé au profil utilisateurs et l'utilisateur a la même vue sur son environnement quel que soit le terminal utilisé.

**Streaming d'OS** : Dans ce cas le système démarre à partir d'un disque installé sur le réseau et charge de façon sélective les contenus et les applications demandés par l'utilisateur depuis un serveur distant.

### A. Logiciels

**VDI** :
- **VMware** a créé le produit de VDI VMware View. (**VMware Horizon** actuellement)
- **Citrix** a créé le produit de VDI **XenDesktop**.
- **LTSP - Linux Terminal Server Project**, intégré dans la distribution Edubuntu ou comme paquet à installer sur un serveur GNU/Linux.
- **Microsoft** utilise les solutions Citrix mais a inclus une solution VDI dans Windows Server 2008.
- **Oracle** a développé le produit de VDI Oracle Virtual Desktop Infrastructure.
- **Red Hat** intègre une solution à Red Hat Enterprise Virtualization (RHEV).
- **Systancia** a créé le produit de VDI AppliDis.
- **Neocoretech** a créé le produit de VDI Neocoretech Desktop Virtualisation (NDV).

**Streaming d'OS** :
- **VMware** la créé le produit de streaming d'OS **ThinApp**
- **Citrix** a créé le produit de streaming d'OS **Provisionning Server**

### B. Avantages

|VDI|Streaming d'OS|
|---|--------------|
|- Création simple de nouveaux postes de travail|- Exploite entièrement les ressources de la machine|
|- Facilité et bas coût du déploiement de nouvelles applications|- Installations et mises à jours centralisés|
|- Meilleure sécurisation des données|- Configuration réinitialisée à chaque démarrage|
|- Meilleurs cycles de rafraichissement de l'infrastructure de bureau client|Pas nécessaire de déployer une infrastructure spécifique|
|- Accès sécurisé à distance à un environnement de bureau d'entreprise|

### C. Inconvénients

|VDI|Streaming d'OS|
|---|--------------|
|- Dégradation de la performance potentielle, peut être causé par l'utilisation de la bande passante du réseau, les mauvais protocoles utilisés ainsi que des ressources pas assez robustes|
|- Risques potentiels pour la sécurité si le réseau n'est pas correctement géré|
|- Difficulté dans la mise en place et le maintien des pilotes pour imprimantes et autres périphériques|
|- Difficulté dans la gestion de certaines applications complexes (notamment multimédia)|
|- Arrêt dans le cas de défaillances du réseau, qui peuvent être évitées par l'utilisation d'un système de fichiers en cluster|
|- Dépendance à la connectivité au réseau d'entreprise ou public|
|- La complexité et les coûts élevés du déploiement et la gestion|


