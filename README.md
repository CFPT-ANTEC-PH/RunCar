# Projet: RunCar Z

## Description du projet
La voiture **RunCar Z** sera conçue grâce à une imprimante 3D en fonction des pièces nécessaires et utilisera la technologie de MakeBlock. Le robot, une fois finalisé du point de vue mécanique, sera capable de se déplacer sur un suiveur de ligne programmé en Python. Un test avancé pourrait consister à optimiser sa vitesse de déplacement.

**Objectif à atteindre** (optionnel) : Faire en sorte que le robot puisse se déplacer dans une salle et détecter les obstacles.

---

## Historique
**Lundi 19 août 2024**

En 3e année au CFPT informatique, j'ai pu découvrir le **Picar S** déjà monté. Mon objectif était de faire en sorte que la voiture se déplace sur un suiveur de ligne, et j'ai réussi à accomplir cette tâche.

Dans ce premier cours de l'atelier "Nouvelle Technologie", je vais maintenant entamer le processus du nouveau projet pas à pas en effectuant un **testing**.

---

## Chapitre 1 : Installation de l'OS et mise en place

### Refaire en sorte que le Picar S se déplace sur un suiveur de ligne.

### Étape 1 : Installation de l'OS
1. Télécharger et installer l'image logicielle sur votre Raspberry Pi.
   - [Visitez la page de téléchargement](https://www.raspberrypi.org/software/).
   
2. Préparer le matériel nécessaire :
   - Voiture **Picar S**
   - **Raspberry Pi 4 Model B**
   - **Système d’exploitation : Raspberry Pi OS** (64 bits)
   - **Ordinateur personnel**
   - Carte microSD (réinitialisée sur Generic-SD/MMC USB Devices)

---
# Projet: RunCar Z

## Description du projet
La voiture **RunCar Z** sera conçue grâce à une imprimante 3D en fonction des pièces nécessaires et utilisera la technologie de MakeBlock. Le robot, une fois finalisé du point de vue mécanique, sera capable de se déplacer sur un suiveur de ligne programmé en Python. Un test avancé pourrait consister à optimiser sa vitesse de déplacement.

**Objectif à atteindre** (optionnel) : Faire en sorte que le robot puisse se déplacer dans une salle et détecter les obstacles.

---

## Historique
**Lundi 19 août 2024**

En 3e année au CFPT informatique, j'ai pu découvrir le **Picar S** déjà monté. Mon objectif était de faire en sorte que la voiture se déplace sur un suiveur de ligne, et j'ai réussi à accomplir cette tâche.

Dans ce premier cours de l'atelier "Nouvelle Technologie", je vais maintenant entamer le processus du nouveau projet pas à pas en effectuant un **testing**.

---

## Chapitre 1 : Installation de l'OS et mise en place

### Refaire en sorte que le Picar S se déplace sur un suiveur de ligne.

### Étape 1 : Installation de l'OS
1. Télécharger et installer l'image logicielle sur votre Raspberry Pi.
   - [Visitez la page de téléchargement](https://www.raspberrypi.org/software/).
   
2. Préparer le matériel nécessaire :
   - Voiture **Picar S**
   - **Raspberry Pi 4 Model B**
   - **Système d’exploitation : Raspberry Pi OS** (64 bits)
   - **Ordinateur personnel**
   - Carte microSD (réinitialisée sur Generic-SD/MMC USB Devices)

---

## Chapitre 2 : Obtenir l'adresse IP

Après avoir alimenté le Raspberry Pi, il est nécessaire d'obtenir son adresse IP pour pouvoir se connecter à distance. Voici les étapes suivies :

1. Alimenter le Raspberry Pi installé dans la voiture.
2. Utiliser la commande suivante pour afficher les informations réseau :
   ```bash
   ip a
![Texte alternatif]()


