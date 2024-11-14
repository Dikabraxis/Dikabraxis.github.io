
# Tutoriel Complet sur Penelope

## Introduction
Penelope est un outil de gestion de shells, conçu pour aider les pentesters à améliorer la gestion des shells inversés. Il fournit une interface avancée qui permet des fonctionnalités telles que l'auto-upgrade de shells en PTY (Pseudo-Terminal), la gestion de multiples sessions, le téléchargement et l'upload de fichiers, ainsi que d'autres commandes interactives.

---

## Installation de Penelope

### Prérequis
- **Python 3.6** ou plus récent
- **Git** pour cloner le dépôt
- Environnement compatible **Linux ou macOS** (Penelope supporte principalement les shells Unix)

### Étapes d'installation
1. **Cloner le dépôt GitHub** :
    ```bash
    git clone https://github.com/brightio/penelope.git
    cd penelope
    ```
2. **Exécuter Penelope** :
    ```bash
    python3 penelope.py
    ```
    **Note** : Penelope est un script Python autonome, il n'est pas nécessaire d'installer d'autres dépendances.

---

## Utilisation de Penelope

### 1. Lancer Penelope pour écouter des connexions shell
```bash
python3 penelope.py        # Écoute sur le port par défaut (4444)
python3 penelope.py 5555   # Écoute sur le port 5555
python3 penelope.py 5555 -i eth0  # Écoute sur une interface spécifique
```
**Explication** :
- Le premier argument définit le port d'écoute.
- L'option `-i` permet de spécifier une interface réseau particulière.

### 2. Connexion à un shell bind
```bash
python3 penelope.py -c <target_ip> 3333
```
**Explication** :  
L'option `-c` (connect) permet de se connecter à une cible qui écoute sur le port 3333.

---

## Fonctions de téléchargement et d'upload

### Télécharger un fichier de la cible
```bash
download /etc/passwd
```

### Uploader un fichier vers la cible
```bash
upload linpeas.sh /tmp
```
**Explication** :
- `download` : Télécharge un fichier depuis la machine cible.
- `upload` : Envoie un fichier local vers la cible.

---

## Maintien de sessions multiples
```bash
python3 penelope.py --maintain 2
```
**Explication** :  
`--maintain` : Maintient deux sessions actives avec la cible. Si une session est perdue, elle est recréée automatiquement.

---

## Auto-upgrade en shell PTY
Penelope tente automatiquement d'upgrader un shell simple en PTY pour permettre des commandes interactives.
```bash
upgrade
```
**Explication** :  
`upgrade` : Convertit le shell actuel en un shell interactif avec PTY.

---

## Fonctionnalités de persistance
```bash
persist
```
**Explication** :  
Cette commande maintient l'accès même après un redémarrage.

---

## Serveur HTTP intégré
```bash
python3 penelope.py -s --port 8000
```
**Explication** :  
L'option `-s` active le serveur HTTP, avec `--port` pour spécifier le port.

---

## Exécution de scripts locaux sur la cible
```bash
run script.sh
```
**Explication** :  
Permet d'exécuter des scripts locaux sur la cible.

---

## Scénarios d'utilisation

### Exemple 1 : Maintenir un accès constant à une machine
```bash
python3 penelope.py --maintain 2
```
Penelope régénérera une session si l'une tombe.

### Exemple 2 : Exécuter des scripts de post-exploitation
```bash
upload linpeas.sh /tmp
run /tmp/linpeas.sh
```

---

## Conclusion
Penelope est un outil puissant pour les pentesters cherchant à améliorer leur gestion des shells. Grâce à ses fonctionnalités telles que le maintien de sessions multiples, l'auto-upgrade des shells en PTY, et la gestion des uploads/téléchargements, il simplifie grandement les tâches de post-exploitation.
