---
layout: default
title: "Nikto"
---

#### Introduction

Nikto est un outil de scan de vulnérabilités pour les serveurs web. Il recherche des problèmes courants tels que des fichiers ou des répertoires vulnérables, des versions de logiciels obsolètes et des configurations de sécurité incorrectes. Nikto est efficace pour une première évaluation de la sécurité des serveurs web.

#### Installation de Nikto

**Installation sur Linux**

1.  **Installer via `apt` (pour les distributions basées sur Debian)**

    ```bash
    sudo apt update
    sudo apt install nikto
    ```
2.  **Installer via `git`**

    ```bash
    git clone https://github.com/sullo/nikto.git
    cd nikto
    ```

**Installation sur Windows**

1. **Télécharger le fichier ZIP** depuis le [dépôt GitHub de Nikto](https://github.com/sullo/nikto).
2. **Extraire le fichier ZIP** et naviguer jusqu'au dossier extrait via la ligne de commande.
3. **Exécuter Nikto avec Perl**, car Nikto est écrit en Perl. Assurez-vous que Perl est installé et disponible dans le PATH.

#### Commandes de Base

**Scan de Base d'un Serveur Web**

1.  **Effectuer un scan de base sur un serveur web**

    ```bash
    nikto -h <URL>
    ```

    * **Explication** : `-h` spécifie l'URL ou l'adresse IP du serveur web à scanner.
    * **Discrétion** : Moyenne à élevée. Le scan peut générer des logs sur le serveur cible et attirer l'attention des administrateurs.

**Scan en Mode Verbose**

1.  **Activer le mode verbose pour des détails supplémentaires**

    ```bash
    nikto -h <URL> -v
    ```

    * **Explication** : `-v` active le mode verbose pour afficher plus de détails sur le scan et les résultats.
    * **Discrétion** : Moyenne. Le mode verbose peut générer plus de trafic et de logs.

**Scan avec une Liste de Mots Personnalisée**

1.  **Utiliser une liste de mots personnalisée pour les tests**

    ```bash
    nikto -h <URL> -w <wordlist>
    ```

    * **Explication** : `-w` spécifie le chemin vers un fichier de liste de mots personnalisé pour les tests.
    * **Discrétion** : Moyenne à élevée. L'utilisation d'une liste de mots personnalisée peut modifier le comportement du scan et le type de données générées.

**Exclusion de Fichiers et Répertoires**

1.  **Exclure certains fichiers et répertoires du scan**

    ```bash
    nikto -h <URL> -x <path>
    ```

    * **Explication** : `-x` permet de spécifier un ou plusieurs chemins à exclure du scan.
    * **Discrétion** : Moyenne. L'exclusion de certains chemins peut réduire la charge sur le serveur et éviter les alertes.

**Sauvegarder les Résultats dans un Fichier**

1.  **Enregistrer les résultats du scan dans un fichier**

    ```bash
    nikto -h <URL> -o <outputfile>
    ```

    * **Explication** : `-o` spécifie le chemin vers le fichier de sortie où les résultats du scan seront enregistrés.
    * **Discrétion** : Moyenne. L'enregistrement des résultats permet une analyse plus approfondie ultérieurement.

#### Exemples de Scénarios

**Scan de Base**

1.  **Scanner un serveur web**

    ```bash
    nikto -h http://example.com
    ```

**Scan Verbose**

1.  **Effectuer un scan détaillé avec des informations supplémentaires**

    ```bash
    nikto -h http://example.com -v
    ```

**Scan avec Liste de Mots**

1.  **Utiliser une liste de mots personnalisée pour le scan**

    ```bash
    nikto -h http://example.com -w /path/to/wordlist.txt
    ```

**Exclusion de Chemins**

1.  **Exclure certains chemins du scan**

    ```bash
    nikto -h http://example.com -x /excluded/path
    ```

**Sauvegarde des Résultats**

1.  **Enregistrer les résultats du scan dans un fichier**

    ```bash
    nikto -h http://example.com -o results.txt
    ```

#### Discrétion et Bonnes Pratiques

1. **Obtenir des Autorisations**
   * **Assurez-vous d'avoir l'autorisation** de scanner le serveur web avant de lancer un scan.
   * **Respectez les lois et les politiques** de sécurité applicables.
2. **Limiter l'Impact**
   * **Configurez le scan pour ne pas surcharger le serveur** en ajustant les options comme la vitesse de scan.
   * **Excluez les chemins non pertinents** pour éviter de générer du bruit inutile.
3. **Analyser les Résultats avec Prudence**
   * **Examinez les résultats** pour identifier les failles et les vulnérabilités potentielles sans générer de faux positifs.
