# Minitalk
[![GitHub top language](https://img.shields.io/github/languages/top/efinicke/minitalk)](https://github.com/efinicke/minitalk)

## Skills

- **Programming in C**
- **UNIX Signal Handling**
- **Inter-process Communication**
- **Error Handling**
- **Makefile Scripting**

## Project Overview

Minitalk est un projet que j'ai réalisé pour approfondir ma compréhension des signaux UNIX et de la communication inter-processus. En développant un serveur et un client minimal en C, j'ai pu étudier le fonctionnement des signaux SIGUSR1 et SIGUSR2 et les utiliser pour transmettre une chaîne de caractères du client au serveur. Les signaux n'étant qu'une somme de bits dont la valeur ne peut dépasser 0 ou 1, un caractère n'étant qu'une suite de 8 bits, le client envoie les bits de la chaîne transmise en argument un par un au serveur qui reconstitue ensuite le message lettre par lettre pour l'afficher directement sur la sortie standard, ainsi le message doit être récupéré entièrement sans perte de signal, la perte d'un seul bit fausserait la suite du message. 


## Features

- **Signal-based Communication**: Utilisation des signaux SIGUSR1 et SIGUSR2 pour la communication de la chaine de caractères.
- **multi-clients**: Possibilité de recevoir des messages de plusieurs clients successivement sans nécessité de redémarrage.

## Content

- **client.c**: Contains the client-side code for sending messages to the server.
- **server.c**: Implements the server-side logic for receiving and displaying messages from clients.
- **libft**: Our custom library.
- **minitalk.h**: Header file defining function prototypes.

## utils 

**signal et sigaction** : Configurés pour gérer les signaux SIGUSR1 et SIGUSR2.
**kill** : Utilisé pour envoyer des signaux d'un processus à un autre.
**getpid** : Utilisé pour obtenir le PID du processus serveur.
**pause** : Utilisé pour mettre en attente le processus jusqu'à la réception d'un signal.
**usleep** : Introduit un léger délai entre l'envoi des signaux.
**exit** : Utilisé pour terminer proprement le programme en cas d'erreur.

## Usage

1. Compilation:

Utiliser le Makefile pour compiler le projet :

```bash
make
```

2. Execution:

- Lancer le serveur en premier :

```bash
./server
```

Le serveur affiche son PID (Process Identifier).

- Ouvrir un autre terminal et lancer le client avec le PID serveur et le message à lui transmettre :

```bash
./client <server_pid> "Message to send"
```

Pour envoyer un fichier texte plus conséquent envoyer directement le contenu d'un fichier .txt avec cette ligne de commande :

```bash
./client <server_pid> "$(cat testfile.txt)"
```
Si les choses se sont passées comme souhaitées, le message a été envoyé au serveur et s'affiche sur la sortie standard. 
