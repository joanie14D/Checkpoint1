# CHECKPOINT 1

## 1.1 ÉLÉMENTS DU RÉSEAU - QUIZZ

1. Le symbole A représente le commutateur (switch).
2. Le switch permet de relier plusieurs segments entre eux d’un réseau informatique. Il se situe sur la couche 2 du modèle OSI, il gère les adresses MAC.
3. Le matériel B qui est un routeur est un dispositif d’interconnexion de réseau, il permet le routage des paquets entre deux réseaux. La différence avec le switch c’est qu’il agit sur la couche 3 du modèle OSI et gère les adresses IP.
4. e0, e2,  e3 représente l'interface du port Ethernet du routeur.
5. f0/0 sur l’élément B signifie l'interface du port FastEthernet.
6. /16 signifie le CIDR de l’adresse IP, c’est le masque de sous réseau de l’adresse, il permet d’identifier quelle est la partie réseau et quelle est la partie machine de l’adresse IP.
7. 10.10.255.254/16 est l'adresse IPv4 de la Passerelle.
8. Dans le vocabulaire IP, PC1, PC2 etc, sont des noeuds, c’est à dire des équipements supportant IP.
9. Pour A c’est un hôte, et pour B c’est un routeur donc un noeud qui transmet les paquets dont il n’est pas destinataire.
10. Le trait rouge représente un câble réseau.

## 1.2 Etude théorique

11. **PC1 : 10.10.4.1/16** Adresse de réseau : 10.10.0.0/16

   Adresse de diffusion : 10.10.255.255

   Début de plage : 10.10.0.1

   Fin de plage : 10.10.255.254

   **PC2 : 10.11.80.2/16**

   Adresse de réseau : 10.11.0.0/16

   Adresse de diffusion : 10.11.255.255

   Début de plage : 10.11.0.1

   Fin de plage : 10.10.255.254

   **PC3 : 10.10.80.3/16**

   Adresse de réseau : 10.10.0.0/16

   Adresse de diffusion : 10.10.255.255

   Début de plage : 10.10.0.1

   Fin de plage : 10.10.255.253

   **PC4 : 10.10.4.2/16**

   Adresse de réseau : 10.10.0.0/16

   Adresse de diffusion : 10.10.255.255

   Début de plage : 10.10.0.1

   Fin de plage : 10.10.255.254

1. PC1 PC3 & PC4 peuvent communiquer entre elles car elles sont sur la même adresse réseau 10.10.0.0/16
2. PC1 PC3 et PC4 peuvent sortir du réseau car ils ont une adresse passerelle, qui est l’adresse du routeur
3. Ça ne change rien.
4. Oui il faut ajouter un serveur DHCP qui fournira un paramètrage dynamique aux hôtes du réseau.

### 1.3 Analyse de trames

**Fichier 1**

16. l'IP qui initialise la communication est 10.10.4.1.
17. Oui la communication à fonctionné entre 10.10.4.1 & 10.10.4.2 car on remarque que le ping à répondu.
18. Le request et le reply est la question et la réponse, cela correspond à la commande ping, qui permet de vérifier si deux équipements communiquent entre eux.
19. Le rôle de A est de faire la commutation et B ne sert pas .

**Fichier 2**

20. Dans cette trame, l'IP qui initialise la communication est 10.10.80.3.
21. Non la communication n’a pas réussi, on remarque que le ping n’a pas fonctionné, on en déduit que les deux équipements ne sont pas sur le même masque de sous réseau.
22. A fait de la commutation - B à essayé de faire du routage mais comme il ne connait pas le réseau, il n’y arrive pas.

**Fichier 3**

23. Celui qui initialise la communication est le PC 3 donc 10.10.80.3.
24. Non la communication n’a pas réussi, le ping request a échoué.
25. Le routeur joue le rôle de gateway et le switch joue le rôle de répéteur de signal.
26. Les différents protocoles encapsulés sont détaillés dans la colonne « Protocol » on y retrouve donc, CDP - ARP (adress résolution protocol) - ICMP (internet message protocol).

## 2. SCRIPTING

#### Version avec interaction utilisateur

\#!/bin/bash

echo "Vous devez rentrer successivement les informations suivantes : Nom du PC, adresse mac, addresse IP :"

read pc addmac addip

echo $pc $addmac $addip >> configurationReseau.txt

echo -e "\nMerci d'avoir entrer les informations suivantes :\nNom du PC    : $pc\nAddresse MAC : $addmac\nAddresse IP  : $addip"

exit 0

### Version avec arguments

\#!/bin/bash

echo "$1 $2 $3" >> configurationReseau.txt

echo -e "\nMerci d'avoir entrer les informations suivantes :\nNom du PC    : $1\nAddresse MAC : $2\nAddresse IP  : $3"

exit 0
