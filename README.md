# SOC-5A
Projet de supervision SOC (BUILD/RUN)
[Google docs: notes SOC 5A](https://docs.google.com/document/d/1h8ktuoaQ3gKiuQtx2Pn_YqQZQQc3w49z9bwUGT6n8UU/edit?tab=t.0)
# Politique de supervision des serveurs linux 
Le client utilise une politique de supervision basée sur [Kunai](https://github.com/kunai-project/kunai) pour la détection des activités système sur les serveurs Linux. Afin de tester nos règles et de remontée d’alertes, `une VM Debian 13` a été intégrée dans l’environnement de test.  

> Kunai est un outil de supervision et de détection s’appuyant sur eBPF pour capturer en temps réel des événements tels que l’exécution de processus, la création ou modification de fichiers, certaines opérations réseau et l’activité au niveau des containers. Il permet ainsi de remonter une visibilité fine sur les actions réellement exécutées sur le système.

>Kunai présente toutefois certaines limites : les commandes internes à Bash (par exemple cd, export, alias) ne sont pas détectées puisqu’elles ne génèrent pas de processus, et certaines opérations d’entrée/sortie réalisées via io_uring peuvent échapper à la surveillance lorsqu’elles ne déclenchent pas les syscalls traditionnels.

# Nos régles 
## Linux 
### Multiple commandes d'énumération 
### Activité de password looting 
## Réseau
### Scan de port vértical
Identifier une source (IP ou machine) qui tente de se connecter à plusieurs ports différents sur un même hôte cible dans une fenêtre de temps courte.
C’est typiquement un comportement de reconnaissance visant à identifier tous les services ouverts d’une machine avant une attaque.
```
nmap -p 1-1000 192.168.179.172
```
### Scan de port horizontal 
Identifier une source (IP ou machine) qui tente de se connecter au même port sur plusieurs hôtes dans une fenêtre de temps courte.
C’est typiquement un comportement de reconnaissance pour détecter quels hôtes sont actifs ou vulnérables sur un service donné.

```
nmap -p 22 192.168.179.0/24
```
### Activité de beaconing CnC
