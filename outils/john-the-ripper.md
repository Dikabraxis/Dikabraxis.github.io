---
layout: default
title: "John The Ripper"
---

#### Introduction

John the Ripper est un outil robuste de craquage de mots de passe conçu pour aider les administrateurs de systèmes, les auditeurs de sécurité, et les passionnés de cybersécurité à tester la robustesse des mots de passe dans leurs systèmes. Il supporte de nombreux formats de hachage et inclut des utilitaires qui facilitent la conversion de formats spécifiques de données cryptées (comme SSH, GPG) en un format que John peut traiter.

#### Installation de John the Ripper

**Sur Linux**

**Installer depuis les dépôts (pour les distributions basées sur Debian)**

```bash
sudo apt update
sudo apt install john
```

**Installer depuis les sources**

```bash
sudo apt install build-essential libssl-dev libgmp-dev
git clone https://github.com/openwall/john.git
cd john/src
./configure && make
sudo make install
```

**Sur Windows**

**Télécharger les binaires précompilés**

* Visitez le site officiel de John the Ripper ou sa page GitHub pour télécharger les versions précompilées pour Windows.

#### Utilisation de Base et Discrétion

**Créer un Hash de Mots de Passe**

```bash
echo "password123" | john --stdin --format=raw-md5
```

**Explication :** Convertit le mot de passe en un hash MD5. **Discrétion :** Faible à moyenne. Créer un hash est généralement une activité discrète mais dépend de l'endroit où les hash sont stockés ou utilisés.

**Craquage de Mots de Passe**

**Craquer des mots de passe à partir d'un fichier de hachages**

```bash
john --wordlist=<wordlist_file> <hash_file>
```

**Explication :** Utilise une liste de mots pour craquer les hachages. **Discrétion :** Élevée. Utiliser des listes de mots de passe peut être détecté si effectué sur des systèmes surveillés.

**Craquer des hachages en utilisant un mode de force brute**

```bash
john --incremental <hash_file>
```

**Explication :** Tente toutes les combinaisons possibles de mots de passe. **Discrétion :** Très élevée. Les attaques de force brute sont bruyantes et facilement détectables.

#### Utilisation des Utilitaires `*2john`

John the Ripper comprend une série d'utilitaires nommés `*2john` qui sont utilisés pour extraire des hachages de divers types de fichiers cryptés. Ces utilitaires transforment les données cryptées en un format que John peut ensuite craquer.

**ssh2john**

**Utiliser ssh2john pour préparer les hachages de clés SSH**

```bash
ssh2john id_rsa > id_rsa.hash
```

**Explication :** Convertit une clé privée SSH en un format de hachage que John peut traiter. **Discrétion :** Moyenne. Extraire des hachages à partir de fichiers peut être détecté si les fichiers sont surveillés.

**gpg2john**

**Utiliser gpg2john pour extraire des hachages de fichiers GPG**

```bash
gpg2john private.key > private.key.hash
```

**Explication :** Prépare les hachages de clés GPG pour le craquage. **Discrétion :** Moyenne. Comme pour ssh2john, cela dépend de la surveillance des fichiers sources.

#### Options Avancées et Discrétion

**Utiliser des Règles pour Améliorer les Attaques**

```bash
john --wordlist=<wordlist_file> --rules <hash_file>
```

**Explication :** Applique des modifications complexes aux mots de la liste pour craquer des hachages plus efficacement. **Discrétion :** Moyenne à élevée. Plus complexe et potentiellement plus facile à détecter en raison des modèles inhabituels de tentatives de connexion.

#### Exemples de Scénarios et Discrétion

**Craquage de Hachages MD5 avec une Liste de Mots**

```bash
john --wordlist=/path/to/wordlist.txt --format=raw-md5 hashes.txt
```

**Discrétion :** Élevée, surtout si les tentatives de connexion sont surveillées.

**Force Brute**

```bash
john --incremental --format=raw-md5 hashes.txt
```

**Discrétion :** Très élevée, due à l'intensité et à la nature de l'activité.

#### Bonnes Pratiques

* **Obtenir des Autorisations :** Assurez-vous d'avoir l'autorisation nécessaire avant de tenter de craquer des mots de passe.
* **Limiter l'Impact :** Utilisez des techniques ciblées pour minimiser l'attention.
* **Surveiller les Ressources :** Soyez conscient de l'utilisation des ressources pour éviter de compromettre les performances du système.
