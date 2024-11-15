#### Introduction

Wapiti est un scanner de vulnérabilités qui analyse les applications web pour détecter les failles de sécurité telles que les injections SQL, les scripts inter-sites (XSS), les failles de redirection, et bien plus. Il fonctionne en explorant les pages web et en testant les points d'entrée pour identifier les vulnérabilités.

#### Installation de Wapiti

**1. Installation sur Linux**

1.  **Installer les dépendances** :

    ```bash
    sudo apt update
    sudo apt install python3 python3-pip
    ```

    * **Explication** :
      * `sudo apt update` : Met à jour la liste des paquets disponibles.
      * `sudo apt install python3 python3-pip` : Installe Python3 et pip3, le gestionnaire de paquets Python.
2.  **Installer Wapiti via pip** :

    ```bash
    pip3 install wapiti3
    ```

    * **Explication** :
      * `pip3 install wapiti3` : Installe Wapiti via pip3.
3.  **Vérifier l'installation** :

    ```bash
    wapiti --help
    ```

    * **Explication** : Vérifie que Wapiti est installé correctement.

**3. Installation sur Windows**

1. **Télécharger et installer Python depuis le** [**site officiel de Python**](https://www.python.org/downloads/).
   * **Explication** : Téléchargez et installez Python en suivant les instructions à l'écran.
2.  **Installer Wapiti via pip** :

    ```bash
    pip install wapiti3
    ```

#### Utilisation de Base

**1. Scan d'un Site Web**

1.  **Commandement de base pour scanner un site web** :

    ```bash
    wapiti -u http://example.com
    ```

    * **Explication** :
      * `-u` : Spécifie l'URL du site web à scanner.
      * `http://example.com` : URL de l'application web cible.
    * **Discrétion** : Moyenne à élevée. L'analyse d'un site web peut être détectée par les mécanismes de sécurité du site.

**2. Génération d'un Rapport**

1.  **Générer un rapport au format HTML** :

    ```bash
    wapiti -u http://example.com -f html -o rapport.html
    ```

    * **Explication** :
      * `-f html` : Spécifie le format du rapport (HTML dans ce cas).
      * `-o rapport.html` : Spécifie le fichier de sortie pour le rapport.
    * **Discrétion** : Moyenne. Les rapports générés peuvent contenir des informations sensibles sur la sécurité du site.

**3. Limiter la Profondeur du Scan**

1.  **Définir la profondeur maximale du scan** :

    ```bash
    wapiti -u http://example.com --depth 2
    ```

    * **Explication** :
      * `--depth 2` : Limite la profondeur de l'exploration à 2 niveaux de liens.
    * **Discrétion** : Moyenne. Limiter la profondeur réduit le nombre de requêtes, diminuant ainsi la visibilité.

#### Options Avancées

**1. Utilisation d'un Proxy**

1.  **Configurer un proxy pour le scan** :

    ```bash
    wapiti -u http://example.com --proxy http://localhost:8080
    ```

    * **Explication** :
      * `--proxy` : Permet d'utiliser un serveur proxy pour le scan.
    * **Discrétion** : Moyenne. Utiliser un proxy peut masquer l'origine des requêtes mais peut également être détecté.

**2. Configurer des Paramètres de Connexion**

1.  **Définir un User-Agent personnalisé et des cookies** :

    ```bash
    wapiti -u http://example.com --user-agent "Mozilla/5.0" --cookies "cookie1=value1; cookie2=value2"
    ```

    * **Explication** :
      * `--user-agent` : Définit le User-Agent utilisé pour les requêtes HTTP.
      * `--cookies` : Spécifie les cookies à utiliser pour accéder à des zones protégées.
    * **Discrétion** : Moyenne. Les paramètres de connexion personnalisés peuvent influencer la manière dont le scan est détecté.

**3. Exclure des Paramètres de Scan**

1.  **Exclure certains paramètres d'URL du scan** :

    ```bash
    wapiti -u http://example.com --ignore-parameters "param1,param2"
    ```

    * **Explication** :
      * `--ignore-parameters` : Permet d'exclure des paramètres spécifiques des tests de vulnérabilités.
    * **Discrétion** : Moyenne. Éviter certains paramètres peut aider à réduire la charge et les alertes.

#### Exemples de Commandes

**1. Scanner un Site Web avec Rapport HTML**

1.  **Commande pour scanner et générer un rapport** :

    ```bash
    wapiti -u http://example.com -f html -o rapport.html
    ```

**2. Scanner avec Proxy et Profondeur Limité**

1.  **Commande pour scanner avec un proxy et une profondeur maximale de 2** :

    ```bash
    wapiti -u http://example.com --proxy http://localhost:8080 --depth 2
    ```

#### Discrétion

**Discrétion** : Moyenne à faible. Le scan peut être détecté par les systèmes de surveillance du réseau ou les mécanismes de protection des applications web, surtout si le scan est intensif ou si un grand nombre de requêtes est envoyé en peu de temps. Assurez-vous d'obtenir les autorisations nécessaires avant de scanner des sites web en production.
