# 😁 Empire

**Introduction**\
Empire est un framework de post-exploitation open-source pour la gestion et l'exploitation des systèmes compromis. Il offre des fonctionnalités puissantes pour la collecte d'informations, l'escalade des privilèges, et l'exécution de commandes via des agents PowerShell ou Python.

**Installation d'Empire**

*   **Sous Linux/macOS** :

    ```bash
    git clone https://github.com/EmpireProject/Empire.git
    cd Empire
    ./setup/install.sh
    ```

    **Explication** : Télécharge le code source d'Empire depuis GitHub, se place dans le répertoire d'Empire et exécute le script d'installation.
* **Sous Windows** : Téléchargez les binaires depuis le dépôt GitHub d'Empire, décompressez-les et suivez les instructions pour installer.

**Utilisation de Base**

1.  **Démarrer Empire**

    ```bash
    ./empire
    ```

    **Explication** : Lance l’interface de ligne de commande d’Empire pour accéder aux fonctionnalités du framework.\
    **Discrétion** : Faible. Le lancement de l'interface peut être détecté par des outils de surveillance du système.
2.  **Créer et Configurer un Listener**

    * **Commande** : Dans l'interface Empire, tapez `listeners`, puis configurez un listener en spécifiant l'adresse IP, le port et le protocole (HTTP, HTTPS, etc.).

    **Explication** : Met en place un listener pour accepter les connexions des agents compromis afin de pouvoir interagir avec eux.\
    **Discrétion** : Moyenne. Les connexions des agents peuvent être détectées par les solutions de surveillance du réseau.

**Options Avancées**

1.  **Utiliser des Modules**

    * **Commande** : Chargez un module avec `usemodule` (ex. `usemodule powershell/credentials/gather/kerberoast`) et exécutez-le.

    **Explication** : Exécute des modules spécifiques pour accomplir des tâches comme la collecte de mots de passe ou l’escalade des privilèges.\
    **Discrétion** : Variable. Les actions effectuées par les modules peuvent être détectées en fonction de la technique utilisée.
2.  **Gérer les Agents**

    * **Commande** : Utilisez `agents` pour afficher les agents actifs et `kill` pour terminer une session.

    **Explication** : Surveillez et gérez les agents connectés, envoyez des commandes ou terminez des sessions lorsqu'elles ne sont plus nécessaires.\
    **Discrétion** : Moyenne à faible. La gestion des agents peut être détectée par les outils de surveillance du réseau si des activités suspectes sont observées.

**Exemples d'Exploitation**

1.  **Collecter des Hashes de Mots de Passe**

    * **Commande** : Utilisez un module comme `creds` pour extraire des mots de passe ou des hashes.

    **Explication** : Extraie des informations d'authentification stockées en mémoire sur le système compromis.\
    **Discrétion** : Faible. L'extraction de mots de passe est souvent surveillée par des solutions de sécurité.
2.  **Exécuter des Commandes sur un Système Compromis**

    * **Commande** : Envoyez des commandes à l’agent via l’interface Empire.

    **Explication** : Effectue des actions sur le système compromis à distance.\
    **Discrétion** : Moyenne. Les commandes envoyées peuvent être détectées par les systèmes de surveillance si elles sont particulièrement visibles.
