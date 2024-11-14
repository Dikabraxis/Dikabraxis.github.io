
# Penelope - Guide d'utilisation

**Penelope** est un outil puissant permettant aux pentesters d'améliorer leur gestion des shells, avec des fonctionnalités comme le maintien de sessions multiples, l'auto-upgrade des shells en PTY, et la gestion des uploads/téléchargements.

---

## Connexion à une cible
L'option `-c` (connect) permet de se connecter à une cible qui écoute sur le port 3333.

---

## Fonctions de téléchargement et d'upload

Penelope inclut des commandes pour télécharger et uploader des fichiers depuis ou vers la machine cible.

### Télécharger un fichier de la cible
```bash
download /etc/passwd
```

### Uploader un fichier vers la cible
```bash
upload linpeas.sh /tmp
```

**Explication** :
- `download` : Télécharge un fichier spécifié depuis la machine cible.
- `upload` : Envoie un fichier local vers la cible, dans le chemin spécifié (par exemple `/tmp`).

---

## Maintien de sessions multiples

Une des fonctionnalités puissantes de Penelope est la gestion de multiples sessions. Penelope permet de maintenir un certain nombre de shells actifs sur une cible, et si une session est perdue, elle sera automatiquement recréée.

```bash
python3 penelope.py --maintain 2
```
**Explication** :  
`--maintain` : Cette option permet de maintenir deux sessions actives avec la cible. Si l'une des sessions tombe, elle est automatiquement recréée.

---

## Auto-upgrade en shell PTY

Penelope tente automatiquement d'upgrader un shell simple en **PTY** (Pseudo-Terminal), afin de permettre l'utilisation de commandes interactives (comme `nano`, `top`, etc.) et d'améliorer l'expérience shell.

Cela se fait automatiquement lorsqu'une connexion est établie. Toutefois, si le shell n'est pas automatiquement amélioré, vous pouvez forcer un upgrade manuel avec la commande suivante :
```bash
upgrade
```
**Explication** :  
`upgrade` : Tente de convertir le shell actuel en un shell interactif avec PTY.

---

## Fonctionnalités de persistance

Penelope peut ajouter de la persistance à votre connexion, en maintenant un certain nombre de sessions ou en ajoutant des backdoors. Pour configurer la persistance, utilisez la commande suivante :
```bash
persist
```
**Explication** :  
Cette commande tente de maintenir l'accès à la machine compromise même après un redémarrage ou d'autres interruptions.

---

## Serveur HTTP intégré

Penelope dispose également d'un serveur HTTP intégré pour partager des fichiers facilement entre votre machine et la cible.
```bash
python3 penelope.py -s --port 8000
```
**Explication** :  
`-s` active le serveur HTTP, et l'option `--port` permet de spécifier un port particulier (8000 dans cet exemple).

---

## Exécution de scripts locaux sur la cible

Penelope vous permet d'exécuter des scripts locaux sur la machine cible et d'obtenir les résultats sur votre machine.
```bash
run script.sh
```

---

## Scénarios d'utilisation

### Exemple 1 : Maintenir un accès constant à une machine
Si vous souhaitez maintenir deux sessions actives avec une machine cible pour ne pas perdre l'accès, vous pouvez exécuter :
```bash
python3 penelope.py --maintain 2
```
Penelope régénérera une nouvelle session si une des connexions est perdue, vous garantissant ainsi un accès constant à la cible.

### Exemple 2 : Exécuter des scripts de post-exploitation
Après avoir établi une connexion shell, vous pouvez facilement uploader et exécuter des scripts de post-exploitation, comme **LinPEAS** pour énumérer les informations sur la cible.
```bash
upload linpeas.sh /tmp
run /tmp/linpeas.sh
```

---

## Conclusion

Penelope est un outil puissant pour les pentesters cherchant à améliorer leur gestion des shells. Grâce à ses fonctionnalités telles que le maintien de sessions multiples, l'auto-upgrade des shells en PTY, et la gestion des uploads/téléchargements, il simplifie grandement les tâches de post-exploitation.
