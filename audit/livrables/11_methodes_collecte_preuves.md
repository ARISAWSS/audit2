# Méthodes de collecte des preuves

Date : 5 janvier 2026  
Équipe Audit SSI — Efrei Paris

## Méthodes générales

### Revue documentaire
Documents fournis par la Direction / Référent SI par email ou partage sécurisé.  
Preuves : P-001, P-006, P-022, P-027, P-029, P-030

### Exports depuis consoles (lecture seule)
Accès "Security Reader" / "Reports Reader" aux consoles avec comptes temporaires.  
Preuves : P-002, P-004, P-005, P-008, P-010, P-014, P-015, P-023

### Captures d'écran (lecture seule)
Captures depuis consoles / interfaces avec floutage identifiants.  
Preuves : P-003, P-009, P-018, P-019

### Observations sur site (non intrusives)
Accès accompagné à des postes échantillons, observation visuelle + commandes lecture seule.  
Preuves : P-012, P-016, P-017

### Exercices / Tests encadrés
Exercices table-top ou tests de restauration encadrés en présence équipe audit.  
Preuves : P-025, P-026, P-028

## Détail par preuve

### P-002 : Export statut MFA
- Connexion M365 Admin Center (rôle Security Reader)
- Navigation : Utilisateurs → Authentification multifacteur
- Export CSV de la liste des utilisateurs avec statut MFA
- Anonymisation : Emails remplacés par noms fictifs

### P-012 : Captures Windows Update (poste accueil)
- Présence sur site avec Référent SI
- Accès au poste accueil (session utilisateur standard)
- Navigation : Paramètres → Windows Update
- Capture d'écran de l'état des mises à jour
- Commande `winver` (lecture seule) pour version OS

### P-016 : État BitLocker (poste direction)
- Présence sur site avec Référent SI
- Accès au poste direction (session utilisateur standard)
- Commande PowerShell : `Get-BitLockerVolume` (lecture seule, pas d'élévation)
- Capture d'écran du résultat

### P-025 : PV test restauration
- Demande de test de restauration au prestataire
- Test réalisé en présence équipe audit (observation)
- Restauration d'un fichier fictif depuis sauvegarde NAS
- PV rédigé par prestataire (validé équipe audit)

### P-028 : PV exercice table-top ransomware
- Organisation exercice table-top (30 min)
- Participants : Direction, Référent SI, Prestataire IT, Équipe audit
- Scénario : Ransomware chiffre postes et NAS
- Animation : Équipe audit (questions, observation réactions)
- PV rédigé par équipe audit (validé participants)

## Précautions

- Aucune action intrusive : pas de scans agressifs, pas d'exploitation
- Lecture seule : tous les accès en lecture seule (pas de modification)
- Accompagnement : observations sur site avec Référent SI
- Anonymisation : identifiants, emails, IP masqués

## Traçabilité

- Registre de preuves : toutes les preuves référencées (P-001 à P-030)
- Journal de bord : toutes les activités tracées (dates, participants)
- Lien preuve ↔ constat : chaque constat référence ses preuves
