# TP 4 - Firewall

Tous les points avec un 👀 doivent figurer sur votre rendu.  
Avant de nous poser une question, avez-vous cherché sur le web ?  

- Merci d'être le plus précis dans vos retours et réponses.
- Pas d'image, merci encore.

---

Pour ce TP il vous faut :

- Les VMs du TP Services, avec leur service fonctionnel.

## Sommaire

- [TP 4 - Firewall](#tp-4---firewall)
- [Sommaire](#sommaire)
- [Iptables](#Iptables)
  - [Installation et configuration Iptables](#installation-et-configuration-iptables)
- [Serveur NFS](#serveur-nfs)
  - [Installation du serveur NFS](#installation-du-serveur-nfs)
  - [Configuration du serveur NFS](#configuration-du-serveur-nfs)
- [Serveur Minecraft](#serveur-minecraft)
  - [Installation du serveur Minecraft](#installation-du-serveur-minecraft)
  - [Supprimer un processus en cours](#supprimer-un-processus-en-cours)
  - [Configuration du serveur Minecraft](#configuration-du-serveur-minecraft)

## Iptables

Iptables est un logiciel libre permettant de configurer les tables de sécurité, du pare-feu du noyau Linux.

Explication des chaînes standard **INPUT, FORWARD et OUTPUT**:

- **INPUT** est en charge de livrer les paquets au système.
- **FORWARD** traite les paquets arrivants, en attente d’être transmis.
- **OUTPUT** contrôle le trafic de données généré par votre ordinateur.

Explications des options utilisées dans les commandes ci-dessous :

- -A : Ajoute une ou plusieurs règles à la fin de la chaîne spécifiée.
- -i : Nom de l'interface qui reçoit les paquets
- -p : Protocole de la règle ou du paquet à vérifier.
- -m : permet d'ajouter un module additionnel.
- conntrack : Module additionnel de Iptables permettant de conserver les connexions déjà établient.
- --ctstate : Spécifie les états consernés par la règle.
  - NEW : Signifie soit que le paquet a initié une nouvelle connexion, soit qu'il est associé à une connexion qui n'a pas vu passer de paquets dans les deux sens.
  - RELATED : Signifie que le paquet initie une nouvelle connexion, mais qu'il est associé avec une connexion existante, comme un transfert de données FTP ou une erreur ICMP.
  - ESTABLISHED : Signifie que le paquet est associé à une connexion qui a déjà vu passer des paquets dans les deux sens.
- comment --comment "" : Ajoute un commentaire à la règle.
- -j : Détermine ce qu'il faut faire si le paquet correspond à la règle.
- --reject-with icmp-host-prohibited : Message de rejet avec lequel le paquet est rejeté. Cela signifie que votre machine informera l'expéditeur que le paquet a été rejeté avec ce message.

## Installation et configuration Iptables

Etant donné que vous utiliserez **Iptables**, vous n'aurez pas besoin de **Firewalld**, de ce fait désactiver le.

Vous trouverez dans le lien ci-dessous, toutes les informations nécessaire à sa compréhension (nous ne verrons ici que les 3 chaînes standard) : <https://doc.ubuntu-fr.org/iptables>

Afin de vous faciliter la tâche, ainsi que pour vous montrer à quoi doivent ressembler vos règles Iptables,

- Ajouter ces règles pour la chaîne **INPUT**, sur toutes vos VMs :
  - `sudo iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT`
  - `sudo iptables -A INPUT -i lo -j ACCEPT`
  - `sudo iptables -A INPUT -p tcp --dport ssh -m conntrack --ctstate NEW -m comment --comment "ALLOW INCOMING SSH CLIENT CONNEXIONS" -j ACCEPT`
  - `sudo iptables -A INPUT -p icmp --icmp-type 8 -m conntrack --ctstate NEW -m comment --comment "ALLOW INCOMING ICMP PING REQUEST" -j ACCEPT`
- 👀 Réaliser ces mêmes règles mais pour la chaîne **OUTPUT** (sauf pour SSH), ainsi qu'une règle pour le trafic web.
- 👀 Sur toutes vos VMs, grâce à **Iptables** accepter les paquets des services **DHCP, DNS, FTP, NFS, serveur Minecraft**. (Les ports sont trouvables très facilement sur internet)
- Ajouter ces règles après avoir ajouté toutes vos autres règles :
  - `sudo iptables -A INPUT -m comment --comment "REJECT UNAUTHORIZED CONNEXIONS" -j REJECT --reject-with icmp-host-prohibited`
  - `sudo iptables -A OUTPUT -m comment --comment "REJECT UNAUTHORIZED CONNEXIONS" -j REJECT --reject-with icmp-host-prohibited`
- 👀 **DROP**er les 3 chaînes standard.
- 👀 Prouver que vos services **DHCP, DNS et FTP** fonctionnent toujours.

## Serveur NFS

Vous installerez ce service sur la VM FTP.

## Installation du serveur NFS

- Installer les paquets **nfs-utils (nfs-utils-lib)** sur votre VM serveur et sur vos VMs clients.
- Activer et démarrer les services **rpcbind nfs-server** à l'aide de **systemctl**.

## Configuration du serveur NFS

- 👀 Renseigner le domaine local dans `/etc/idmapd.conf`.
- Créer un dossier **partage** dans `/home/<votreUser>`.
- 👀 Renseigner le/les répertoire(s) que vous souhaitez partager dans *`/etc/exports`.
  - Par défauts les fichiers modifiés prendront comme utilisateur propriétaire **nobody**,
  - 👀 Faites en sorte que les fichiers partagés ne deviennent pas la propriété de l'utilisateur **nobody**. (Regardez du coté de **anonuid** et **anongid**).
- 👀 Monter le partage sur vos clients, et échanger des fichiers entre eux.
  - Depuis **client 1** monter le dossier partagé, créer un fichier dans ce dossier et écrivez un message,
  - Sur **client 2** monter le dossier partagé, écriver une 2ème ligne dans le fichier créé par **client 1**,
  - Affichez le fichier modifié sur **client 1**.

## Serveur Minecraft

Vous installerez ce service sur la VM FTP.

## Installation du serveur Minecraft

- Installer les paquets **java-1.8.0-openjdk-headless** et **screen**
- Vérifier que Java est bien installé, en vérifiant sa version
- Créer un dossier Minecraft dans lequel vous téléchargerez **minecraft_server.jar**
  - `wget https://minecraft.net/download/minecraft_server.jar`
- 👀 Lancer votre serveur Minecraft, en utilisant le mode daemon de **screen**, afin que les fichiers de configuration se créent :
  - Afin de lancer screen en mode daemon il existe le paramètre `-dmS <ScreenName>`
  - Vous devrez aussi créer un fichier contenant la commande ci-dessous et précisé ce fichier dans la commande **screen**,
  - Commande permettant de lancer votre serveur Minecaft : `java -Xmx512M -Xms512M -jar minecraft_server.jar nogui`.

## Supprimer un processus en cours

- 👀 Lister les processus en cours et retrouver le **PID** appartenant au processus **screen en mode daemon**.
  - Vous trouverez cette commande dans les prérequis, disponible ici : <https://github.com/GabrielClmcn/Ydays-Labo-Infra-2020/tree/master/Cours/1_debutant/0_prerequis>
  - Ajouter les paramètres `-aux` à cette commande.
  > -a : présente également les processus des autres utilisateurs.\
  > -u : présente le nom de l'utilisateur et l'heure de lancement.\
  > -x : affiche les processus qui n'ont pas de terminal de contrôle.
- 👀 Une fois retrouvé, tuer ce processus.

## Configuration du serveur Minecraft

- Ouvrer le fichier `server/eula.txt` et remplacer **false** par **true**.
- 👀 Modifier le fichier de configuration `server/server.properties` afin que le serveur puisse fonctionner.
- 👀 Prouver le bonne fonctionnement du serveur en screenant votre connexion à celui-ci, ainsi qu'un de votre fichier de log, de votre serveur Minecraft.

> Nous DM si vous ne possédez pas le jeu Minecraft, pour qu'on vous donne une version cracké.
---

Enjoy 🎉
