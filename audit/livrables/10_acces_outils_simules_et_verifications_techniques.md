# Accès et outils simulés — Vérifications techniques

Audit SSI — Clinique Santé Plus  
Période : 01/12/2025 → 05/01/2026

## SI fictif — Architecture

### Organisation
- Petite clinique (≈ 15 employés) : accueil, secrétariat, médecins, facturation, direction
- 1 site principal, 1 baie réseau
- Volume : ≈ 50 patients/jour

### Actifs
- Postes : 8 PC Windows 11 Pro (accueil x2, secrétariat x2, médecins x3, direction x1)
- Réseau : 1 pare-feu/routeur avec Wi‑Fi, 1 switch manageable
- SSID : `SANTEPLUS-INTERNE` et `SANTEPLUS-INVITES`
- Application : MedSimple (SaaS, gestion dossiers patients)
- Messagerie : Microsoft 365 (Exchange Online) + OneDrive/SharePoint
- Sauvegardes : quotidienne M365, hebdomadaire NAS, copie hors site hebdo
- Prestataire IT : maintenance + supervision AV/patch

## Accès simulés (lecture seule)

### Consoles
1. Microsoft 365 Admin Center — rôle "Security Reader / Reports Reader"
2. Portail MedSimple (admin lecture)
3. Console antivirus/EDR prestataire (lecture)
4. Console sauvegardes (lecture)
5. Interface pare-feu/routeur (lecture)

### Terrain
- Accès accompagné à 3 postes échantillons (accueil, médecin, direction)
- Vérification visuelle des paramètres (Windows Update, BitLocker, antivirus, verrouillage session)
- Sans installation d'outil, sans scan agressif

## Vérifications techniques (14 vérifications)

### V-01 — MFA et durcissement des comptes Microsoft 365
- Export liste utilisateurs + statut MFA
- Vérifier admins avec MFA obligatoire
- Preuves : P-002, P-003

### V-02 — Comptes à privilèges
- Liste admins
- Vérifier comptes séparés (admin ≠ user), logs connexions
- Preuves : P-004, P-005

### V-03 — Gestion des entrées/sorties
- Échantillon 3 mouvements RH fictifs
- Vérifier création/suppression comptes
- Preuves : P-006, P-007

### V-04 — Rôles & permissions MedSimple
- Export rôles
- Vérifier séparation Accueil/Médecin/Admin
- Preuves : P-008, P-009

### V-05 — Journalisation accès applicatif
- Vérifier logs d'accès, durée rétention
- Preuves : P-010, P-011

### V-06 — Postes : état des mises à jour
- Sur 3 postes échantillons, vérifier Windows Update + date dernier patch
- Preuves : P-012, P-013

### V-07 — Postes : antivirus/EDR
- Console EDR lecture
- Vérifier 100% postes couverts, alertes 90 jours
- Preuves : P-014, P-015

### V-08 — Chiffrement disque et verrouillage session
- Vérifier BitLocker et verrouillage auto
- Preuves : P-016, P-017

### V-09 — Wi‑Fi : chiffrement, WPS, isolation invité
- Interface routeur
- Vérifier WPA2/3, WPS désactivé, VLAN/règles
- Preuves : P-018, P-019

### V-10 — Pare-feu : exposition Internet
- Revue règles + NAT
- Vérifier services exposés
- Preuves : P-020, P-021

### V-11 — Sauvegardes : stratégie 3-2-1
- Console backup
- Vérifier fréquence, rétention, offsite, chiffrement
- Preuves : P-022, P-023, P-024

### V-12 — Test de restauration
- Demander PV test
- Sinon réaliser table-top + restauration fictive encadrée
- Preuves : P-025, P-026

### V-13 — Incidents : procédure + exercice ransomware
- Revue procédure, arbre d'appel
- Exercice 30 min
- Preuves : P-027, P-028

### V-14 — Fournisseurs : clauses RGPD
- Revue contrats/DPA
- Vérifier notification incident, sous-traitants ultérieurs
- Preuves : P-029, P-030

## Outils autorisés (non intrusifs)

- Export natif des consoles (CSV/PDF)
- Captures d'écran anonymisées
- Commandes lecture seule : `winver`, `systeminfo`, `Get-BitLockerVolume`, `Get-MpComputerStatus`

## Interdits

- Nmap agressif, exploitation, brute force, phishing réel, DoS, exploitation de failles
