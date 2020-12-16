# TP 3 - Services

Tous les points avec un 👀 doivent figurer sur votre rendu.  
Avant de nous poser une question, avez-vous cherché sur le web ?  

- Merci d'être le plus précis dans vos retours et réponses.
- Pas d'image, merci encore.

---

Pour ce TP il vous faut :

- 5 Machines CentOS 7 avec 3 interfaces chacunes :
  - 1 carte NAT
  - 1 réseau privé de management
  - 1 réseau privé qui sera votre réseau local

> Si toutefois vous n'avez pas assez de RAM, une fois l'installation terminé, vous pouvez essayer de descendre à 512Mo.

- Mettre à jour vos paquets sur l'ensemble de vos machines avant toute action :

```bash
yum update -y
```

## Sommaire

- [TP 3 - Services](#tp-2---services)
- [Sommaire](#sommaire)
- [Vue globale de l'infra](#vue-globale-de-l'infra)
- [Réseau MGMT](#Réseau-mgmt)
- [Serveur DHCP](#serveur-DHCP)
  - [Installation d'un serveur DHCP](#installation-d'un-serveur-dhcp)
  - [Configuration du serveur DHCP](#configuration-du-serveur-dhcp)
  - [Vérfication DHCP](###-Vérification-dhcp)
- [Serveur DNS](##serveur-dns)
  - [Installation d'un serveur DNS](#installation-d'un-serveur-dns)
  - [Configuration du serveur DNS](#configuration-du-serveur-dns)
  - [Vérfication DNS](###-Vérification-dns)
- [Serveur FTP](##-serveur-ftp)
  - [Installation d'un serveur FTP](###-installation-d'un-serveur-ftp)
  - [Configuration du serveur FTP](###-configuration-du-serveur-ftp)
  - [Vérfication FTP](###-Vérification-ftp)

## Vue globale de l'infra

Votre infrastructure se composera de **trois serveurs** et de **deux clients**.

- Le **serveur DHCP** permet **d'attribuer des adresses IP** aux clients.
- Le **serveur DNS** permet de **résoudre le nom de domaine** attribué à vos machines.
- Le **serveur FTP** permet **d'échanger des fichiers** entre différentes machines.

---

## Réseau MGMT

- 👀 Attribuer une adresse IP statique à vos machines sur le réseau de mgmt
- Réaliser une connexion `SSH` sur votre machine sur le réseau de mgmt et travailler depuis cette connexion.

## Serveur DHCP

- Attribuer une adresse IP statique à cette machine sur les réseaux mgmt et local.
- Réaliser une connexion `SSH` sur votre machine sur le réseau de mgmt et travailler depuis cette connexion.
- Modifier le [`hostname`](https://www.geeksforgeeks.org/hostname-command-in-linux-with-examples/) de cette machine par un nom explicite la concernant (Tip : Ca pourrait vous être utile pour le DNS, on dit ça, on dit rien)

👀 Quelle **range d'adresses IP DHCP allez vous utiliser** dans votre réseau local ?  
⚠ Attention vous savez des choses à propos de ça, pensez-y ⚠

### Installation du service DHCP

- Installer les paquets `dhcp` et `bind-utils`.
- 👀 Désactiver la carte NAT. Expliquer pourquoi.

### Configuration du serveur DHCP

- 👀 Réaliser la configuration du service, fournissez nous en copiant collant le contenu des fichiers de conf ci-dessous :

`/etc/sysconfig/dhcpd`  
`/etc/dhcp/dhcpd.conf`

- 👀 Vérifier si le service `dhcp` est actif, sinon lancez le et rendre son démarrage permanent à l'aide de `systemctl`.

> The internet is your friend.

### Vérification DHCP

👀 :

- Récupérer une adresse IP à l'aide de votre serveur `DHCP` sur vos deux machines clientes.
- Montrer les adresses IP qui ont été attribués à vos machines clientes.
- Quelle commande avez vous utiliser pour récupérer une adresse IP de votre serveur `DHCP` ?
- Quelle est la commande utilisée pour libérer votre interface de l'adresse IP qui lui est attribuée ?

---

## Serveur DNS

- Attribuer une adresse IP statique à cette machine sur les réseaux de mgmt et local.
- Réaliser une connexion `SSH` sur votre machine sur le réseau de mgmt et travailler depuis cette connexion.
- Modifier le `hostname` de cette machine par un nom explicite la concernant.
- Modifier le `hostname` de la machine `FTP` par un nom explicite la concernant.

### Installation d'un serveur DNS

- Installer le paquet `bind` et `bind-utils`.
- Désactiver la carte NAT.

### Configuration du serveur DNS

Les fichiers de configuration de votre serveur DNS se trouvent ici :

- `/etc/named.conf`
- `/var/named/lab-infra.local.db`
- `/var/named/10.10.20.db`

> Certain d'entre eux sont à créer.

- 👀 Assigner le nom `lab-infra.local` comme domaine DNS dans le fichier `/etc/named.conf`. ⚠ **Il y a d'autres configurations à réaliser dans ce fichier.** ⚠
- 👀 Créer une zone direct. Cette zone est à créer dans le fichier `lab-infra.local.db`.
- 👀 Créer une zone inversé. Cette zone est à créer dans le fichier `10.10.20.db`.

> The internet is your BEST friend.

Une fois votre configuration terminer :

- Vérifier si le service `named` est actif, sinon lancer le et rendre son démarrage permanent.

### Vérification DNS

👀 :

- Réaliser un dig depuis votre serveur `DHCP` vers vos serveurs `DNS` et `FTP`.
- Réaliser un ping depuis votre serveur `DHCP` avec le nom `DNS` attribué à vos machines `DNS` et `FTP`.
- Réaliser un dig depuis votre serveur `DNS` vers vos serveur `DHCP` et `FTP`.
- Réaliser un ping depuis votre serveur `DNS` avec le nom `DNS` attribué à vos machines `DHCP` et `FTP`.

Tiens ? Ca ne fonctionne pas ? :) Retenter en arrêtant le daemon `firewalld`. Ca va mieux n'est-ce pas ? Ne le dites surtout pas mais notre prochain cours portera peut-être dessus 😉

---

## Serveur FTP

- Attribuer une adresse IP statique à cette machine sur les réseaux de mgmt et local
- Réaliser une connexion `SSH` sur votre machine sur le réseau de mgmt et travailler depuis cette connexion.

### Installation d'un serveur FTP

- Installer le paquet `epel-release`. Une fois fait, vous pouvez installer le paquet `proftpd`.
- 👀 Vérifier si le service est actif, sinon lancer le et rendre son démarrage permanent.

### Configuration du serveur FTP

👀 Réaliser la configuration du serveur FTP.

- Les fichiers que vous avez à modifier sont `/etc/proftpd.conf` et `/etc/ftpusers`.
- 👀 L'utilisateur `Anonymous` et `root`, n'ont pas le droit de se connecter.
- Faire un `touch file` dans `~/` et la même chose dans `/root/`.
- Créer un dossier `ftpFiles/` dans `/tmp/`
- 👀 Resteindre l'accès au serveur à `/tmp/ftpfiles/` prouver le avec le fichier de configuration `proftpd.conf`.
- Redémarrer le service.

> You're living a real love story with the internet, it's really beautiful to see that. A real couple goal :heart:

### Vérification FTP

👀 :

- Afin que la machine `Client 1` et `Client 2` puissent se connecter au serveur `FTP` il vous faudra sur chacun d'elles installer le paquet `lftp`.
- Sur `Client 1` créer un fichier et écriver "hello" à l'intérieur.
- Envoyer ce fichier sur le serveur `FTP` afin que `Client 2` puisse le récupérer, le modifié et enfin le renvoyé sur le serveur `FTP`.
- Afficher le fichier modifié depuis `Client1`.
- Prouver qu'`Anonymous` et l'utilisateur `root` ne peuvent pas se connecter au serveur `FTP`.
- Resteindre l'accès au serveur à `/tmp/ftpfiles/`
- Répertorier les commandes que vous avez utilisés pour réaliser ces actions.

---

Enjoy 🎉
