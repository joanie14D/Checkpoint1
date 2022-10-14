# CHECKPOINT 1

## 1.1 ÉLÉMENTS DU RÉSEAU - QUIZZ

1. Le symbole A représente le commutateur (switch).
2. Le switch permet de relier plusieurs segments entre eux d’un réseau informatique. Il se situe sur la couche 2 du modèle OSI, il gère les adresses MAC.
3. Le matériel B qui est un routeur est un dispositif d’interconnexion de réseau, il permet le routage des paquets entre deux réseaux. La différence avec le switch c’est qu’il agit sur la couche 3 du modèle OSI et gère les adresses IP.
4. e0, e2,  e3 représente l'interface du port Ethernet du routeur
5. f0/0 sur l’élément B signifie l'interface du port FastEthernet
6. /16 signifie le CIDR de l’adresse IP, c’est le masque de sous réseau de l’adresse, il permet d’identifier quelle est la partie réseau et quelle est la partie machine de l’adresse IP.
7. 10.10.255.254/16 est l'adresse IPv4 du réseau
8. Dans le vocabulaire IP, PC1, PC2 etc, sont des noeuds, c’est à dire des équipements supportant IP.
9. Pour A c’est un hôte, et pour B c’est un routeur donc un noeud qui transmet les paquets dont il n’est pas destinataire.
10. Le trait rouge représente la liaison physique ou virtuel des ports entre les équipements.

## 1.2 Etude théorique

11. **PC1 : 10.10.4.1/16** Adresse de réseau : 10.10.0.0/16

   Adresse de diffusion : 10.10.255.255

   Début de plage : 10.10.0.1

   Fin de plage : 10.10.255.253

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

1. PC1 PC3 & PC4 peuvent communiquer entre elles car elles ont la même adresse de diffusion.
2. PC1 PC3 et PC4 peuvent sortir du réseau car ils ont une adresse passerelle, qui est l’adresse du routeur
3. Il faut reconfigurer le port des équipements pour établir un design correct du réseau.
4. Oui il faut ajouter un serveur DHCP qui fournira un paramètrage dynamique aux hôtes du réseau.

### 1.3 Analyse de trames

**Fichier 1**

16. l'IP qui initialise la communication est 10.10.4.1
17. Oui la communication à fonctionné entre 10.10.4.1 & 10.10.4.2 car on remarque que le ping à répondu.
18. Le request et le reply est la question et la réponse, cela correspond à la commande ping, qui permet de vérifier si deux équipements communiquent entre eux.
19. Le rôle de A & B est d’assurer la transmission des paquets. Le rôle du switch est de répéter le signal d’une machine pour connaitre l’adresse MAC de 10.10.4.2 et le routeur se réfère à la table de routage.

**Fichier 2**

20. Dans cette trame, l'IP qui initialise la communication est 10.10.80.3
21. Non la communication n’a pas réussi, on remarque que le ping n’a pas fonctionné, on en déduit que les deux équipements ne sont pas sur le même masque de sous réseau.
22. Ils ont joués un role différent car il n’y a pas eu de demande d’identification.

**Fichier 3**

23. Celui qui initialise la communication est le PC 3 donc 10.10.80.3
24. Non la communication n’a pas réussi, le ping request a échoué.
25. A et B ont joués un rôle différent car il n’y a pas eu de demande d’identification.
26. Les différents protocoles encapsulés sont détaillés dans la colonne « Protocol » on y retrouve donc, CDP - ARP (adress résolution protocol) - ICMP (internet message protocol).

## 2. SCRIPTING

#### 2.1 Version avec interaction utilisateur

\#!/bin/bash

read -p "Vous devez rentrer les informations suivantes : Nom du PC, adresse MAC, addresse IP : " Nom AdresseMac AdresseIp

echo "merci d'avoir entré les informations suivantes :"

echo "Nom du Pc : " $Nom

echo "Addresse Mac :" $AdresseMac

echo "Addresse IP : " $AdressIp

echo $Nom> configurationReseauNom.txt

echo $AdressMac > configurationReseauMac.txt

echo $AdressIp > configurationReseauIp.txt

cat configurationReseauNom.txt configurationReseauMac.txt configurationReseauIp.txt > configurationReseau.txt

rm configurationReseauNom.txt

rm configurationReseauMac.txt

rm configurationReseauIp.txt

