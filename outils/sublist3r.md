# 😁 Sublist3r

#### Introduction

Sublist3r est un outil pour la découverte de sous-domaines. Il aide les testeurs de sécurité et les analystes à identifier les sous-domaines associés à un domaine cible, ce qui est crucial pour une reconnaissance efficace.

#### Installation de Sublist3r

**Installation via git**

1.  **Cloner le Dépôt GitHub** :

    ```bash
    git clone https://github.com/aboul3la/Sublist3r.git
    cd Sublist3r
    ```

    * **Explication** :
      * `git clone` : Clone le dépôt GitHub de Sublist3r.
      * `cd Sublist3r` : Navigue dans le répertoire cloné.
2.  **Installer les Dépendances** :

    ```bash
    pip install -r requirements.txt
    ```

    * **Explication** : Installe les dépendances nécessaires pour Sublist3r à partir du fichier `requirements.txt`.

#### Utilisation de Base

**Scan de Sous-domaines**

1.  **Exécuter Sublist3r pour découvrir les sous-domaines** :

    ```bash
    python sublist3r.py -d example.com
    ```

    * **Explication** :
      * `-d` : Spécifie le domaine cible pour la recherche des sous-domaines.
    * **Discrétion** : Élevée. Sublist3r effectue des requêtes à des moteurs de recherche et des services API, ce qui est généralement discret.

**Exemples d'Options Supplémentaires**

1.  **Utiliser des moteurs de recherche spécifiques** :

    ```bash
    python sublist3r.py -d example.com -b
    ```

    * **Explication** :
      * `-b` : Utilise les moteurs de recherche pour la recherche de sous-domaines (Google, Bing, Yahoo, etc.).
    * **Discrétion** : Élevée. Les requêtes aux moteurs de recherche sont discrètes, mais peuvent générer du trafic visible.
2.  **Exporter les résultats dans un fichier** :

    ```bash
    python sublist3r.py -d example.com -o subdomains.txt
    ```

    * **Explication** :
      * `-o` : Spécifie le fichier de sortie pour enregistrer les sous-domaines découverts.
    * **Discrétion** : Élevée. L'exportation des résultats est une action locale, sans impact sur la discrétion.
3.  **Utiliser des services d'API** :

    ```bash
    python sublist3r.py -d example.com -a -o subdomains.txt
    ```

    * **Explication** :
      * `-a` : Utilise les services d'API (comme VirusTotal) pour rechercher des sous-domaines.
    * **Discrétion** : Élevée. L'utilisation des API est discrète, mais peut être légèrement plus visible que les requêtes standard.

#### Discrétion

**Discrétion** : Élevée. Sublist3r effectue des requêtes à des moteurs de recherche et des services API, ce qui est généralement discret. Cependant, il peut générer du trafic visible, notamment si de nombreux sous-domaines sont découverts ou si des API spécifiques sont utilisées. Il est recommandé d'obtenir les autorisations nécessaires avant d'utiliser Sublist3r dans des environnements de production ou sur des domaines qui ne vous appartiennent pas.
