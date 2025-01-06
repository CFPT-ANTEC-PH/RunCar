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

## Étape 2 : Programmation du suiveur de ligne

Une fois le capteur de ligne installé et connecté, il est temps de comprendre comment fonctionne le script de `line_follower` fourni par Sunfounder. Ce script est déjà configuré pour contrôler le déplacement du robot en suivant une ligne.

### Code :
```python
#!/usr/bin/env python

'''
**********************************************************************
* Filename    : line_follower
* Description : An example for sensor car kit to follow line
* Author      : Dream
* Brand       : SunFounder
* E-mail      : service@sunfounder.com
* Website     : www.sunfounder.com
* Update      : Dream    2016-09-21    New release
**********************************************************************
'''

from SunFounder_Line_Follower import Line_Follower
from picar import front_wheels
from picar import back_wheels
import time
import picar

picar.setup()

REFERENCES = [200, 200, 200, 200, 200]
# calibrate = True
calibrate = False

forward_speed = 80
backward_speed = 70
turning_angle = 40

max_off_track_count = 40
delay = 0.0005

fw = front_wheels.Front_Wheels(db='config')
bw = back_wheels.Back_Wheels(db='config')
lf = Line_Follower.Line_Follower()

lf.references = REFERENCES
fw.ready()
bw.ready()
fw.turning_max = 45

def straight_run():
    while True:
        bw.speed = 70
        bw.forward()
        fw.turn_straight()

def setup():
    if calibrate:
        cali()

def main():
    global turning_angle
    off_track_count = 0
    bw.speed = forward_speed

    a_step = 3
    b_step = 10
    c_step = 30
    d_step = 45

    bw.forward()
    while True:
        lt_status_now = lf.read_digital()
        print(lt_status_now)

        # Angle calculate
        if lt_status_now == [0, 0, 1, 0, 0]:
            step = 0    
        elif lt_status_now == [0, 1, 1, 0, 0] or lt_status_now == [0, 0, 1, 1, 0]:
            step = a_step
        elif lt_status_now == [0, 1, 0, 0, 0] or lt_status_now == [0, 0, 0, 1, 0]:
            step = b_step
        elif lt_status_now == [1, 1, 0, 0, 0] or lt_status_now == [0, 0, 0, 1, 1]:
            step = c_step
        elif lt_status_now == [1, 0, 0, 0, 0] or lt_status_now == [0, 0, 0, 0, 1]:
            step = d_step

        # Direction calculate
        if lt_status_now == [0, 0, 1, 0, 0]:
            off_track_count = 0
            fw.turn(90)
        elif lt_status_now in ([0, 1, 1, 0, 0], [0, 1, 0, 0, 0], [1, 1, 0, 0, 0], [1, 0, 0, 0, 0]):
            off_track_count = 0
            turning_angle = int(90 - step)
        elif lt_status_now in ([0, 0, 1, 1, 0], [0, 0, 0, 1, 0], [0, 0, 0, 1, 1], [0, 0, 0, 0, 1]):
            off_track_count = 0
            turning_angle = int(90 + step)
        elif lt_status_now == [0, 0, 0, 0, 0]:
            off_track_count += 1
            if off_track_count > max_off_track_count:
                tmp_angle = (turning_angle - 90) / abs(90 - turning_angle)
                tmp_angle *= fw.turning_max
                bw.speed = backward_speed
                bw.backward()
                fw.turn(tmp_angle)
                lf.wait_tile_center()
                bw.stop()

                fw.turn(turning_angle)
                time.sleep(0.2)
                bw.speed = forward_speed
                bw.forward()
                time.sleep(0.2)
        else:
            off_track_count = 0

        fw.turn(turning_angle)
        time.sleep(delay)

def cali():
    references = [0, 0, 0, 0, 0]
    print("cali for module:\n  first put all sensors on white, then put all sensors on black")
    mount = 100
    fw.turn(70)
    print("\n cali white")
    time.sleep(4)
    fw.turn(90)
    white_references = lf.get_average(mount)
    fw.turn(95)
    time.sleep(0.5)
    fw.turn(85)
    time.sleep(0.5)
    fw.turn(90)
    time.sleep(1)

    fw.turn(110)
    print("\n cali black")
    time.sleep(4)
    fw.turn(90)
    black_references = lf.get_average(mount)
    fw.turn(95)
    time.sleep(0.5)
    fw.turn(85)
    time.sleep(0.5)
    fw.turn(90)
    time.sleep(1)

    for i in range(0, 5):
        references[i] = (white_references[i] + black_references[i]) / 2
    lf.references = references
    print("Middle references =", references)
    time.sleep(1)

def destroy():
    bw.stop()
    fw.turn(90)

if __name__ == '__main__':
    try:
        try:
            while True:
                setup()
                main()
        except Exception as e:
            print(e)
            print('error try again in 5')
            destroy()
            time.sleep(5)
    except KeyboardInterrupt:
        destroy()
```
  ### Étape 3 : Test du suiveur de ligne
 - Ouvrir un terminal et vous rendre dans le répertoire du fichier qui contient le fichier de démarrage du programme :
   ```bash
   python nom_du_programme.py
   ```
  
