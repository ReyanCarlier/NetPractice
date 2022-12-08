# NetPractice

Introduction
============

Pour ce projet, nous n'utiliserons que de l'IPv4, donc nous n'aborderons pas l'IPv6.
Une adresse IPv4 est un nombre de 32bits divisé en 4 blocs de 8 bits.

Exemple :
---------

`192.168.100.1` => `11000000.10101000.01100100.00000001`
Donc la valeur minimale d'un bloc est `0` et la valeur maximale est `255`.

Cette logique s'applique aussi aux masques réseau :
`255.255.255.0` => `11111111.11111111.11111111.00000000`

La différence pour les masques réseau est qu'après un bit `0`, il ne peut y avoir que des `0`.
- 255 `(binary: 11111111)`
- 254 `(binary: 11111110)`
- 252 `(binary: 11111100)`
- 248 `(binary: 11111000)`
- 240 `(binary: 11110000)`
- 224 `(binary: 11100000)`
- 192 `(binary: 11000000)`
- 128 `(binary: 10000000)`
- 0 `(binary: 00000000)`
Le masque `255.255.255.0` est valide, mais `255.255.128.128` ne l'est pas.

Afin de pouvoir envoyer des données entre deux adresses IP, il faut soit qu'elles appartiennent au même réseau, soit qu'elles soient connectés à un routeur appartenant à leurs sous-réseaux respectifs.

Plages d'IP spéciales
=====================

Les plages d'IP suivantes sont réservées aux Réseaux Privés :
- 10.0.X.X
- 172.16.X.X
- 192.168.X.X

La plage d'IP suivante est réservée aux IP dites de bouclage :
- 127.0.0.1

Masques
=======

Le "masque réseau", "masque sous-réseau" ou "masque" dans notre projet, permet de déterminer quelle plage d'adresses IP appartiennent au même sous-réseau (subnet).
Il y a deux manières d'écrire un masque :
- Notation point-décimale : `255.255.255.0`
- Routage inter-domaines par classe (RIDC) : `/24`

Au plus nous avons besoin d'adresse IP distinctes au sein d'un même sous-réseau, au moins il nous sera possible de créer de sous-réseaux.

| RIDC | Point-décimale | Nombre d'adresse<br /> par subnet | IP utilisables <br /> par subnet | Nombre de subnets |
| :---: | :-----------: | :---: | :---: | :---: |
| /32 | 255.255.255.255 | 1 | 0 | 256 |
| /31 | 255.255.255.254 | 2 | 0 | 128 |
| /30 | 255.255.255.252 | 4 | 2 | 64 |
| /29 | 255.255.255.248 | 8 | 6 | 32 |
| /28 | 255.255.255.240 | 16 | 14 | 16 |
| /27 | 255.255.255.224 | 32 | 30 | 8 |
| /26 | 255.255.255.192 | 64 | 62 | 4 |
| /25 | 255.255.255.128 | 128 | 126 | 2 |
| /24 | 255.255.255.0 | 256 | 254 | 1 |

Le nombre d'adresse IP utilisable par subnet est inférieure au nombre total d'IP car la première adresse est réservée en tant qu'adresse du sous-réseau et la dernière est utilisée comme adresse de diffusion.

Exemple :
---------

Masque : `255.255.255.252`
Réseau : `190.3.2.252`
Diffusion : `190.3.2.255`
Adresses utilisables : `190.3.2.253` à `190.3.2.254`


