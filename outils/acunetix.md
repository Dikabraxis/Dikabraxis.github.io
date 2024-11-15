---
layout: default
title: "Acunetix"
---

**Introduction**\
Acunetix est un scanner de vulnérabilités web automatisé qui identifie les failles de sécurité dans les applications web telles que les injections SQL, les vulnérabilités XSS et les erreurs de configuration. Il fournit des rapports détaillés pour aider à corriger les vulnérabilités découvertes.

**Installation d'Acunetix**

* **Sous Linux/macOS/Windows** : Téléchargez la version d’évaluation ou achetez une licence depuis le [site officiel d’Acunetix](https://www.acunetix.com/). Suivez les instructions pour l’installation spécifique à votre système d'exploitation.

**Utilisation de Base**

1.  **Lancer une Analyse de Site**

    * **Commande** : Accédez à l’interface web d’Acunetix (`https://localhost:443`), allez dans `Scans` et créez un nouveau scan en entrant l’URL du site cible.

    **Explication** : Acunetix scanne le site web pour détecter des vulnérabilités potentielles en explorant les pages, les formulaires, et les paramètres de requêtes.\
    **Discrétion** : Moyenne. Le scan peut être détecté par les systèmes de détection d'intrusions ou les logs du serveur.
2.  **Configurer des Analyses Programmées**

    * **Commande** : Interface web d'Acunetix, dans `Scans > New Scan`, configurez les paramètres pour une analyse récurrente, en définissant la fréquence et les heures d'exécution.

    **Explication** : Permet de planifier des analyses automatiques pour surveiller les applications web régulièrement pour de nouvelles vulnérabilités.\
    **Discrétion** : Variable. Les analyses programmées peuvent être configurées pour se dérouler pendant des périodes de faible activité pour réduire la visibilité.

**Options Avancées**

1.  **Configurer les Profils d'Analyse**

    * **Commande** : Lors de la création d'un scan dans l'interface web, accédez aux paramètres avancés pour ajuster les politiques de sécurité, les types de tests à effectuer, et les chemins à exclure.

    **Explication** : Personnalise les paramètres de l’analyse pour répondre à des besoins spécifiques, comme exclure certains répertoires ou inclure des tests de sécurité particuliers.\
    **Discrétion** : Variable. La personnalisation peut aider à éviter les faux positifs et à concentrer les tests sur les zones sensibles.
2.  **Génération et Exportation des Rapports**

    * **Commande** : Accédez à `Scans > Reports`, sélectionnez le rapport d'analyse, et exportez-le en PDF, HTML, ou CSV.

    **Explication** : Exporte les résultats de l’analyse pour une évaluation et une documentation plus approfondies. Les rapports contiennent des détails sur les vulnérabilités trouvées et les recommandations de correction.\
    **Discrétion** : Faible. Les rapports sont des documents statiques et n'affectent pas le trafic réseau.

**Exemples d'Analyses**

1.  **Analyse d’un Site pour les Injections SQL**

    * **Commande** : Configurez le scan pour inclure les tests de vulnérabilités SQL et lancez-le.

    **Explication** : Identifie les points faibles dans les formulaires et les paramètres de requêtes susceptibles d’être vulnérables aux injections SQL.\
    **Discrétion** : Moyenne. Les tests peuvent être détectés si les systèmes de sécurité surveillent les requêtes web.
2.  **Analyse pour les Vulnérabilités XSS**

    * **Commande** : Configurez le scan pour inclure des tests pour les vulnérabilités Cross-Site Scripting (XSS).

    **Explication** : Détecte les failles XSS dans les applications web en testant les entrées des utilisateurs et les réponses du serveur.\
    **Discrétion** : Moyenne. La recherche de vulnérabilités XSS peut générer un trafic spécifique et potentiellement alerter les systèmes de sécurité.
