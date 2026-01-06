# Accès et Vérifications Techniques (non intrusives) — Audit SSI Clinique Santé Plus

Ce document décrit le système d'information (SI) fictif de la Clinique Santé Plus, les accès simulés accordés aux auditeurs, les outils autorisés, et la liste des vérifications techniques réalisées. L'objectif est de montrer une approche technique rigoureuse mais strictement non intrusive, conforme aux exigences de l'audit.

---

## 1. Le SI fictif de la Clinique Santé Plus

La Clinique Santé Plus est une petite structure d'environ 15 employés. Son infrastructure informatique est typique d'une PME du secteur médical.

Le parc informatique comprend huit postes de travail sous Windows 11 Pro, répartis entre l'accueil (deux postes), le secrétariat (deux postes), les médecins (trois postes) et la direction (un poste). Le réseau interne est composé d'un pare-feu/routeur avec Wi‑Fi et d'un switch manageable. Deux réseaux Wi‑Fi distincts sont configurés : `SANTEPLUS-INTERNE` pour le personnel et `SANTEPLUS-INVITES` pour les visiteurs.

L'application principale utilisée est "MedSimple", une solution SaaS de gestion des dossiers patients. La messagerie et le stockage de documents sont assurés par Microsoft 365 (Exchange Online, OneDrive et SharePoint). Les sauvegardes sont organisées en trois niveaux : sauvegardes quotidiennes automatiques des données M365, sauvegardes hebdomadaires des postes critiques vers un NAS local, et une copie hors site hebdomadaire chiffrée via un prestataire externe.

Un prestataire IT externe assure la maintenance du parc informatique, la supervision antivirus/EDR et la gestion des mises à jour. Les comptes utilisateurs sont nominatifs pour Microsoft 365, et des rôles spécifiques existent dans MedSimple (Accueil, Médecin, Admin applicatif). Trois comptes d'administration sont identifiés : deux pour le prestataire IT et un pour la direction de la clinique.

---

## 2. Accès simulés pour l'audit (lecture seule)

Pour réaliser les vérifications techniques, les auditeurs ont eu accès à des interfaces en mode "lecture seule", simulant des droits d'observation sans modification possible.

L'accès au Microsoft 365 Admin Center a été accordé avec un rôle "Security Reader / Reports Reader", permettant d'exporter des listes d'utilisateurs, des statuts MFA, des politiques de sécurité et des rapports de connexion. Le portail MedSimple a été accessible en mode "admin lecture" pour exporter les rôles, les permissions, les journaux d'accès et les paramètres de sécurité. La console antivirus/EDR du prestataire a été consultée en lecture seule pour vérifier la couverture des postes, les mises à jour des signatures et les alertes récentes. La console de sauvegardes (NAS ou outil prestataire) a été accessible en lecture seule pour consulter les jobs, les statuts de succès/échec, la rétention et les logs. Enfin, l'interface du pare-feu/routeur a été consultée en lecture seule pour exporter la configuration, les règles, les réseaux et les paramètres Wi‑Fi.

Des **observations sur site** ont également été réalisées sur 3 postes échantillons (accueil, médecin, direction), en présence du référent SI, pour vérifier visuellement les paramètres (Windows Update, BitLocker, antivirus, verrouillage de session), sans installation d'outils ni actions intrusives.

---

## 3. Outils autorisés (non intrusifs)

Les outils utilisés sont des outils standards de consultation et d'export, garantissant l'absence d'intrusion.

Les outils bureautiques incluent les exports natifs des consoles (CSV, PDF) et les captures d'écran anonymisées (floutage des identifiants, données patients, IP si nécessaire). Sur les postes Windows observés, seules des commandes de lecture ont été autorisées, comme `winver` (version OS), `systeminfo`, `Get-BitLockerVolume` (état chiffrement) ou `Get-MpComputerStatus` (état Defender). Les vérifications via l'interface utilisateur (Windows Update, pare-feu, verrouillage écran) sont également autorisées.

