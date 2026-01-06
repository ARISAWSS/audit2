# Méthodes de Collecte des Preuves — Audit SSI Clinique Santé Plus

Ce document détaille les méthodes utilisées pour collecter les preuves lors de l'audit de la Clinique Santé Plus. L'objectif est de garantir la traçabilité, la crédibilité et la conformité de chaque preuve avec les principes d'un audit non intrusif.

---

## 1. Principes généraux de collecte des preuves

La collecte des preuves s'est appuyée sur une combinaison de techniques, toutes réalisées dans un cadre non intrusif et avec un souci constant d'anonymisation des données sensibles.

La revue documentaire a consisté à examiner les documents fournis par la Direction de la clinique et son prestataire IT. Cela inclut les politiques de sécurité, les procédures internes (RH, IT), les inventaires, les contrats avec les fournisseurs, les accords de traitement de données (DPA) et les attestations de certification (HDS). Les documents ont été transmis par email ou via un partage sécurisé, et les preuves correspondantes sont référencées P-001, P-006, P-022, P-027, P-029 et P-030.

Les exports depuis les consoles d'administration ont été réalisés avec les accès "lecture seule" simulés. Nous avons effectué des exports de données depuis les consoles d'administration de Microsoft 365, de l'application MedSimple, de la console EDR et de l'outil de sauvegarde. Ces exports sont généralement au format CSV ou PDF, et les preuves correspondantes sont P-002, P-004, P-005, P-008, P-010, P-014, P-015 et P-023.

Les captures d'écran ont été réalisées sur les interfaces des consoles d'administration (M365, MedSimple, pare-feu) et sur les postes de travail observés. Toutes les informations sensibles (identifiants, données patients, adresses IP) ont été systématiquement floutées ou masquées. Les preuves correspondantes sont P-003, P-009, P-018 et P-019.

Les observations sur site ont été effectuées en présence du référent SI de la clinique. Nous avons procédé à des observations directes sur un échantillon de postes de travail. Ces observations incluent la vérification visuelle de paramètres Windows (mises à jour, BitLocker, verrouillage de session) et l'exécution de commandes PowerShell de lecture seule. Les preuves correspondantes sont P-012, P-016 et P-017.

Les exercices et tests encadrés ont permis d'évaluer la réactivité face à des incidents. Nous avons mené un exercice "table-top" simulant un scénario de ransomware. Un test de restauration de données a également été demandé au prestataire IT et observé par l'équipe d'audit. Les preuves correspondantes sont P-025, P-026 et P-028.

---

## 2. Détail de la collecte pour les preuves clés

Chaque preuve est identifiée par un ID unique (P-xxx) et est référencée dans le registre de preuves (`05_registre_preuves.csv`). Voici comment certaines preuves clés ont été obtenues.

La preuve P-001 (Organigramme) a été fournie par la Direction de la Clinique Santé Plus lors de la réunion de cadrage du 2 décembre 2025. Ce document présente la structure organisationnelle et les rôles IT de la clinique.

La preuve P-002 (Export MFA M365) a été obtenue le 8 décembre 2025. Un export CSV a été réalisé depuis le Microsoft 365 Admin Center avec un rôle "Security Reader". La navigation s'est faite via Utilisateurs puis Authentification multifacteur. Les noms d'utilisateurs et emails ont été anonymisés dans l'export final.

La preuve P-003 (Politiques MFA M365) consiste en une capture d'écran des politiques de sécurité et d'authentification dans le Microsoft 365 Admin Center, réalisée le 8 décembre 2025. Les identifiants et informations sensibles ont été floutés.

La preuve P-004 (Comptes Admin M365) est un export CSV des comptes à privilèges depuis le Microsoft 365 Admin Center, réalisé le 8 décembre 2025. Les noms et emails ont été anonymisés.

La preuve P-012 (Windows Update Poste Accueil) a été obtenue lors d'une observation sur site le 12 décembre 2025. En présence du référent SI, nous avons accédé au poste d'accueil avec une session utilisateur standard. La navigation s'est faite via Paramètres puis Windows Update, et une capture d'écran de l'état des mises à jour a été réalisée. La commande `winver` a également été exécutée en lecture seule pour vérifier la version de l'OS.

