# Guide de Codage — Audit SSI Clinique Santé Plus

Ce document explique le système de codage utilisé dans tous les livrables de l'audit pour faciliter la compréhension et la navigation.

---

## Codes des Constats (C-xxx)

Les constats sont numérotés de **C-001** à **C-007**. Chaque constat identifie un écart ou une vulnérabilité identifiée lors de l'audit.

**Exemples** :
- **C-001** : Absence de MFA obligatoire pour tous les comptes Microsoft 365
- **C-002** : Stratégie de sauvegarde incomplète et absence de test de restauration récent
- **C-003** : Retard dans l'application des correctifs de sécurité sur les postes de travail

---

## Codes des Recommandations (P-1, P-2, etc.)

Les recommandations sont numérotées de **P-1** à **P-7**. Chaque recommandation correspond à un constat et propose des actions correctives.

**Exemples** :
- **P-1** : Implémenter MFA obligatoire pour 100% des comptes M365 (correspond à C-001)
- **P-2** : Compléter stratégie sauvegarde (3-2-1) et tests trimestriels (correspond à C-002)
- **P-3** : Mettre en place gestion centralisée des correctifs (correspond à C-003)

---

## Priorités (P1, P2, P3)

Les recommandations sont classées par priorité selon leur criticité :

- **P1 — Critique** : Actions à traiter en priorité absolue (risques très élevés ou élevés)
- **P2 — Important** : Actions importantes mais moins urgentes (risques moyens)
- **P3 — Mineur** : Actions d'amélioration continue (risques faibles)

**Dans cet audit** :
- **P1** : 4 recommandations (P-1, P-2, P-3, P-5)
- **P2** : 3 recommandations (P-4, P-6, P-7)
- **P3** : Aucune (tous les constats identifiés nécessitent une action)

---

## Codes des Preuves (P-xxx)

Les preuves collectées sont numérotées de **P-001** à **P-030**. Chaque preuve est un élément factuel qui étaye un constat.

**Types de preuves** :
- **Documents** : Politiques, procédures, contrats (ex. P-001, P-022, P-027)
- **Exports** : Données exportées depuis les consoles (ex. P-002, P-004, P-023)
- **Captures** : Captures d'écran anonymisées (ex. P-003, P-018)
- **Observations** : Observations directes sur site (ex. P-012, P-016)

**Exemples** :
- **P-001** : Organigramme + rôles SI
- **P-002** : Export statut MFA des comptes utilisateurs
- **P-025** : PV test restauration

---

## Codes des Risques (R-xxx)

Les risques identifiés sont numérotés de **R-001** à **R-007**. Chaque risque est associé à un constat.

**Exemples** :
- **R-001** : Compromission comptes utilisateurs (phishing) — associé à C-001
- **R-002** : Perte définitive données critiques (ransomware/panne) — associé à C-002
- **R-005** : Incapacité à gérer incident majeur (ransomware) — associé à C-005

---

## Codes des Vérifications Techniques (V-xx)

Les vérifications techniques sont numérotées de **V-01** à **V-14**. Chaque vérification correspond à un contrôle technique non intrusif.

**Exemples** :
- **V-01** : MFA et durcissement des comptes Microsoft 365
- **V-06** : Postes : état des mises à jour
- **V-11** : Sauvegardes : stratégie 3-2-1

---

## Correspondances entre les codes

**Exemple pour le constat C-001** :
- **Constat** : C-001 (Absence de MFA obligatoire)
- **Risque associé** : R-001 (Compromission comptes utilisateurs)
- **Recommandation** : P-1 (Implémenter MFA obligatoire)
- **Priorité** : P1 — Critique
- **Preuves** : P-002, P-003, P-004, P-005
- **Vérification** : V-01

**Exemple pour le constat C-002** :
- **Constat** : C-002 (Stratégie sauvegarde incomplète)
- **Risque associé** : R-002 (Perte définitive données critiques)
- **Recommandation** : P-2 (Compléter stratégie sauvegarde)
- **Priorité** : P1 — Critique
- **Preuves** : P-022, P-023, P-024, P-025, P-026
- **Vérification** : V-11, V-12

---

## Où trouver ces codes dans les livrables

- **Constats détaillés** : `06_fiches_constats.md` (C-001 à C-007)
- **Recommandations** : `06_fiches_constats.md` et `07_rapport_audit.md` (P-1 à P-7)
- **Preuves** : `05_registre_preuves.csv` (P-001 à P-030)
- **Risques** : `07_rapport_audit.md` section 4 (R-001 à R-007)
- **Vérifications techniques** : `10_acces_outils_simules_et_verifications_techniques.md` (V-01 à V-14)

---

## Résumé visuel

```
Constat (C-xxx)
    ↓
Risque (R-xxx)
    ↓
Recommandation (P-x) avec Priorité (P1/P2/P3)
    ↓
Preuves (P-xxx) collectées via Vérifications (V-xx)
```

---

*Document de référence — Équipe Audit SSI — Efrei Paris*