Il est formellement **interdit** d'utiliser des outils intrusifs tels que Nmap agressif, des outils d'exploitation de vulnérabilités, de brute force, de phishing réel, ou de déni de service.

---

## 4. Liste des vérifications techniques (non intrusives)

Chaque vérification a été conçue pour produire des preuves concrètes (référencées par un ID P-xxx) et alimenter les constats d'audit (C-xxx).

La première vérification concernait la MFA et le durcissement des comptes Microsoft 365. Nous avons vérifié l'activation de la MFA pour les utilisateurs et les administrateurs via l'export des statuts et les politiques de Conditional Access. Cette vérification a produit les preuves P-002, P-003 et P-004.

La deuxième vérification portait sur les comptes à privilèges. Nous avons identifié le nombre de comptes administrateurs, vérifié l'usage de comptes séparés et la traçabilité des connexions. Les preuves collectées sont P-004 et P-005.

La troisième vérification concernait la gestion des entrées/sorties (onboarding/offboarding). Nous avons examiné les procédures RH et IT pour la création et la suppression des comptes, en échantillonnant trois mouvements fictifs. Les preuves sont P-006 et P-007.

La quatrième vérification portait sur les rôles et permissions dans MedSimple. Nous avons revu les rôles applicatifs pour s'assurer du principe du moindre privilège. Les preuves collectées sont P-008 et P-009.

La cinquième vérification concernait la journalisation des accès applicatifs. Nous avons vérifié l'existence, la rétention et l'accessibilité des logs d'accès dans MedSimple. Les preuves sont P-010 et P-011.

La sixième vérification portait sur l'état des mises à jour des postes. Nous avons observé les dates de dernier patch Windows Update sur les postes échantillons. Les preuves collectées sont P-012 et P-013.

La septième vérification concernait l'antivirus/EDR, la couverture et les alertes. Nous avons consulté la console EDR pour la couverture des postes et le traitement des alertes. Les preuves sont P-014 et P-015.

La huitième vérification portait sur le chiffrement disque et le verrouillage de session. Nous avons vérifié l'activation de BitLocker et les délais de verrouillage automatique des sessions. Les preuves collectées sont P-016 et P-017.

La neuvième vérification concernait le Wi‑Fi : chiffrement, WPS, et isolation invité. Nous avons revu la configuration Wi‑Fi (WPA2/3, désactivation WPS) et l'isolation du réseau invité. Les preuves sont P-018 et P-019.

La dixième vérification portait sur le pare-feu et l'exposition Internet. Nous avons examiné les règles du pare-feu pour identifier les services exposés et les règles de filtrage. Les preuves collectées sont P-020 et P-021.

La onzième vérification concernait les sauvegardes : stratégie 3-2-1, rétention, hors site. Nous avons vérifié le plan de sauvegarde (fréquence, rétention, copie hors site, chiffrement). Les preuves sont P-022, P-023 et P-024.

La douzième vérification portait sur le test de restauration. Nous avons demandé une preuve d'un test de restauration récent ou réalisé un exercice table-top. Les preuves collectées sont P-025 et P-026.

La treizième vérification concernait les incidents : procédure et exercice ransomware. Nous avons revu la procédure de gestion des incidents et réalisé un exercice table-top. Les preuves sont P-027 et P-028.

Enfin, la quatorzième vérification portait sur les fournisseurs : clauses RGPD (art. 28) et HDS. Nous avons examiné les contrats et les DPA avec les prestataires pour la conformité RGPD et HDS. Les preuves collectées sont P-029 et P-030.

---

## 5. Sorties attendues

Ces vérifications techniques ont permis de collecter les preuves nécessaires pour alimenter le registre de preuves (`05_registre_preuves.csv`), formuler des constats factuels dans les fiches constats (`06_fiches_constats.md`), et contribuer à la cartographie des risques et au plan d'actions du rapport d'audit (`07_rapport_audit.md`).