La preuve P-014 (Couverture EDR) est un export CSV du rapport de couverture des postes par l'agent EDR, fourni par le prestataire IT depuis sa console d'administration le 13 décembre 2025. Les identifiants des postes ont été anonymisés.

La preuve P-016 (BitLocker Direction) a été obtenue lors d'une observation sur site le 12 décembre 2025. En présence du référent SI, nous avons accédé au poste de direction avec une session utilisateur standard. La commande PowerShell `Get-BitLockerVolume` a été exécutée en lecture seule (sans élévation de privilèges), et une capture d'écran du résultat a été réalisée.

La preuve P-018 (Config Wi‑Fi) est une capture d'écran de la configuration Wi‑Fi (SSID, WPA, WPS) depuis l'interface d'administration du routeur/pare-feu, réalisée le 14 décembre 2025. Les mots de passe et clés ont été masqués.

La preuve P-022 (Plan Sauvegarde) est un document "Plan de Sauvegarde" fourni par le prestataire IT le 5 décembre 2025. Ce document décrit la stratégie de sauvegarde, les fréquences, le périmètre et la rétention.

La preuve P-023 (Logs Sauvegardes) est un export CSV des logs de jobs de sauvegarde sur 30 jours, fourni par le prestataire IT depuis sa console de sauvegarde le 15 décembre 2025. Les chemins de fichiers sensibles ont été anonymisés.

La preuve P-025 (PV Test Restauration) est un procès-verbal de test de restauration fourni par le prestataire IT le 18 décembre 2025, suite à un test observé par l'équipe d'audit. Le test consistait à restaurer un fichier fictif depuis la sauvegarde NAS, et le PV a été validé par l'équipe d'audit.

La preuve P-027 (Procédure Incident) est un document "Procédure de Gestion des Incidents" fourni par la Clinique Santé Plus le 16 décembre 2025. Ce document décrit les étapes de gestion des incidents de sécurité.

La preuve P-028 (PV Exercice Ransomware) est un procès-verbal de l'exercice table-top "Ransomware" rédigé par l'équipe d'audit le 19 décembre 2025. L'exercice a duré 30 minutes et a réuni la Direction, le Référent SI, le Prestataire IT et l'Équipe audit. Le scénario simulait un ransomware chiffrant les postes et le NAS. L'équipe d'audit a animé l'exercice en posant des questions et en observant les réactions des participants. Le PV a été validé par tous les participants.

La preuve P-029 (Contrats DPA) consiste en des extraits des contrats avec les prestataires IT et l'hébergeur MedSimple, fournis par la Direction le 6 décembre 2025. Les noms des sociétés et les montants ont été anonymisés.

La preuve P-030 (Attestation HDS) est une attestation de certification HDS de l'hébergeur MedSimple, fournie par la Direction le 6 décembre 2025. Le numéro d'attestation a été partiellement anonymisé.

---

## 3. Précautions et garanties

Tout au long de la collecte, nous avons veillé à maintenir une approche **non intrusive**, en nous limitant à la lecture et à l'observation. Aucune action intrusive n'a été réalisée : pas de scans agressifs, pas d'exploitation de vulnérabilités. Tous les accès ont été en lecture seule, sans possibilité de modification des systèmes.

L'**anonymisation systématique** des données sensibles a été appliquée pour protéger la confidentialité. Les identifiants, emails, données patients, adresses IP et autres informations sensibles ont été floutés ou masqués dans toutes les preuves.

La **traçabilité** de chaque preuve a été garantie en la liant aux constats et aux recommandations. Chaque preuve est référencée dans le registre de preuves avec sa date, sa source, son type et son association aux constats correspondants.

Ces méthodes permettent de construire un dossier de preuves solide et crédible, même dans un contexte d'audit fictif, en respectant les principes d'indépendance, d'objectivité et de non-intrusion.
