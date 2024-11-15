# 😁 Feroxbuster

#### Introduction

FeroxBuster est un outil rapide de découverte de contenu web qui utilise des techniques de force brute pour identifier les fichiers et répertoires cachés sur des serveurs web. Conçu pour être rapide et efficace, FeroxBuster permet aux auditeurs de sécurité et aux pentesters de découvrir des ressources non référencées qui peuvent révéler des vulnérabilités potentielles ou des informations sensibles.

#### Installation de FeroxBuster

**Sous Linux**

FeroxBuster peut être installé facilement via un script d'installation ou en téléchargeant le binaire directement depuis les releases GitHub.

**Installer FeroxBuster via le script d'installation**

```bash
curl -sL https://raw.githubusercontent.com/epi052/feroxbuster/master/install-nix.sh | bash
```

**Explication :** Ce script télécharge et installe automatiquement la dernière version de FeroxBuster.

**Sous Windows**

**Télécharger les binaires précompilés**

* Visitez la page [GitHub de FeroxBuster](https://github.com/epi052/feroxbuster/releases) pour télécharger le binaire pour Windows.
* Extrayez le fichier ZIP dans un répertoire de votre choix et ajoutez ce répertoire au PATH de Windows pour utiliser FeroxBuster depuis n'importe quelle invite de commande.

#### Commandes de Base

**Découverte de Répertoires et de Fichiers**

**Lancer un scan de base**

```bash
feroxbuster -u http://example.com
```

**Explication :** Lance un scan de base pour découvrir les répertoires et fichiers en utilisant les listes de mots intégrées.&#x20;

**Discrétion :** Moyenne. Génère un volume significatif de requêtes HTTP qui peuvent être détectées par les systèmes de surveillance des serveurs.

**Utilisation des listes de mots personnalisées**

**Scanner avec une liste de mots personnalisée**

```bash
feroxbuster -u http://example.com -w path/to/wordlist.txt
```

**Explication :** Utilise une liste de mots spécifique pour découvrir des ressources.&#x20;

**Discrétion :** Moyenne à élevée. Utiliser des listes de mots personnalisées peut augmenter ou diminuer la discrétion en fonction des chemins testés.

#### Options Avancées et Discrétion

**Ignorer les Codes de Statut**

**Ignorer des codes de statut spécifiques**

```bash
feroxbuster -u http://example.com --filter-status 404,403
```

**Explication :** Configure FeroxBuster pour ignorer les réponses avec des codes de statut 404 et 403.&#x20;

**Discrétion :** Moyenne. Ignorer les codes de statut fréquemment retournés réduit le bruit dans les résultats.

**Spécifier des Extensions de Fichiers**

**Tester des extensions spécifiques**

```bash
feroxbuster -u http://example.com -x php,html,js
```

**Explication :** Limite les requêtes aux types de fichiers spécifiés.&#x20;

**Discrétion :** Moyenne à élevée. Cibler des extensions spécifiques peut révéler des informations sensibles ou exploiter des vulnérabilités.

#### Exemples de Scénarios et Discrétion

**Découverte de panneaux d'administration**

```bash
feroxbuster -u http://example.com -w path/to/admin_wordlist.txt -x php
```

**Explication :** Utilise une liste de mots orientée vers la découverte de panneaux d'administration web.&#x20;

**Discrétion :** Élevée. La recherche de panneaux d'administration est souvent surveillée de près.

**Audit de sécurité complet d'une application web**

```bash
feroxbuster -u http://example.com --recurse -w path/to/wordlist.txt -x php,html,js --filter-size 0
```

**Explication :** Lance un scan récursif complet en utilisant une liste de mots détaillée et filtre les réponses de taille nulle.&#x20;

**Discrétion :** Moyenne à élevée. Un scan récursif est plus intrusif et génère un grand volume de trafic.

#### Bonnes Pratiques

* **Obtenir des Autorisations :** Toujours obtenir l'autorisation nécessaire avant de lancer des scans de découverte de contenu sur des serveurs web.
* **Limiter l'Impact :** Utilisez des délais (--delay) entre les requêtes pour minimiser l'impact sur les performances du serveur cible.
* **Surveiller les Réponses :** Évaluez soigneusement les réponses pour éviter de passer à côté de découvertes critiques ou de générer des faux positifs.
