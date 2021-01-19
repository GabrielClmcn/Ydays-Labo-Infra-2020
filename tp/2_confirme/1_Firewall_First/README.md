# Projet n°1 : Firewall First !
Ce projet à pour but de prendre en main un firewall en coeur de réseau. De nos jours, beaucoup d'entreprise utilise cette architecture, notamment pour les raisons cité dans le cours (cf. cours Firewall)

L'objectif est de vous présenter les différentes fonctionnalité qu'un firewall peut proposer.

- [0. Setup](#0-setup)
- [1. La partie Réseau](#0-setup)
- [2. Les règles de sécurité](#0-setup)
- [3. Le NAT](#0-setup)
- [4. Le VPN](#0-setup)
- [5. Optimisation](#0-setup)
- [6. Rendu](#0-setup)

## 0. Setup

- 1 x VM pfsense
- 1 x VM Linux
- 1 x VM Windows Client
- 1 x Réseau NAT
- 2 x Réseau interne
- 1 x Host-Only
- 1 x Réseau Bridge

La topologie est la suivant :
- Chaque élément (VM Windows et VM Linux est dans un réseau interne différents)
- Internet est le réseau NAT
- Les VMs auront la première IP disponible
- Le pfSense aura la dernière IP disponible

## 1. La partie réseau
- Chaque VM doit avoir une IP et pouvoir Pinger le pfsense
- Les VMs ne doivent pas se pinger entre elles ni sortir sur Internet sans passer par le pfsense
- Le pfSense doit avoir accès à Internet par le réseau INTERNET (réseau NAT)
- Le pfSense doit servir de serveur DHCP aux réseaux internes
- Le pfSense doit router les réseaux internes entre eux et les réseaux internes vers Internet
- La vm Linux doit héberger un service de FTP et un service Web

## 2. Les règles de sécurité
- Le Windows doit pouvoir pinger et utiliser les services du serveur Linux
- **[Bonus]** Faire du Web Filter pour le réseau windows. Les Windows doivent pouvoir surfer sur internet (sauf sur les sites pour adultes)

## 3. Le NAT
- Configurer un NAT Static pour que le serveur linux utilise une adresse du réseau Internet différente que le windows (S-NAT)
- Configurer un D-NAT pour publier les services du serveur Linux depuis le réseau Internet

## 4. Le VPN
- Configurez un VPN IPSec et interconnectez deux pfSense (le votre et celui de votre binome) soit avec un Bridge soit en 4G avec votre téléphone
- **[Bonus]** Configurer un VPN SSL avec un client OpenVPN afin d’avoir accès à l’administration de votre serveur linux depuis votre PC ou même Internet

## 5. Optimisation
- Configurer un Traffic Shaper (limitation de bande passante) sur le réseau Windows à destination d’internet, avec une Bande Passante max de 300ko/s
- **[Bonus]** Faire une deuxième VM pfSense et la mettre en HA avec la première
- **[Bonus]** Proposer/Mettre en place des optimisations que vous pensez utile.

## 6. Rendu
Présentation avec démonstration avec votre binôme.

Barème :

- Oral:
  - **Présentation /7**
    - Qualité du support /2
    - Gestion du temps /1
    - Posture professionnelle /1
    - Contenu /3
  - **Démonstration /5**
  - **Question-Réponse /8**

---

Enjoy 🎉
