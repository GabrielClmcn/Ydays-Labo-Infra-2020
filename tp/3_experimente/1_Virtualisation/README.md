# TP n°1 :

Objectif : Virtualiser une machine physique sur un ESXi.

Prérequis : VMware Workstation
3 VM :
- 1 esxi
- 1 VM Windows
- 1 VM Linux

Toutes les machines dans le même réseau. 

## 1. Installation de VMware vSphere Hypervisor (ou Esx 7)

1. Trouver les prérequis hardware pour installer un Esxi.
2. Installer l'esxi dans VMware Workstation
  - Mettez les ressources nécessaires pour faire tourner les VM que l'on va migrer. 
4. Suivez les instructions suivantes :
  - Avoir une IP statique
  - Insérer la licence
  - Ajouter un datastore (assez gros pour héberger quelques VM)

## 2. Utilisation de VMware vCenter Converter Standalone (mode local)

1. Crée une VM Windows Server (Client si pas de ressource).
  - Assurer vous que les 2 machines se ping.
2. Installer vCenter Converter en mode local sur cette VM.
3. Utiliser la solution pour migrer la VM dans l'esxi.
4. Vérifier que la VM fonctionne bien dans votre ESXI

## 3. Utilisation de VMware vCenter Converter Standalone (mode Client-Server)

1. Crée une VM Linux.
2. Installer vCenter Converter sur votre PC pour le Windows migrer précédemment en mode client-serveur.
3. Utiliser le pour migrer le serveur linux sur l'esxi.
4. Vérifier que la VM fonctionne bien dans votre ESXI

Question : 

Quel sont les différences entre les 2 modes ? Dans quel cas on va privilégié le mode local ? Et le mode Client-Server ?

## 4. Manipulation de l'esxi

À suivre
