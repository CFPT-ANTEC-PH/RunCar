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

# Étape 2 : Activer le serveur VNC sur le Raspberry Pi

1. **Ouvrir les paramètres de configuration du Raspberry Pi :**
   - Entrez la commande suivante pour ouvrir la configuration du Raspberry Pi :
     ```bash
     sudo raspi-config
     ```
   
2. **Accéder au menu Interface Options et sélectionner VNC :**
   - Activez le serveur VNC.

3. **Ouvrir l'application VNC et rechercher l'IP du Raspberry Pi :**
   - L'identifiant et le mot de passe vous seront demandés.
   - admin et Super sont les identifiants
   - Une fois connecté, l'interface graphique du Raspberry Pi devrait s'afficher dans le client VNC, vous permettant de contrôler le Raspberry Pi à distance comme si vous utilisiez un écran directement connecté.

---

## Chapitre 3 - 7 octobre

Avant d’implémenter le code du suiveur de ligne, il a été nécessaire de mettre en place un tableau de vérité pour identifier les conditions du bon déroulement de la voiture sur le suiveur de ligne.

---

## Chapitre 4 - 14 octobre au 11 novembre : Configuration et tests du suiveur de ligne

> Pendant ces semaines, j’ai rencontré quelques problèmes techniques au niveau du `runCar`, et je me suis focalisé sur l’implémentation d’une structure de code pour le bon déroulement du suiveur de ligne.

### Étape 1 : Préparer le capteur de ligne

- Pour que la voiture RunCar Z puisse suivre une ligne, il est nécessaire d'utiliser un capteur de ligne. Ce capteur peut être installé en utilisant des modules infrarouges qui détectent la présence d'une ligne noire sur un fond blanc.
- Connecter le capteur de ligne au Raspberry Pi via les ports GPIO sur la voiture.
- Installer les bibliothèques nécessaires pour utiliser le capteur avec Python. Une bibliothèque couramment utilisée pour interfacer avec les GPIO de Raspberry Pi est `RPi.GPIO`.

### Étape 2 : Programmation du suiveur de ligne

- Une fois le capteur de ligne installé et connecté, il est temps de tester le code du robot pour qu'il puisse suivre la ligne. Voici un exemple simple de code Python pour ce faire :
  
  ```python
  # Todo code
  ```
  ### Étape 3 : Test du suiveur de ligne
 - Ouvrir un terminal et vous rendre dans le répertoire du fichier qui contient le fichier de démarrage du programme :
   ```bash
   python nom_du_programme.py
   ```
  
