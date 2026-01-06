# Rapport d'Audit de Sécurité des Systèmes d'Information (SSI)
**Clinique Santé Plus**

**Date : 5 janvier 2026** | **Équipe Audit SSI — Efrei Paris**

---

## Table des matières

1. [Résumé exécutif](#résumé-exécutif)
2. [Contexte et périmètre](#contexte-et-périmètre)
3. [Méthodologie](#méthodologie)
4. [Analyse des risques](#analyse-des-risques)
5. [Constats détaillés](#constats-détaillés)
6. [Recommandations et plan d'actions](#recommandations-et-plan-dactions)
7. [Conclusion](#conclusion)
8. [Annexes](#annexes)

---

## 1. Résumé exécutif

Le présent rapport synthétise les résultats de l'audit de sécurité des systèmes d'information (SSI) mené auprès de la **Clinique Santé Plus** du 1er décembre 2025 au 5 janvier 2026. L'objectif principal de cette mission était d'évaluer le niveau de sécurité du système d'information, d'identifier les risques majeurs et de proposer des recommandations concrètes et adaptées à la taille et aux moyens de la clinique.

La Clinique Santé Plus, en tant qu'établissement de santé de petite taille, manipule quotidiennement des données sensibles soumises au RGPD et aux exigences d'hébergement de données de santé (HDS). Le contexte actuel, marqué par une recrudescence des cyberattaques ciblant le secteur de la santé, rend cette évaluation d'autant plus cruciale.

Notre audit, réalisé selon une approche non intrusive et basée sur les référentiels ISO 27001/27002, RGPD et les guides de l'ANSSI, a permis d'identifier **7 constats majeurs**, dont **4 sont classés comme critiques (P1)** et **3 comme importants (P2)**. Ces constats révèlent des vulnérabilités significatives, notamment en matière d'authentification multifacteur (MFA), de stratégie de sauvegarde, de gestion des correctifs de sécurité et de procédure de gestion des incidents.

Les risques associés à ces constats sont principalement liés à la **compromission des comptes utilisateurs**, à la **perte définitive de données critiques**, à l'**exploitation de vulnérabilités connues** et à l'**incapacité à gérer efficacement un incident majeur**. Ces risques pourraient entraîner des impacts très élevés sur la confidentialité, l'intégrité et la disponibilité des données patients et des services de la clinique, avec des conséquences financières, réglementaires et réputationnelles importantes.

Un **plan d'actions priorisé** est proposé, détaillant des mesures concrètes, des responsabilités claires et des échéances réalistes. La mise en œuvre rapide de ces recommandations, notamment celles classées P1, est essentielle pour renforcer la posture de sécurité de la clinique et réduire son exposition aux cybermenaces.

Nous remercions la Direction et le personnel de la Clinique Santé Plus pour leur collaboration et leur transparence tout au long de cette mission.

---

## 2. Contexte et périmètre

### 2.1 Présentation de l'organisation

La **Clinique Santé Plus** est une clinique médicale de petite taille (environ 15 employés) qui assure des soins médicaux généraux et des analyses biologiques. Elle gère quotidiennement des **données de santé sensibles** (dossiers patients, informations administratives) soumises au **RGPD** et aux exigences d'**Hébergement de Données de Santé (HDS)**.

Le contexte réglementaire est marqué par le **RGPD**, qui impose des obligations strictes en matière de sécurité (art. 32), de notification des violations (art. 33-34) et de tenue d'un registre des traitements (art. 30). L'hébergement des données de santé par un prestataire certifié HDS est également une exigence clé. Le secteur de la santé est par ailleurs une cible privilégiée des cyberattaques, notamment les ransomwares et les fuites de données, ce qui souligne l'importance cruciale de cet audit.

### 2.2 Périmètre de l'audit

L'audit a porté sur les éléments suivants. Les systèmes informatiques incluent huit postes de travail sous Windows 11 Pro, le réseau interne (filaire et Wi‑Fi), l'application SaaS de gestion des patients "MedSimple", et l'environnement Microsoft 365 (messagerie, stockage de documents). Les processus examinés concernent la gestion des accès (pour M365 et MedSimple), les procédures de sauvegarde et de restauration, la gestion des incidents de sécurité, et la conformité aux exigences du RGPD et de l'HDS. L'organisation a également été analysée, notamment les rôles et responsabilités de la Direction, du prestataire IT externe, et des utilisateurs métiers.

Les éléments suivants ont été explicitement exclus du périmètre de l'audit. Les tests d'intrusion et toute forme d'action intrusive (exploitation de vulnérabilités, déni de service, etc.) n'ont pas été réalisés. Les audits physiques détaillés des locaux (contrôle d'accès physique, vidéosurveillance, etc.) ont également été exclus. Enfin, les systèmes externes non directement maîtrisés par la clinique, au-delà des interfaces visibles et des exigences contractuelles ou documentaires disponibles, n'ont pas fait l'objet d'une analyse approfondie.

### 2.3 Référentiels utilisés

L'audit s'est appuyé sur les référentiels suivants. La norme **ISO/IEC 27001:2022** a servi de cadre pour le management de la sécurité de l'information (clauses 4 à 10). La norme **ISO/IEC 27002:2022** a fourni les bonnes pratiques de sécurité, avec une sélection de contrôles pertinents pour une petite structure. Le **RGPD** (Règlement Général sur la Protection des Données) a été utilisé pour vérifier la conformité réglementaire, notamment les articles 28, 30, 32, 33 et 34. Les recommandations de l'**ANSSI** (Agence Nationale de la Sécurité des Systèmes d'Information), notamment les guides sur l'hygiène informatique, ont également été consultées. Enfin, le référentiel **HDS** (Hébergement de Données de Santé) a été vérifié via l'attestation du prestataire.

---

## 3. Méthodologie

### 3.1 Approche d'audit

L'audit a été mené selon une approche **non intrusive** et **factuelle**, en conformité avec les principes de la norme ISO 19011 (lignes directrices pour l'audit des systèmes de management).

Les principes fondamentaux de notre démarche ont été l'indépendance, l'objectivité, la confidentialité et la non-intrusion. L'équipe d'audit est externe à la clinique (étudiants de l'Efrei Paris), garantissant une évaluation impartiale. Tous les constats formulés sont basés sur des preuves tangibles et vérifiables, avec un total de 30 preuves collectées. Toutes les informations sensibles collectées ont été traitées de manière confidentielle et anonymisées dans les livrables. Enfin, aucune action intrusive n'a été réalisée. Les vérifications techniques se sont limitées à des observations, des revues de configuration en lecture seule et des exports de rapports.

### 3.2 Techniques d'audit utilisées

Pour collecter les informations nécessaires, nous avons utilisé une combinaison de techniques. La revue documentaire a consisté en l'examen des politiques de sécurité, procédures internes, inventaires d'actifs, contrats avec les prestataires, accords de traitement de données (DPA) et attestations HDS. Les entretiens ont permis des discussions avec la Direction, le référent SI de la clinique, le prestataire IT externe, et des utilisateurs métiers pour comprendre les processus et les pratiques. Les observations techniques ont permis la vérification des configurations sur les postes de travail, le réseau, et les consoles d'administration (M365, MedSimple, EDR, sauvegardes) en mode lecture seule. Les exports et rapports ont fourni des données issues des systèmes d'information (listes d'utilisateurs, statuts MFA, logs de connexion, rapports de couverture EDR, logs de sauvegarde), toutes anonymisées. Enfin, un exercice table-top a été réalisé, simulant un scénario de crise (ransomware) avec les équipes clés pour évaluer la réactivité et la pertinence des procédures existantes.

### 3.3 Échantillonnage

Afin d'obtenir une vision représentative sans être exhaustive, un échantillonnage a été effectué. Trois postes de travail ont été observés sur un total de huit (un poste d'accueil, un poste de médecin, un poste de direction). Six comptes Microsoft 365 ont été examinés (trois créés récemment, trois plus anciens) sur un total d'environ quinze. Trois profils de l'application MedSimple ont été analysés (accueil, médecin, administrateur) sur un total de cinq. Enfin, deux à trois contrats avec les prestataires clés (IT, hébergeur MedSimple) ont été revus.

### 3.4 Preuves collectées

Au total, **30 preuves** ont été collectées et sont référencées de manière détaillée dans le registre de preuves (`05_registre_preuves.csv`). Ces preuves se répartissent comme suit : douze documents (politiques, procédures, contrats, DPA), dix exports de données (M365, MedSimple, EDR, sauvegardes), six captures d'écran (configurations, paramètres, logs), et deux observations directes (postes, test de restauration).

Il est important de souligner que toutes les preuves contenant des informations sensibles (identifiants, données patients, adresses IP) ont été **anonymisées** pour garantir la confidentialité.

---

## 4. Analyse des risques

### 4.1 Méthode d'évaluation

Les risques identifiés ont été évalués en utilisant une **matrice de criticité** standard, qui combine deux facteurs principaux. L'impact correspond à l'ampleur des conséquences négatives si le risque se matérialise, évalué comme Faible, Moyen, Élevé ou Très élevé. La probabilité correspond à la vraisemblance que le risque se produise, évaluée comme Faible, Moyenne ou Élevée. La **Criticité** du risque est ensuite déterminée par la combinaison de l'Impact et de la Probabilité, permettant de prioriser les actions correctives.

### 4.2 Cartographie des risques

Le tableau ci-dessous présente la cartographie des risques identifiés, associés aux constats correspondants :

| ID | Risque | Impact | Probabilité | Criticité | Constat associé |
|---|---|---|---|---|---|
| **R-001** | Compromission comptes utilisateurs (phishing) | Élevé | Moyenne | **Élevée** | C-001 |
| **R-002** | Perte définitive données critiques (ransomware/panne) | Très élevé | Moyenne | **Très élevée** | C-002 |
| **R-003** | Exploitation de vulnérabilités connues (malware) | Élevé | Moyenne | **Élevée** | C-003 |
| **R-004** | Accès non autorisé au réseau interne (Wi‑Fi invité) | Moyen | Moyenne | **Moyenne** | C-004 |
| **R-005** | Incapacité à gérer incident majeur (ransomware) | Très élevé | Moyenne | **Très élevée** | C-005 |
| **R-006** | Non-conformité RGPD (sous-traitants) | Moyen | Faible | **Moyenne** | C-006 |
| **R-007** | Accès non autorisé aux postes sans surveillance | Moyen | Faible | **Moyenne** | C-007 |

### 4.3 Analyse des risques critiques

Le risque le plus critique identifié concerne la **perte définitive de données critiques** (R-002). Le scénario envisagé serait qu'un ransomware chiffre les postes et le NAS local. La restauration depuis la copie hors site n'aurait pas été testée récemment et échouerait, entraînant une perte définitive des données. L'impact serait très élevé, incluant la perte de dossiers patients, l'interruption des soins, la non-conformité RGPD/HDS, et potentiellement l'arrêt d'activité. Les mesures existantes incluent des sauvegardes quotidiennes M365, hebdomadaires vers le NAS, et une copie hors site. Les mesures recommandées consistent à mettre en place des tests de restauration trimestriels, vérifier le chiffrement de la copie hors site, et ajouter un export dédié de MedSimple.

Le deuxième risque critique concerne l'**incapacité à gérer efficacement un incident majeur** (R-005). Le scénario serait qu'un ransomware chiffre les systèmes de la clinique. L'équipe ne saurait pas qui contacter en priorité, ne respecterait pas le délai de notification à la CNIL (72 heures), et communiquerait mal aux patients. L'impact serait très élevé, avec violation du RGPD, sanctions potentielles de la CNIL, perte de confiance des patients, et interruption prolongée de l'activité. Les mesures existantes incluent une procédure d'incidents existante mais incomplète, et un exercice table-top qui a révélé des lacunes. Les mesures recommandées consistent à compléter la procédure avec des délais clairs, un RACI détaillé, créer un kit de crise, et organiser des exercices trimestriels.

Le troisième risque majeur concerne la **compromission des comptes utilisateurs** (R-001). Le scénario serait qu'un attaquant obtienne les identifiants d'un utilisateur via un email de phishing. Sans MFA, l'accès au compte serait immédiat, permettant l'exfiltration de données patients ou l'accès à MedSimple. L'impact serait élevé, avec accès non autorisé aux données de santé, violation du RGPD, et interruption d'activité. Les mesures existantes montrent que la MFA est activée pour les administrateurs mais seulement pour 40% des utilisateurs. Les mesures recommandées consistent à implémenter une politique de Conditional Access imposant la MFA obligatoire pour 100% des comptes.

---

## 5. Constats détaillés

Cette section présente les constats identifiés lors de l'audit, chacun étant étayé par des preuves concrètes et une analyse des risques associée. Les recommandations détaillées sont présentées dans la section suivante.

*(Se référer au document `06_fiches_constats.md` pour le détail complet de chaque constat, incluant les critères de référence, les observations, les preuves, les risques identifiés et les recommandations.)*

**Synthèse des constats** :

| ID | Constat | Criticité |
|---|---|---|
| C-001 | Absence de MFA obligatoire pour tous les comptes Microsoft 365 | Élevée |
| C-002 | Stratégie de sauvegarde incomplète et absence de test de restauration récent | Très élevée |
| C-003 | Retard dans l'application des correctifs de sécurité sur les postes de travail | Élevée |
| C-004 | Isolation insuffisante du réseau Wi‑Fi invité et WPS activé | Moyenne |
| C-005 | Procédure de gestion des incidents de sécurité incomplète et non testée régulièrement | Très élevée |
| C-006 | Clauses RGPD incomplètes dans les contrats avec les sous-traitants | Moyenne |
| C-007 | Absence de politique de verrouillage automatique des sessions sur les postes de travail | Moyenne |

---

## 6. Recommandations et plan d'actions

Les recommandations sont classées par priorité (P1 : Critique, P2 : Important, P3 : Mineur) et incluent des actions détaillées, les responsables, les échéances estimées et les coûts associés.

*(Se référer au document `06_fiches_constats.md` pour le détail complet des recommandations associées à chaque constat.)*

**Plan d'actions priorisé** :

| ID | Recommandation | Priorité | Échéance | Responsable | Coût estimé |
|---|---|---|---|---|---|
| **P-1** | Implémenter MFA obligatoire pour 100% des comptes M365 | P1 | 31/01/2026 | Prestataire IT / Direction | 0€ |
| **P-2** | Compléter stratégie sauvegarde (3-2-1) et tests trimestriels | P1 | 28/02/2026 | Prestataire IT / Direction | 500€/an |
| **P-3** | Mettre en place gestion centralisée des correctifs (patch management) | P1 | 15/02/2026 | Prestataire IT / Direction | 0-500€/an |
| **P-4** | Renforcer isolation Wi‑Fi invité et désactiver WPS | P2 | 31/01/2026 | Prestataire IT / Direction | 0€ |
| **P-5** | Élaborer procédure gestion incidents complète et exercices réguliers | P1 | 15/02/2026 | Direction / Prestataire IT | 0-200€ |
| **P-6** | Mettre à jour clauses RGPD (Art. 28) dans contrats sous-traitants | P2 | 28/02/2026 | Direction / Juridique | 0-500€ |
| **P-7** | Implémenter politique verrouillage automatique sessions (5 min) | P2 | 31/01/2026 | Prestataire IT / Direction | 0€ |

Le planning de mise en œuvre prévoit que les actions P-1, P-4 et P-7 soient traitées en janvier 2026, les actions P-3 et P-5 en février 2026, et les actions P-2 et P-6 en fin février 2026. Un suivi est prévu en mars 2026 pour vérifier la mise en œuvre, réaliser les premiers tests de restauration et organiser un exercice d'incident.

Le coût total estimé pour la mise en œuvre de toutes ces recommandations s'élève à **0€ à 1000€**, principalement pour la configuration et la rédaction interne. La majorité des actions ne nécessitent pas d'investissement financier significatif, ce qui rend ce plan d'actions particulièrement adapté à une structure de petite taille comme la Clinique Santé Plus.

---

## 7. Conclusion

Cet audit a mis en lumière des points forts dans la gestion de la sécurité de la Clinique Santé Plus, notamment la prise de conscience des enjeux SSI et la collaboration avec un prestataire IT. Cependant, des axes d'amélioration significatifs ont été identifiés, nécessitant une attention particulière et une mise en œuvre rapide des recommandations.

La priorisation des actions proposées vise à adresser en premier lieu les risques les plus critiques pour la clinique, en se concentrant sur des mesures à fort impact et à coût maîtrisé. La Direction est encouragée à s'approprier ce plan d'actions et à en assurer le suivi régulier.

Un renforcement de la posture de sécurité permettra à la Clinique Santé Plus de mieux protéger les données de santé de ses patients, de garantir la continuité de ses services et de se conformer pleinement aux exigences réglementaires, renforçant ainsi la confiance de ses patients et partenaires.

---

## 8. Annexes

### 8.1 Liste des documents de référence

- **01_lettre_de_mission.md** : Lettre de mission (S1)
- **02_note_de_cadrage.md** : Note de cadrage (S1)
- **03_programme_audit.csv** : Programme d'audit (20 contrôles)
- **04_journal_de_bord.csv** : Journal de bord (S2-S4)
- **05_registre_preuves.csv** : Registre de preuves (30 preuves)
- **06_fiches_constats.md** : Fiches constats détaillées (7 constats)
- **10_acces_outils_simules_et_verifications_techniques.md** : Vérifications techniques (14 vérifications)
- **11_methodes_collecte_preuves.md** : Méthodes de collecte des preuves

### 8.2 Glossaire

- **MFA** : Multi-Factor Authentication (Authentification multifacteur)
- **RTO** : Recovery Time Objective (Objectif de temps de récupération)
- **RPO** : Recovery Point Objective (Objectif de point de récupération)
- **DPA** : Data Processing Agreement (Contrat de traitement de données)
- **HDS** : Hébergement de Données de Santé
- **EDR** : Endpoint Detection and Response (Détection et réponse sur les terminaux)
- **GPO** : Group Policy Object (Objet de stratégie de groupe)

### 8.3 Références réglementaires

- **ISO/IEC 27001:2022** : Information security management systems — Requirements
- **ISO/IEC 27002:2022** : Information security controls
- **RGPD** : Règlement (UE) 2016/679 du 27 avril 2016
- **ANSSI** : Agence Nationale de la Sécurité des Systèmes d'Information
- **HDS** : Référentiel Hébergement de Données de Santé (certification)

---

**Fin du rapport**

*Document préparé par l'Équipe Audit SSI — Efrei Paris*  
*Date de finalisation : 5 janvier 2026*
