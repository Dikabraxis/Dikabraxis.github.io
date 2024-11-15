# 😁 ZAP

#### Introduction

ZAP (OWASP Zed Attack Proxy) est un outil open-source de test de sécurité des applications web. Il fournit des fonctionnalités telles qu'un proxy, un scanner de vulnérabilités, et des outils de manipulation de requêtes pour évaluer la sécurité des applications web.

#### Installation de ZAP

**Installation via `apt` (pour les distributions basées sur Debian)**

1.  **Installer ZAP** :

    ```bash
    sudo apt update
    sudo apt install zaproxy
    ```

    * **Explication** :
      * `sudo apt update` : Met à jour la liste des paquets disponibles.
      * `sudo apt install zaproxy` : Installe ZAP via le gestionnaire de paquets `apt`.

**Installation via le Site Officiel**

1. **Télécharger ZAP** depuis le site officiel et suivre les instructions pour votre système d'exploitation.
   * **Explication** : Télécharge l'installateur approprié et suit les étapes d'installation fournies.

#### Utilisation de Base

**1. Lancer ZAP**

1.  **Démarrer ZAP** :

    ```bash
    zaproxy
    ```

    * **Explication** : Lance l'application ZAP.

**2. Configurer le Proxy**

1. **Configurer le navigateur pour utiliser le proxy ZAP** :
   * **Explication** :
     * Par défaut, ZAP utilise le port 8080. Configurez votre navigateur pour utiliser `localhost:8080` comme serveur proxy.
   * **Discrétion** : Moyenne à faible. L'utilisation d'un proxy local peut être détectée par des outils de surveillance réseau.

**3. Scanner une Application Web**

1. **Configurer et lancer un scan** :
   * **Ajouter l'URL de l'application** :
     * Ouvrez ZAP.
     * Dans le panneau "Sites", faites un clic droit et sélectionnez "Add Context".
     * Entrez l'URL de l'application web cible.
   * **Lancer un scan actif** :
     * Allez dans l'onglet "Active Scan".
     * Sélectionnez le contexte ou la cible.
     * Cliquez sur "Start Scan".
   * **Discrétion** : Moyenne à faible. Un scan actif envoie de nombreuses requêtes à la cible, ce qui peut être facilement détecté.

**4. Analyser les Résultats**

1. **Consulter les rapports** :
   * **Explication** :
     * Les vulnérabilités et les problèmes de sécurité seront affichés dans le panneau "Alerts" ou "Results".
     * Vous pouvez exporter ces résultats dans divers formats via le menu "Reports".
   * **Discrétion** : N/A (action locale).

#### Discrétion

**Discrétion** : Moyenne à faible. ZAP est souvent détecté comme un proxy de sécurité. Les scans actifs et les requêtes générées par ZAP peuvent être facilement identifiés par les systèmes de surveillance. Assurez-vous de configurer le proxy correctement et d'exécuter des scans sur des environnements où vous avez l'autorisation. Utilisez des délais dans vos scans pour réduire la détection et minimiser les impacts sur la cible.
