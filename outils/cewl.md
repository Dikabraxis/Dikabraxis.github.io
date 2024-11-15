---
layout: default
title: "Cewl"
---

#### Introduction

Cewl est un outil Ruby conçu pour créer des dictionnaires personnalisés en analysant le contenu HTML d'un site web. Il peut extraire des mots et des phrases du contenu des pages web pour générer des listes de mots qui peuvent être utilisées pour les attaques par dictionnaire.

#### Installation de Cewl

**Installation sur Linux**

1.  **Installer Ruby (si ce n’est pas déjà fait)** :

    ```bash
    sudo apt update
    sudo apt install ruby
    ```

    * **Explication** :
      * `sudo apt update` : Met à jour la liste des paquets disponibles.
      * `sudo apt install ruby` : Installe Ruby via le gestionnaire de paquets `apt`.
2.  **Installer Cewl via RubyGems** :

    ```bash
    sudo gem install cewl
    ```

    * **Explication** :
      * `sudo gem install cewl` : Installe Cewl via RubyGems.
3.  **Vérifier l'installation** :

    ```bash
    cewl --help
    ```

    * **Explication** : Vérifie que Cewl est installé correctement.

**Installation sur Windows**

1. **Télécharger Ruby depuis le site officiel de Ruby**.
   * **Explication** : Téléchargez et installez Ruby en suivant les instructions à l'écran.
2.  **Installer Cewl via la ligne de commande** :

    ```bash
    gem install cewl
    ```

#### Utilisation de Base

**1. Génération d'un Dictionnaire à partir d'un Site Web**

1.  **Commandement de base pour extraire des mots** :

    ```bash
    cewl http://example.com
    ```

    * **Explication** :
      * `http://example.com` : URL du site web à partir duquel extraire les mots.
    * **Discrétion** : Moyenne. L'exploration d'un site peut être détectée.
2.  **Enregistrer les mots extraits dans un fichier** :

    ```bash
    cewl http://example.com -w dictionnaire.txt
    ```

    * **Explication** :
      * `-w dictionnaire.txt` : Spécifie le fichier dans lequel enregistrer les mots extraits.
    * **Discrétion** : Moyenne. L'exploration d'un site peut être détectée.

**2. Extraction avec une Profondeur Spécifique**

1.  **Définir la profondeur de l'exploration des liens** :

    ```bash
    cewl http://example.com --depth 2
    ```

    * **Explication** :
      * `--depth 2` : Indique la profondeur de l'exploration des liens. Une profondeur de 2 explore les liens de premier et deuxième niveau.
    * **Discrétion** : Moyenne. L'exploration d'un site avec une profondeur plus élevée peut être plus facilement détectée.

**3. Extraction de Mots avec des Options de Filtrage**

1.  **Filtrer les mots en fonction de leur longueur** :

    ```bash
    cewl http://example.com --min_length 6 --max_length 12
    ```

    * **Explication** :
      * `--min_length 6` : Extrait seulement les mots d'une longueur minimale de 6 caractères.
      * `--max_length 12` : Extrait seulement les mots d'une longueur maximale de 12 caractères.
    * **Discrétion** : Moyenne. L'exploration d'un site peut être détectée.

#### Options Avancées

**1. Utilisation des Cookies pour l'Authentification**

1.  **Ajouter des cookies pour accéder à un site nécessitant une connexion** :

    ```bash
    cewl http://example.com --cookies "cookie1=value1; cookie2=value2"
    ```

    * **Explication** :
      * `--cookies` : Permet d'ajouter des cookies pour accéder à des zones protégées du site web.
    * **Discrétion** : Moyenne à faible. Les requêtes authentifiées peuvent être surveillées.

**2. Extraction des Mots en Ignorant les Balises HTML**

1.  **Exclure les balises HTML et les éléments JavaScript** :

    ```bash
    cewl http://example.com --ignore_words "javascript:;void(0);"
    ```

    * **Explication** :
      * `--ignore_words` : Exclut les mots spécifiques ou les patterns indésirables.
    * **Discrétion** : Moyenne. L'exploration d'un site peut être détectée.

**3. Utilisation d'un Proxy**

1.  **Configurer un proxy pour l'extraction des mots** :

    ```bash
    cewl http://example.com --proxy http://localhost:8080
    ```

    * **Explication** :
      * `--proxy` : Spécifie un serveur proxy pour acheminer le trafic HTTP.
    * **Discrétion** : Moyenne. Utiliser un proxy peut masquer l'origine des requêtes mais peut aussi être surveillé.

#### Exemples de Commandes

**1. Générer un Dictionnaire pour un Site Web Spécifique**

1.  **Commande pour extraire les mots et les enregistrer dans un fichier** :

    ```bash
    cewl http://example.com -w dictionnaire.txt
    ```

**2. Extraire des Mots avec Profondeur et Filtrage**

1.  **Commande pour extraire des mots avec une profondeur de 3 et longueur minimale de 8 caractères** :

    ```bash
    cewl http://example.com --depth 3 --min_length 8 -w dictionnaire.txt
    ```

#### Discrétion

**Discrétion** : Moyenne à faible. Les requêtes HTTP envoyées par Cewl peuvent être détectées par les systèmes de surveillance du réseau, surtout si de nombreuses requêtes sont effectuées en peu de temps. Assurez-vous de respecter les politiques d'utilisation des sites web que vous explorez et d'utiliser Cewl dans un cadre éthique.
