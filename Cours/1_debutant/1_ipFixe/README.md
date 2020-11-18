# 1 L'adressage IP

## Sommaire

- **Internet Protocol**
  - **[2 versions](#2-versions)**
    - IPv4
    - Ipv6
  - **[3 types d'addresses](#2-types-daddresses)**
    - Publique
    - Privé
    - Localhost
- **Masque de sous-réseaux**
  - **[Quésaco ?](#quésaco-)**
  - Notation CIDR
  - **[Calcul de division en sous-réseau](#Calcul-de-division-en-sous-réseau)**
- **Adresse réseau**
  - **[Calcul d'une adresse réseau](#calcul-dune-adresse-réseau)**
- **Adresse de broadcast**
  - **[Quésaco encore ?](#quésaco-encore-)**
  - **[Calcul d'une adresse de broadcast](#calcul-dune-adresse-de-broadcast)**
- adresses utilisables
  - **[Calcul de la 1ère et dernière adresse disponible du réseau](#calcul-de-la-1ère-et-dernière-adresse-disponible-du-réseau)**
- adresses disponibles
  - **[Calcul du nombre total d'adresse et d'adresse disponible](#calcul-du-nombre-total-dadresse-et-dadresse-disponible)**

- **Pré-requis**
  - **[Calculer en binaire](#calculer-en-binaire)**
  - **[Méthode de conversion d'une ip en binaire](#méthode-de-conversion-dune-ip-en-binaire)**

---

## Pré-requis

### Calculer en binaire

1 + 1 = 1  
1 + 0 = 0  
0 + 1 = 0  
0 + 0 = 0  

### Méthode de conversion d'une ip en binaire

**Ip =** 192.168.0.1
**Bit =** 0 ou 1
**Octet =** Suite de huit 0 et/ou 1 ( ou dans sa forme non-binaire exemple: 192)

- Chaque adresse ip se compose de 32 bits.
- Composé en 4 parties, equivalentes à 1 octet chacune.

#### Pour convertir une ip en binaire il faut calculer les octets l'un après l'autre, en utilisant le tableau ci-dessous.

- :warning: Ce processus s'effectue un octet après l'autre. :warning: 
- Un octet est égale à la somme de certains des nombres du tableau.
- Soustraire le premier nombre du tableau avec notre octet, si le résultat est inférieur à 0, inscrivez un 0 puis passé au nombre suivant. Si le résultat est positif, inscrivez un 1 puis passer aux nombres suivant et répéter l'opération **avec le reste de la soustraction**.
- Une fois que **le reste est = 0**, tous les nombres suivant du tableau seront des 0.

|128|64 |32 |16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |   |

#### Exemple pour 192 et 168

192 = 128 + 64

|128|64 |32 |16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|
| 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |

168 = 128 + 32 + 8

|128|64 |32 |16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|
| 1 | 0 | 1 | 0 | 1 | 0 | 0 | 0 |

#### Résultat :
192.168 = 11000000.10101000

---
## Ip = Internet Protocol
### 2 versions

#### IPv4 
* Représenté par une série de **4 octets** sous forme de nombres entiers, allant **de 0 à 255**, séparé par des points. Pour un total de **32 bits**.
    * **Exemple :** 123.456.0.89

* On peut la décomposé en 2 partie :
    * La partie réseau commune à tous les hôtes d'un même réseau.
    **Exemple :** 123.456.0.\_\_ 
*(ou 123.456.\_\_.\_\_ selon le nombre d'adresses disponibles dans le réseau)*

    * La partie hôte, unique à l'intérieur d'un même réseau.
    **Exemple :** \_\_.\_\_.\_\_.89 
*(ou \_\_.\_\_.1.89 selon le nombre d'adresses disponibles dans le réseau)*

#### IPv6
* Représenté par une série de **8x 2octets** en héxadécimal, séparé par des deux-points. Pour un total de **128 bits**.
    * **Exemple :** 2001:0db8:0000:85a3:0000:0000:ac1f:8001 (ou 2001:db8:0:85a3:0:0:ac1f:8001)


### 2 types d'addresses

#### Adresse publique : 
* Unique dans le monde, elle permet d'être identifié sur internet.
    * **Exemple d'IPv4:** 77.210.126.42

#### Adresse privée :
* Unique dans son réseau, elle n'est utilisée que dans des réseaux privés.
    * **Exemple d'IPv4 :** 192.168.0.1 - 10.0.0.0 - 172.16.0.0

---

## Masque de sous-réseaux
### Quésaco ?

**192.168.0.1/20**
**Ip** = 192.168.0.1
**Masque (CIRD)** = /20
**Masque** = 255.255.240.0

Composé lui aussi de **32 bits**, il permet de spécifier **le nombre d'ip disponibles** dans le réseaux.

Le masque sous la forme de **"notion CIRD"** correspondant **au nombre de bits à l'état 1**, dans son écriture binaire.
**Exemple : /20 = 255.255.240.0 = 1111 1111.1111 1111.1111 0000.0000 0000**

**``
A savoir : Le 1er octet doit être supérieur ou égale au 2nd, qui lui même doit être   supérieur ou égale au 3ème, et ainsi de suite...
``**

---

## Adresse réseau
### Calcul d'une adresse réseau

**192.168.0.25/20**
**/20 =** 255.255.240.0

- Mettre en rapport l'ip et le masque.

>192.168.0.25
255.255.240.0


**````Astuce :````
````x + 255 = x````
````x + 0 = 0````
````x + y = ?````**

- Rechercher le/les inconnu.s (un octet après l'autre).

>192.168.0.25
255.255.240.0
**= 192.168.?.0**

- Mettre en corrélation l'octet de l'ip et l'octet du masque dont le résultat est inconnu puis  calculer la différence.

>240 = 1111 0000
>0 = 0000 0000
>**= 0000 0000 = 0**


:arrow_right: **L'adresse réseau est donc 192.168.0.0**

---

## Adresse de broadcast
### Quésaco encore ?

L'adresse de broadcast ou adresse de diffusion, est la dernière adresse d'un réseau ou d'un sous-réseau. Elle permet de vérifier la bonne communication entre tout les participants d'un réseau ou d'un sous-réseau, en leur envoyant des paquets.

### Calcul d'une adresse de broadcast

**Ip :** 192.168.0.25/20
**Adresse réseau :** 192.168.0.0
**Masque /20 :** 255.255.240.0

- Tous les bits à 0 dans le masque, passe à 1 dans l'adresse de réseau.

>255.255.240.0 = 1111 1111.1111 1111.1111 0000.0000 0000
>192.168.0.0 = 1100 0000.1010 1000.0000 0000.0000 0000
>**Résultat = 1100 0000.1010 1000.0000 1111.1111 1111**

:arrow_right: **L'adresse de broadcast est donc 192.168.15.255**

---
## Divers calculs
### Calcul de la 1ère et dernière adresse disponible du réseau

**Ip :** 192.168.0.25/20
**Adresse réseau :** 192.168.0.0
**Adresse de broadcast :** 192.168.15.255

- L'adresse de réseau et de broadcast ne sont pas disponible.
- L'adresse de réseau étant la première adresse du réseau, la première adresse disponible dans le réseau sera -> **adresse réseau + 1**.
- L'adresse de broadcast étant la dernière adresse du réseau, la dernière adresse disponible dans le réseau sera -> **adresse de broadcast - 1**.

:arrow_right: **1ère adresse disponible = 192.168.0.1**
:arrow_right: **Dernière adresse disponible = 192.168.15.254**

---
### Calcul du nombre total d'adresse et d'adresse disponible

**Masque :** /20 = 255.255.240.0 = 1111 1111.1111 1111.1111 0000.0000 0000

- Le nombre total d'adresse dans le réseau correspond à 2^ le nombre de 0 dans le masque, dans sa forme binaire.

>Il y a 12x 0 dans un masque /20
>**2^12 = 4096 adresses au total**

- Le nombre d'adresse disponible dans le réseau correspond au nombre total d'adresse dans le réseau -2. Puis que l'on retire l'adresse de réseau et de broadcast.

>**4096 - 2 = 4094 adresses disponibles**

---

### Calcul de division en sous-réseau

**Adresse réseau :** 192.168.0.0/24
**Adresse de broadcast :** 192.168.0.255
**Masque /24 :** 255.255.255.0

#### Comment diviser ce réseau en 4 ?

- En mettant en corrélation l'adresse réseau et l'adresse de broadcast, nous pouvons constater que la partie hôte de se réseau ne se concentre que sur le 4ème octet de l'adresse.
*(pour plus de clarté cet octet est représenté sous sa forme binaire)*

>192.168.0.**0000 0000**

- Afin de diviser en 4 ce réseau nous modifirons les 2 premiers bits de cet octet, en utilisant des combinaisons binaires.

>**Exemple :** **00**00 0000; **01**00 0000; **10**00 0000; **11**00 0000
>*(00; 01; 10; 11)*

- En ajoutant ces combinaisons nous obtenons 4 plages de sous-réseau, contenant des adresses disponibles, borner chacune par son adresse de sous-réseau et de broadcast.

>192.168.0.**00**00 0000 -> 192.168.0.**01**00 0000 -> 192.168.0.**10**00 0000 -> 192.168.0.**11**00 0000

***La 1ère plage allant de :***
>192.168.0.**00**00 0000 -> 192.168.0.**01**00 0000
192.168.0.**0** -> 192.168.0.**64 - 1**
192.168.0.**0** -> 192.168.0.**63**
(Adresse de réseau) -> (Adresse de broadcast)

***La 2ème plage allant de :***
>192.168.0.**01**00 0000 -> 192.168.0.**10**00 0000
192.168.0.**64** -> 192.168.0.**128 - 1**
192.168.0.**64** -> 192.168.0.**126**
(Adresse de réseau) -> (Adresse de broadcast)

***Et ainsi de suite jusqu'à la dernière adresse possible avec ce masque.***

**``
Si nous avions voulu diviser ce réseau en 5, nous aurions utiliser 3 bits, mais nous aurions perdu des adresses disponibles.
``**
