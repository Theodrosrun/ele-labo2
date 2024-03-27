<img src="heig-vd.png" style="height:80px;">


# <center> Laboratoire n°02

# <center> Limites de Linux dans un contexte temps réel



## <center>Département : TIC

## <center>Unité d'enseignement ELE


Auteur:     **Theodros Mulugeta, Colin Jacque, Alexandre Iorio**

Professeur: **Bertrand Hochet**

Assistant : **-**

Salle de labo : **B03**
Date : **13.03.2024**

<!-- pagebreak -->

## 1. Introduction

Dans ce laboratoire, nous allons visualiser à l'oscilloscope des trames binaires dans des communications sérielles UART et SPI. Nous mettrons en évidence les limites de débit physiques en fonction de la qualité des interconnexions. Les essais de communication seront effectués au moyen de deux câbles différents. Un rapport sera à remettre à la fin de la dernière séance dédiée à ce laboratoire, dont la date sera précisée ultérieurement.

## 2.

### 2.1 Matériel et branchement

Nous disposons de deux cartes de développement NUCLEO-U575ZI-Q pour des microcontrôleurs modernes (STM32U5). Chacune des cartes est programmée pour permettre de mettre en œuvre une communication sérielle. Nous avons monté des barrettes à 3 et 4 broches (headers) respectivement sur les accès [PA2, PA3, GND] et [GND, PA5, PA6, PA7].

### 2.2 Configurations

Les commandes suivantes ont été utilisées pour configurer les ports série sur les deux cartes de développement.


|                      | carte émettrice  | carte réceptrice |
| -------------------- | --------------- | ---------------- |
| PORT COM             | COM 10          | COM 11           |
| Position sur l'image | haut            | bas              |
| Interface            | interface=uart  | interface=uart   |
| direction            | dir=TX          | dir=RX           |
| baud                 | baudrate=115200 | baudrate=115200  |
| interval             | interval=100    | -                |
| data                 | data=hello      | -                |
| start                | start           | start            |
|                      |                 |                  |

Test de la communication série entre les deux cartes de développement.

@import "cartes.jpg"



@import "testcomm.png"


### 2.3 Branchement oscilloscope    

Nous avons branché l'oscilloscope sur les ports série des deux cartes de développement. Les deux cartes sont alimentées par le port USB de l'ordinateur.

@import "branchement.jpg"
@import "branchement2.jpg"
@import "branchement3.jpg"





### 3 Analyse des résultats UART

### 3.1 Analyse des signaux UART avec un câble de 25cm

Nous avons réalisé les tests suivants avec un câble de 25cm.

À une fréquence de 115'200 bauds, nous pouvons voir que le signal est bien transmis et reçu par les deux cartes de développement. Le signal est quasiment identique sur les deux cartes de développement.

**115'200 bauds**    
@import "TEK00001.PNG"



À une fréquence de 10'000'000 bauds, nous pouvons voir que le signal transmis subi des déformations directement sur la carte émettrice cependant
 est bien transmis et reçu par les deux cartes de développement. Le signal reçu diverge du signal émis en raison de la résonance créée par l'inductance du câble.

Le données transmises sont quant à elles bien reçues par la carte réceptrice.

**10'000'000 bauds**
@import "TEK00002.PNG"



### 3.2 Analyse des signaux UART avec un câble de 1m

Les mêmes tests ont été réalisés avec un câble de 1m.

À une fréquence de 115'200 bauds, nous pouvons voir que le signal est bien transmis et reçu par les deux cartes de développement. Le signal est quasiment identique sur les deux cartes de développement.

**115'200 bauds**
@import "TEK00004.PNG"

À une fréquence de 10'000'000 bauds, nous pouvons voir que le signal est envoyé est envoyé par la carte émettrice subit des déformations, 

**10'000'000 bauds**
@import "TEK00003.PNG"


### 4 Analyse des résultats LPUART

### 4.1 Analyse des signaux LPUART avec un câble de 25cm

Les analyses des signaux LPUART ont été effectuées avec un câble de 25cm et les résultats suivants ont été obtenus.

Avec une fréquence de 115'200 bauds à 40'000'000 bauds, les signaux sont bien transmis et reçus par les deux cartes de développement. Les signaux sont subissent des déformations lors des augmentations de fréquence.

À partir de 53'000'000 bauds, la communication ne fonctionne plus et les signaux n'ont plus de signification.


### 4.2 Analyse des signaux LPUART avec un câble de 1m

115'200 bauds
@import "TEK00007.PNG"

10'000'000 bauds
@import "TEK00006.PNG"

20'000'000 bauds
@import "TEK00009.PNG"

32'000'000 bauds
@import "TEK00010.PNG"

40'000'000 bauds sans retirer l'oscilloscope
@import "TEK00008.PNG"
@import "baud40m_lpuart.png"

40'000'000 bauds en retirant l'oscilloscope
La communication ne fonctionne toujours pas


40'000'000 petits câbles oscille branché
@import "TEK00011.PNG"

53'000'000 bauds
@import "TEK00012.PNG"
@import "baud53m_lpuart.png"

# 5.1 Analyse des signaux SPI
L'analyse des signaux SPI n'a pas été effectuée étant donné que les valeurs n'auraient pas été plus intéressantes que les analyses LPUART et UART.




