#### Introduction

OpenVAS (Open Vulnerability Assessment System) est un scanner de vulnérabilités open-source utilisé pour identifier et gérer les vulnérabilités dans les systèmes et les réseaux. Il fait partie de la suite Greenbone Vulnerability Management (GVM).

#### Installation d'OpenVAS

**Installation sur Debian/Ubuntu**

1.  **Ajouter le dépôt Greenbone** :

    ```bash
    sudo add-apt-repository ppa:mrazavi/gvm
    ```

    * **Explication** : Ajoute le dépôt PPA pour installer les paquets OpenVAS.
    * **Discrétion** : N/A (action locale, aucune interaction réseau).
2.  **Mettre à jour les paquets et installer OpenVAS** :

    ```bash
    sudo apt update
    sudo apt install gvm
    ```

    * **Explication** : Met à jour la liste des paquets et installe OpenVAS.
    * **Discrétion** : N/A (action locale, aucune interaction réseau).
3.  **Configurer et initialiser OpenVAS** :

    ```bash
    sudo gvm-setup
    ```

    * **Explication** : Configure et initialise OpenVAS.
    * **Discrétion** : N/A (action locale, aucune interaction réseau).
4.  **Vérifier l'installation** :

    ```bash
    sudo gvm-check-setup
    ```

    * **Explication** : Vérifie que l'installation d'OpenVAS a été effectuée correctement.
    * **Discrétion** : N/A (action locale, aucune interaction réseau).

#### Utilisation d'OpenVAS

**Démarrage et Accès à l'Interface Web**

1.  **Démarrer les services OpenVAS** :

    ```bash
    sudo gvm-start
    ```

    * **Explication** : Démarre les services nécessaires pour OpenVAS.
    * **Discrétion** : N/A (action locale, aucune interaction réseau).
2. **Accéder à l'interface web** :
   * Ouvrir un navigateur web et naviguer vers : `https://localhost:9392`
   * Se connecter avec les informations d'identification fournies lors de la configuration initiale.
   * **Discrétion** : Moyenne. Accéder à l'interface web génère du trafic réseau local, mais ne devrait pas attirer beaucoup d'attention.

**Scanner un Réseau ou un Système**

1. **Créer une nouvelle tâche de scan**
   * Aller dans l'interface web d'OpenVAS.
   * Cliquer sur "Scans" > "Tasks" > "New Task".
2. **Configurer la tâche de scan**
   * **Name** : Donner un nom à la tâche.
   * **Scan Targets** : Spécifier les cibles (adresse IP ou plage d'adresses).
   * **Scan Config** : Choisir une configuration de scan (par exemple, "Full and fast").
   * **Scanner** : Utiliser le scanner par défaut (OpenVAS Default).
   * **Discrétion** : Moyenne à élevée. Le scan de vulnérabilités peut générer beaucoup de trafic réseau et peut être détecté par des systèmes de surveillance.
3. **Lancer la tâche de scan**
   * Sauvegarder la tâche et cliquer sur "Start".
   * **Discrétion** : Moyenne à élevée. Le lancement d'un scan génère du trafic réseau et peut déclencher des alertes de sécurité.
4. **Visualiser les résultats**
   * Aller dans "Scans" > "Reports" pour voir les résultats du scan une fois terminé.
   * **Discrétion** : N/A (action locale, aucune interaction réseau).

**Gestion des Vulnérabilités**

1. **Analyser les résultats**
   * Dans la section "Reports", cliquer sur le rapport du scan pour voir les détails des vulnérabilités détectées.
   * **Discrétion** : N/A (action locale, aucune interaction réseau).
2. **Créer des tickets ou des tâches de correction**
   * Identifier les vulnérabilités critiques et créer des tickets pour les corriger.
   * Prioriser les tâches en fonction de la gravité des vulnérabilités.
   * **Discrétion** : N/A (action locale, aucune interaction réseau).
3. **Re-scanner après correction**
   * Après avoir corrigé les vulnérabilités, re-scannez les cibles pour vérifier que les corrections ont été effectuées avec succès.
   * **Discrétion** : Moyenne à élevée. Les re-scans génèrent du trafic réseau et peuvent être détectés par des systèmes de surveillance.

#### Options Avancées

**Utilisation de l'Interface en Ligne de Commande**

OpenVAS fournit des outils en ligne de commande pour interagir avec le gestionnaire de vulnérabilités.

1.  **Liste des commandes disponibles**

    ```bash
    gvm-cli --help
    ```

    * **Explication** : Affiche l'aide pour les commandes disponibles de gvm-cli.
    * **Discrétion** : N/A (action locale, aucune interaction réseau).
2.  **Lister les tâches existantes**

    ```bash
    gvm-cli --gmp-username <username> --gmp-password <password> socket --xml "<get_tasks/>"
    ```

    * **Explication** : Liste toutes les tâches existantes dans OpenVAS.
    * **Discrétion** : Basse. La commande interagit avec le serveur OpenVAS mais ne génère pas de trafic réseau important.
3.  **Créer une nouvelle tâche via CLI**

    ```bash
    gvm-cli --gmp-username <username> --gmp-password <password> socket --xml "<create_task><name>New Task</name><config id='<config_id>'/><target id='<target_id>'/></create_task>"
    ```

    * **Explication** : Crée une nouvelle tâche de scan via la ligne de commande.
    * **Discrétion** : Basse. La création de tâches n'entraîne pas d'activité réseau notable.
4.  **Lancer une tâche via CLI**

    ```bash
    gvm-cli --gmp-username <username> --gmp-password <password> socket --xml "<start_task task_id='<task_id>'/>"
    ```

    * **Explication** : Démarre une tâche de scan existante via la ligne de commande.
    * **Discrétion** : Moyenne à élevée. Le lancement d'un scan génère du trafic réseau et peut déclencher des alertes de sécurité.
5.  **Vérifier l'état d'une tâche via CLI**

    ```bash
    gvm-cli --gmp-username <username> --gmp-password <password> socket --xml "<get_tasks task_id='<task_id>'/>"
    ```

    * **Explication** : Vérifie l'état d'une tâche de scan existante via la ligne de commande.
    * **Discrétion** : Basse. La vérification de l'état des tâches n'entraîne pas d'activité réseau notable.

#### Bonnes Pratiques et Discrétion

1. **Obtenir des Autorisations**
   * **Assurez-vous toujours** d'avoir les autorisations nécessaires avant de scanner des réseaux ou des systèmes.
   * **Discrétion** : Élevée. Les scans sans autorisation sont éthiquement et légalement problématiques.
2. **Limiter la portée des scans**
   * Spécifier des plages d'adresses IP précises pour éviter d'affecter des systèmes non ciblés.
   * **Discrétion** : Moyenne à élevée. Limiter la portée réduit la visibilité mais génère tout de même du trafic réseau.
3. **Planifier les scans pendant les heures creuses**
   * Effectuer les scans pendant les périodes de faible activité pour minimiser l'impact sur les performances du réseau.
   * **Discrétion** : Moyenne. Les scans hors des heures de pointe attirent moins l'attention.
4. **Analyser les résultats en détail**
   * Examiner attentivement les rapports de vulnérabilités pour comprendre les implications et prioriser les corrections.
   * **Discrétion** : N/A (action locale, aucune interaction réseau).
