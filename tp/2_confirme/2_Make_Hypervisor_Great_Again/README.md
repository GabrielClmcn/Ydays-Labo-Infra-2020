# Projet n°2 : Make Hypervisor Great Again !
Ce projet à pour but de prendre en main une infrastructure de virtualisation. De nos jours, beaucoup d'entreprise utilise cette architecture, notamment pour les raisons cité dans le cours (cf. cours Infrastructure Virtualisée)

L'objectif est de vous présenter les différentes fonctionnalité que cette infrastructure peut proposer.

- [0. Setup](#0-setup)
- [1. Mise en place de l'hyperviseur](#0-setup)
- [2. Mise en place du stockage](#0-setup)
- [3. Configuration iSCSI](#0-setup)
- [4. Rendu](#0-setup)

## 0. Setup

**Attention !** Il est obligatoire d'utiliser VmWare Workstation 16 pour réaliser le projet.

> Noté sur le côté  les mots de vocabulaires (vSwitch, LUN, iSCSI, etc...). Lors de votre présentation on considère que vous avez parfaitement compris tous les mots du projet en question.

- 1 x VM Stockage (Xepenology)
- 1 x VM vSphere Hypervisor 7.0
- 1 x Réseau NAT
- 1 x Réseau interne (iSCSI)

La topologie est la suivant :
![topo.png](https://github.com/GabrielClmcn/Ydays-Labo-Infra-2020/blob/master/tp/2_confirme/2_Make_Hypervisor_Great_Again/screenshot/topo.png)

## 1. Mise en place de l'hyperviseur
1. Trouver les prérequis minimal pour installer un ESX.
2. Installer l'esx.
3. Faire la configuration réseau :
    - IP statique pour l'interface management
    - Activé le **SSH**
    - Activé la console **shell**
    - Crée un nouveau **vSwitch**
    - Le lié au **vmnic1**
    - Crée une carte **VMKernel** avec l'ip pour le réseau iSCSI

## 2. Mise en place du stockage
1. Importer la VM [Xepenology](https://xpenology.com/forum/topic/13019-tuto-configs-toute-pr%C3%AAte-pour-vmware/). Elle vous permettra de simuler un NAS Synology.
2. Dérouler l'installation et configurer la partie réseau
    - Mettre une IP statique pour le management
    - Mettre une IP statique pour la partie **iSCSI**
3. Configurer un RAID 5 avec 3 disques de 40 go.
    - Lors de la création de ces disque de **DATA**, penser à suivre le tuto sur le lien.

## 3. Configuration iSCSI
1. Configurer la target iSCSI sur le NAS
2. Crée un LUN
3. Connecter l'esx à son stockage distant
4. Crée un nouveau datastore puis une VM Windows depuis ce datastore
5. Télécharge cristalDiskMark sur le windows et lance le
6. Casser un disque du RAID. Que remarquer vous ?

## 4. Rendu
Explication théorique et de comment vous avez fait + démonstration du HA RAID

---

Enjoy 🎉
