

# Introduction

**Nmap (Network Mapper)** est un outil puissant pour la découverte de réseaux et l’audit de sécurité. Il permet de scanner des réseaux pour découvrir des hôtes actifs, des services ouverts, des systèmes d'exploitation et bien plus encore.

---

## Installation de Nmap

### Sous Linux
```bash
sudo apt-get install nmap    # Pour les distributions basées sur Debian/Ubuntu
```

### Sous Windows
Téléchargez le programme d'installation depuis le [site officiel de Nmap](https://nmap.org/download.html) et suivez les instructions.

---

## Commandes de Base

### Scan de base
```bash
nmap <IP ou domaine>
```
**Explication** : Effectue un scan par défaut pour découvrir les hôtes actifs et les services ouverts sur l'adresse IP ou le domaine spécifié.
**Discrétion** : Moyenne. Dépend des services ouverts et de la configuration du réseau cible.

### Scan de plusieurs hôtes
```bash
nmap 192.168.1.1 192.168.1.2 192.168.1.3
nmap 192.168.1.1-10
```
**Explication** : Permet de scanner plusieurs adresses IP à la fois, soit en les listant individuellement, soit en spécifiant une plage d'adresses.
**Discrétion** : Moyenne.

### Scan d'une plage d'adresses IP
```bash
nmap 192.168.1.0/24
```
**Explication** : Scanne un sous-réseau complet en utilisant la notation CIDR.
**Discrétion** : Faible à moyenne.

### Scan de ports spécifiques
```bash
nmap -p 22,80,443 <IP>
```
**Explication** : Limite le scan à des ports spécifiques (par exemple, les ports 22, 80, et 443).
**Discrétion** : Haute.

### Scan de tous les ports
```bash
nmap -p- <IP>
```
**Explication** : Scanne tous les ports TCP disponibles (de 1 à 65535).
**Discrétion** : Faible.

---

## Types de Scans

### Scan SYN (scan par défaut, nécessite des privilèges root)
```bash
sudo nmap -sS <IP>
```
**Explication** : Effectue un scan SYN, souvent appelé "demi-ouvert", car il n'établit pas de connexion complète. Ce scan est rapide et discret.
**Discrétion** : Haute.

### Scan de connectivité TCP (n'exige pas de privilèges root)
```bash
nmap -sT <IP>
```
**Explication** : Effectue un scan de connectivité TCP complet en établissant des connexions complètes avec les ports cibles.
**Discrétion** : Moyenne à faible.

### Scan UDP
```bash
sudo nmap -sU <IP>
```
**Explication** : Scanne les ports UDP. Ce type de scan est plus lent et peut générer beaucoup de faux positifs.
**Discrétion** : Moyenne.

### Scan pour la détection des versions des services
```bash
nmap -sV <IP>
```
**Explication** : Interroge les services sur les ports ouverts pour déterminer les versions des logiciels en cours d'exécution.
**Discrétion** : Moyenne.

### Scan de détection du système d'exploitation
```bash
sudo nmap -O <IP>
```
**Explication** : Utilise diverses techniques pour déterminer le système d'exploitation en cours d'exécution sur l'hôte cible.
**Discrétion** : Faible.

---

## Options Avancées

### Fragmentation des paquets (-f)
```bash
sudo nmap -f <IP>
```
**Explication** : Fragmente les paquets envoyés en plus petits segments pour contourner certains pare-feu et IDS.
**Discrétion** : Haute.

### Spécification de la taille des fragments
```bash
sudo nmap --mtu 24 <IP>
```
**Explication** : Permet de spécifier la taille de l'unité de transmission maximale (MTU) pour les fragments.
**Discrétion** : Haute.

### Utilisation de fausses adresses IP sources (-D)
```bash
sudo nmap -D RND:10 <IP>
```
**Explication** : Utilise des adresses IP sources fictives pour masquer l'origine réelle du scan.
**Discrétion** : Très haute.

### Scan avec temporisation lente (-T0 à -T5)
```bash
sudo nmap -sS -T0 <IP>
```
**Explication** : Utilise un timing très lent pour rendre le scan moins détectable.
**Discrétion** : Très haute.
