# 😁 Mimikatz

**Introduction**\
Mimikatz est un outil puissant pour l'extraction de mots de passe, de hashes et de tickets Kerberos depuis la mémoire d'un système Windows compromis. Il est souvent utilisé dans les tests de pénétration pour démontrer des failles de sécurité dans les systèmes de gestion des mots de passe et des sessions.

**Installation de Mimikatz**

* **Sous Windows** : Téléchargez Mimikatz depuis le dépôt GitHub de Mimikatz ou depuis un site de confiance. Décompressez l’archive ZIP et exécutez `mimikatz.exe` depuis l'invite de commandes (cmd) avec les droits administratifs.

**Utilisation de Base**

1.  **Exécuter Mimikatz**

    ```cmd
    mimikatz
    ```

    **Explication** : Lance l’interface de ligne de commande de Mimikatz pour accéder à ses fonctionnalités.\
    **Discrétion** : Faible. L'exécution de Mimikatz est souvent surveillée et peut être détectée par les solutions de sécurité.
2.  **Obtenir les Hashes des Mots de Passe**

    ```cmd
    privilege::debug
    lsadump::sam
    ```

    **Explication** : Active les privilèges de débogage et extrait les hashes NTLM des comptes utilisateurs stockés dans le SAM (Security Accounts Manager).\
    **Discrétion** : Faible. L'extraction des hashes NTLM est très visible et peut être détectée facilement.

**Options Avancées**

1.  **Extraire les Tickets Kerberos**

    ```cmd
    kerberos::list
    ```

    **Explication** : Liste les tickets Kerberos en mémoire, qui peuvent être utilisés pour effectuer des attaques de type pass-the-ticket.\
    **Discrétion** : Moyenne. Les tickets Kerberos en mémoire peuvent être détectés par des outils de surveillance des tickets.
2.  **Injecter des Tickets Kerberos**

    ```cmd
    kerberos::ptt /path/to/ticket.kirbi
    ```

    **Explication** : Injecte des tickets Kerberos dans le système pour obtenir des accès privilégiés ou contourner les contrôles de sécurité.\
    **Discrétion** : Moyenne. L’injection des tickets Kerberos peut être détectée par des contrôles de sécurité Kerberos et les outils de surveillance réseau.

**Exemples d'Extraction**

1.  **Extraire les Mots de Passe des Sessions Actives**

    ```cmd
    sekurlsa::logonpasswords
    ```

    **Explication** : Extrait les mots de passe et les hashes des sessions actives en mémoire.\
    **Discrétion** : Faible. La récupération de mots de passe actifs est généralement surveillée par les solutions de sécurité.
2.  **Dump des Hashes NTLM**

    ```cmd
    lsadump::sam
    ```

    **Explication** : Extrait les hashes NTLM des comptes utilisateurs stockés dans le SAM du système.\
    **Discrétion** : Faible. Le dumping des hashes NTLM est souvent surveillé et peut être détecté par les solutions de sécurité.
