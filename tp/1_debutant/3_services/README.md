# TP 2 - Services

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

- [TP 2 - Services](#tp-2---services)
- [Sommaire](#sommaire)
- [Vue globale de l'infra](#vue-globale-de-l'infra)
- [Réseau MGMT](#Réseau-mgmt)
- [Serveur DHCP](#serveur-DHCP)
  - [Installation d'un serveur DHCP](#installation-d'un-serveur-dhcp)
  - [Configuration du serveur DHCP](#configuration-du-serveur-dhcp)
- [Serveur DNS](#serveur-dns)
  - [Installation d'un serveur DNS](#installation-d'un-serveur-dns)
  - [Configuration du serveur DNS](#configuration-du-serveur-dns)
- [Serveur FTP](#serveur-ftp)
  - [Installation d'un serveur FTP](#installation-d'un-serveur-ftp)
  - [Configuration du serveur FTP](#configuration-du-serveur-ftp)

## Vue globale de l'infra

Votre infrastructure se composera de **trois serveurs** et de **deux clients**.

- Le **serveur DHCP** permet de **d'attribuer des adresses IP** aux clients.
- Le **serveur DNS** permet de **résoudre le nom de domaine** attribué à vos machines.
- Le **serveur FTP** permet **d'échanger des fichiers** entre différentes machines.

---

## Réseau MGMT

- 👀 Attribuer une adresse IP statique à vos machines sur le réseau de mgmt
- Réaliser une connexion `SSH` sur votre machine sur le réseau de mgmt et travailler depuis cette connexion.

## Serveur DHCP

- Attribuer une adresse IP statique à cette machine sur les réseaux local
- Réaliser une connexion `SSH` sur votre machine sur le réseau de mgmt et travailler depuis cette connexion.
- Modifier le `hostname` de cette machine par un nom explicite la concernant (Tip : Ca pourrait vous être utile pour le DNS, on dit ça, on dit rien)

👀 Quelle **range d'adresses IP allez vous utiliser** dans votre réseau ?
⚠ Attention vous savez des choses à propos de ça, pensez-y ⚠

## Installation du service DHCP

- Installer les paquets `dhcp` et `bind-utils`.
- 👀 Désactiver la carte NAT. Expliquer pourquoi.
- 👀 Vérifier si le service `dhcp` est actif, sinon lancer le et rendre son démarrage permanent à l'aide de `systemctl`.

## Configuration du serveur DHCP

- 👀 Réaliser la configuration du service, fournissez nous en copiant collant le contenu des fichiers de conf ci-dessous :

`/etc/sysconfig/dhcpd/dhcpd.conf`  
`/etc/dhcp/dhcpd.conf`

- Récupérer une adresse IP à l'aide de votre serveur `DHCP` respectivement sur vos deux machines clientes.

> The internet is your friend.

👀 :

- Montrer les adresses IP qui ont été attribués à vos machines clientes
- Quelle commande utiliser pour récupérer une adresse IP de votre serveur DHCP ?
- Quelle est la commande utilisée pour libérer votre interface de l'adresse IP qui lui est attribuée ?

---

## Serveur DNS

- Attribuer une adresse IP statique à cette machine sur les réseaux de mgmt et local
- Réaliser une connexion `SSH` sur votre machine sur le réseau de mgmt et travailler depuis cette connexion.
- Modifier le `hostname` de cette machine par un nom explicite la concernant

## Installation d'un serveur DNS

- Installer le paquet `bind` et `bind-utils`.
- Désactiver la carte NAT

## Configuration du serveur DNS

L'un des fichiers de configuration de votre serveur DNS se trouve ici, à vous de nous dire où se trouve les deux autres :

Donner pour nom à votre DNS : `labo-infra.local`

`/etc/named.conf`

- 👀 Créer une zone direct
- 👀 Créer une zone inversé

Une fois votre configuration terminer :

- Démarrer le service `named` et rendre son démarrage permanent.

> The internet is your BEST friend.

👀 :

- Réaliser un dig depuis votre serveur `DHCP` vers votre serveur `DNS` et `FTP`.
- Réaliser un ping avec le nom `DHCP` attribué à vos machines `DNS` et `FTP`.
- Réaliser un dig depuis votre serveur `DNS` vers votre serveur `DHCP` et `FTP`.
- Réaliser un ping avec le nom DNS attribué à vos machines `DHCP` et `FTP`.

Tiens ? Ca ne fonctionne pas ? :) Retenter en arrêtant le daemon `firewalld`. Ca va mieux n'est-ce pas ? Ne le dites surtout pas mais notre prochain cours portera peut-être dessus 😉

---

## Serveur FTP

- Attribuer une adresse IP statique à cette machine sur les réseaux de mgmt et local
- Réaliser une connexion `SSH` sur votre machine sur le réseau de mgmt et travailler depuis cette connexion.
- Modifier le `hostname` de cette machine par un nom explicite la concernant

## Installation d'un serveur FTP

- Installer le paquet **proftpd**.
- Activer et démarrer le service à l'aide de **systemctl**.

## Configuration du serveur FTP

👀 Réaliser la configuration du serveur FTP.

- 👀 L'utilisateur Anonmous et root, n'ont pas le droit de se connecter.
- 👀 Resteindre l'accès au serveur à `/tmp/ftpfiles/`

> You're living a real love story with the internet, it's really beautiful to see that. A real couple goal :heart:

👀 :

- Sur Client 1 créer un fichier et écriver "hello" dans un fichier.
- Envoyer ce fichier sur le serveur FTP afin que Client 2 puisse le récupérer.
- Prouver qu'Anonymous et root ne peuvent pas se connecter au serveur
- Répertorier les commandes que vous avez utilisés pour réaliser ces actions.

---

Enjoy 🎉
