# Cours n°1 : L'adressage IP

ToDo: Sommaire  
Pré-requis  
Masque de sous-réseau calcul

## Sommaire

- [Internet Protocol](#IP)
  - [2 versions](#2-versions)
    - [IPv4](#IPv4)
    - [IPv6](#IPv6)
  - [3 types d'adresses](#3-types-d'adresses)
    - [Publique](#Publique)
    - [Privé](#Privé)
    - [Adresses](#Adresses)
- [Les différents composants d'un adressage IP](#Les-différents-composants-dun-adressage-IP)
  - [L'adresse de réseau](##Ladresse-de-réseau)
  - [L'adresse de broadcast](#Ladresse-de-broadcast)
  - [Masque de sous-réseau](#Masque-de-sous-réseau)
    - [Notation CIDR](#Notation-CIDR)
  - [Adresses utilisables](#Adresses-utilisables)
  - [Adresses disponibles](#Adresses-disponibles)
- [Comment créer son premier réseau](#Comment-créer-son-premier-réseau)
  - [Méthode de calcul](#Méthode-de-calcul)
    - [Adresse de réseau](#Adresse-de-réseau)
    - [Adresse de broadsact](#Adresse-de-broadsact)
    - [Adresses utilisables](#Adresses-utilisables)
    - [Adresses disponibles](#Adresses-disponibles)

---

## Pré-requis

- [ET Logique (AND)](##1.---Internet-Protocol)
- [OU logique (OR)](##1.---Internet-Protocol)

## IP

Quel est son utilité et par quoi est-ce utilisé ?

> L'adresse IP est l'abréviation d'Internet Protocol un identifiant permanant (statique) ou provisoir (dynamique) attribué à un équipement réseau se trouvant sur la couche 3 du modèle OSI.

Une adresse IP est attribué à une interface réseau possédant une `adresse physique` (Adresse MAC).

### 2 versions

L'adresse IP possède deux versions utilisées aujourd'hui.  
L'`IPv4` et l'`IPv6`. L'ensemble de ce cours portera sur l'`IPv4`, l'`IPv6` est abordé de façon très bref.

#### IPv4

L'IPv4 est une représentation décimal de 0 à 255 séparer par des points (4*8 bits)

Exemple :

`192.168.1.47` est une adresse IPv4 en `notation décimal`.

L'IPv4 peut se découper en deux partie. La partie `réseau` et la partie `hôte`.

La partie `réseau` est **commune** à tous les hôtes d'un même réseau. Cette partie de l'adresse IP est définie par le masque de sous réseau que nous définissons.

Exemple d'une partie `réseau` :  
192.168.0.\_\_ /24

La partie `hôte` est **unique** à l'intérieur d'un même réseau.

Exemple `hôte`:
\_\_.\_\_.10.89 /16

#### IPv6

L'IPv6 est une représentation en hexadécimal séparé par deux-points (16 * 8 bits)

Exemple :

`2001:0db8:0000:85a3:0000:0000:ac1f:8001` est une adresse IPv6 en `notation hexadécimal`

## 3 types d'adresses

### Publique

Une adresse publique est unique dans le monde.

Vous pouvez tapez pour exemple l'adresse IP `216.58.213.142` sur votre barre URL de votre navigateur afin d'aller sur le site web [www.google.com](https://www.google.com)

### Privée

Une adresse privée est unique dans un réseau local.

Les adresses réseaux suivants sont des adresses utilisés pour de l'adressage privée. Ces adresses réseaux sont définies par la RFC 1918.

10.0.0.0/8  
172.16.0.0/16  
192.168.0.0/24  

### Spécial

127.0.0.0/8 est votre adresse de bouclage, autrement appeler `localhost`.

Cette adresse vous permet d'effectuer des essais ou de démarrer des applications localement sur votre propre machine.

## Les différents composants d'un adressage IP

### L'adresse de réseau

La première adresse IP d'un réseau. Elle est inutilisable. Sa fonction est d'identifier le réseau.

### L'adresse de broadcast

Egalement appellé adresse de diffusion elle est la dernière adresse IP d'un réseau. Elle est inutilisable. Sa fonction est d'envoyer des paquets à tous les membres de son même réseau sans distinction et sans diffuser les informations de ses récepteur sur le réseau.

---

> Les autres adresses permettent à identifier des machines connectées au réseau.

### Masque de sous-réseau

Il défini la partie hôte de notre réseau mais également de diviser notre réseau.

Voici quelques exemples de masque de sous-réseau :

255.0.0.0 ou /8
255.255.0.0 ou /16
255.255.255.0 ou /24
255.255.255.252 ou /30

#### Notation CIDR

Cette notation CIDR est une seconde manière d'écrire le masque de sous-réseau **plus rapide** et **plus simple à lire**. Il indique le nombre de bits à l'état 1.

Exemples :

255.0.0.0 ou /8  
1111 1111.0000 0000.0000 0000.0000 0000  

Nombres de bits à l'état 1 : 8
>La notation CIDR de 255.0.0.0 est donc /8

255.255.0.0 ou /16  
1111 1111.1111 1111.0000 0000.0000 0000  

Nombres de bits à l'état 1 : 16
>La notation CIDR de 255.255.0.0 est donc /16

255.255.255.0 ou /24  
1111 1111.1111 1111.1111 1111.0000 0000  

Nombres de bits à l'état 1 : 24
>La notation CIDR de 255.255.255.0 est donc /24

## Comment créer son adressage réseau IPv4

Afin de créer son adressage réseau il est nécessaire d'avoir :

- Une adresse réseau `privée`
- Un masque de sous-réseau

Rien d'autre ? Enfaite si, il est plutôt utile de savoir certaines choses comme  comment connaître son adresse de réseau à partir d'une adresse IP, son adresse de broadcast, le nombre d'adresse utilisable...  

Pour ça, il faut regarder juste en dessous.

Il est important de savoir aussi qu'un réseau ça évolue alors il est préférable de prévoir une marge et de ne pas utiliser le nombre fixe d'adresse dont vous avez besoin au moment précis.

### Méthode de calcul

Nécessite de connaître et comprendre la conversion `binaire` vers `décimal` et `décimal` vers `binaire`.  
Afin de vous aider voici un tableau à utiliser :

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
|     |    |    |    |   |   |   |   |

Exemples :

Donner l'adresse IP suivante en binaire :

10.65.0.3

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 0   | 0  | 0  | 0  | 1 | 0 | 1 | 0 |
> 10

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 0   | 1  | 0  | 0  | 0 | 0 | 0 | 1 |
> 65

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 0   | 0  | 0  | 0  | 0 | 0 | 0 | 0 |
> 0

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 0   | 0  | 0  | 0  | 0 | 0 | 1 | 1 |
> 3

Résultat :

> 0000 1010.0100 0001.0000 0000.0000 0011

Donner l'adresse IP suivante en décimal :

1100 0000.1010 1000.0001 0100.1111 1110

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 1   | 1  | 0  | 0  | 0 | 0 | 0 | 0 |
> 192

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 1   | 0  | 1  | 0  | 1 | 0 | 0 | 0 |
> 168

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 0   | 0  | 0  | 1  | 0 | 1 | 0 | 0 |
> 20

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|-----|----|----|----|---|---|---|---|
| 1   | 1  | 1  | 1  | 1 | 1 | 1 | 0 |
> 254

Résultat :
> 192.168.20.254

Vous avez compris ? Non ? Rien de plus simple, il suffit d'additioner les valeurs où se situe les bits à l'état 1.  
> 8 + 2 = 10  
64 + 1 = 65  
128 + 32 + 8 = 168  
128 + 64 + 32 + 16 + 8 + 4 + 2 = 254  
etc...

C'est plus clair maintenant ? Vous êtes donc prêt pour un lire la suite et un bon exercice d'entrainement avant le TP 😊

#### Adresse de réseau

Afin de connaître notre adresse de réseau il est nécesaire de connaître une adresse IP et son masque de sous réseau.  
Utilisation du `ET logique (AND)` nécessaire afin d'obtenir le résultat.

Exemple :

192.168.1.47/24  

|                                  |                                             |
|----------------------------------|---------------------------------------------|
| Adresse IP en binaire | 1100 0000.1010 1000.0000 0001.0010 1111                |
| Masque de sous-réseau en binaire | 1111 1111.1111 1111.1111 1111.0000 0000     |
| Adresse de réseau en binaire     | 1100 0000.1010 1000.0000 0001.0000 0000     |
| Adresse de réseau en décimal     | 192.168.1.0                                 |

Résultat :

> 192.168.1.0

#### Adresse de Broadcast

Nécessite l'adresse réseau en binaire.
Utilisation du `OU logique (OR)` nécessaire afin d'obtenir le résultat.  

De manière plus simple il vous faut placer la **partie hôte** de cette adresse à une valeur de bits à l'état 1 pour récupérer l'adresse de broadcast.

Exemple :

192.168.1.0/24

|                                  |                                         |
|----------------------------------|-----------------------------------------|
| Adresse de réseau en binaire     | 1100 0000.1010 1000.0000 0001.0000 0000 |
| Adresse de broadcast en binaire  | 1100 0000.1010 1000.0000 0001.1111 1111 |
| Adresse de broadcast en décimal  | 192.168.1.255                           |

Résultat :

> 192.168.1.255

#### Adresses utilisables

Le nombre d'adresse utilisable dans votre réseau s'obtient à l'aide de 2 puissance le chiffre/nombre de bits à l'état `0` de votre masque de sous réseau.

Exemples :

10.0.0.0/8 soit 2^24 = 16 777 216 adresses utilisables
172.16.0.0/16 soit 2^16 = 65 536 adresses utilisables
192.168.1.0/24 soit 2^8 = 256 adresses utilisables  

#### Adresses disponibles

Le nombre d'adresses disponibles est le résultat du nombre d'adresses utilisable - 2.

Pourquoi le nombre d'adresses utilisable - 2 ?

`L'adresse de réseau` et `l'adresse de broadcast` sont tout simplement  **inutilisable**, elles ne sont pas attribuable à un équipement réseau et donc `non-disponible`.  
D'où la subtilité des mots `utilisables` et `disponibles`.

Exemples :

10.0.0.0/8 soit 2^24 - 2 = 16 777 214 adresses disponible  
172.16.0.0/16 soit 2^16 - 2 = 65 534 adresses disponible  
192.168.1.0/24 soit 2^8 - 2 = 254 adresses disponible

---

Enjoy 🎉
