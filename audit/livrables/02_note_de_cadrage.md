# Note de cadrage — Audit SSI
**Clinique Santé Plus**

Date : 24 décembre 2025  
Préparée par : Équipe Audit SSI — Efrei Paris

## Compréhension du contexte, enjeux et faisabilité

### Contexte organisationnel

La Clinique Santé Plus est une clinique de petite taille, comptant environ 10 à 20 employés et accueillant environ 50 patients par jour. Elle assure des consultations médicales et des actes biologiques. Le système d'information qu'elle exploite est composé de plusieurs éléments typiques d'une structure de cette taille. On y trouve des postes de travail répartis entre l'accueil, le secrétariat, les médecins et la comptabilité. La messagerie et les outils bureautiques sont utilisés quotidiennement. Une application de gestion des patients, appelée "MedSimple", est au cœur des activités. Le réseau local comprend un switch, un routeur, un accès Wi‑Fi et une connexion Internet. Des sauvegardes sont réalisées sur support local et/ou cloud. Enfin, plusieurs prestataires interviennent pour la maintenance informatique, l'édition du logiciel et l'hébergement.

### Données traitées et contraintes réglementaires

Les données manipulées par la clinique incluent des données personnelles et des données de santé, qui constituent des catégories particulières au sens du RGPD. En conséquence, plusieurs référentiels réglementaires s'appliquent. Le RGPD impose des principes de sécurité, de confidentialité, de minimisation, de traçabilité et de gestion des violations. Des exigences de contractualisation avec les sous-traitants sont également prévues aux articles 28 et suivants. En cas d'hébergement de données de santé par un prestataire, les exigences HDS doivent être vérifiées au niveau contractuel et documentaire, notamment les attestations, clauses et responsabilités.

### Enjeux SSI

Les enjeux de sécurité des systèmes d'information pour la clinique sont multiples et critiques. La confidentialité est essentielle, car une fuite de dossiers patients pourrait entraîner une atteinte au secret médical, des sanctions réglementaires et une perte de confiance des patients. L'intégrité des données est également cruciale, car une altération de données médicales ou administratives pourrait engendrer des risques cliniques et des erreurs de facturation. Enfin, la disponibilité du système est vitale, car une interruption de soins due à un rançongiciel ou une panne pourrait entraîner une perte de productivité et le report de rendez-vous.

### Faisabilité et niveau d'assurance visé

La mission vise une assurance raisonnable, obtenue grâce à la revue documentaire, aux entretiens et aux observations non intrusives. La faisabilité est considérée comme acceptable si plusieurs conditions sont remplies. Les documents et informations doivent être suffisants et accessibles, même s'ils sont fictifs dans le cadre pédagogique. Les interlocuteurs doivent être disponibles, notamment la direction, le référent SI et les métiers. La fenêtre de 4 semaines doit être compatible avec la profondeur attendue. Enfin, les données sensibles doivent être anonymisées dans les livrables si nécessaire.

## Objectifs détaillés

Les objectifs de cette mission sont multiples et complémentaires. Il s'agit d'abord d'évaluer le niveau de sécurité du système d'information, en examinant la gouvernance, les pratiques et les contrôles en place. Nous vérifierons également l'application des bonnes pratiques et des exigences réglementaires pertinentes, notamment le RGPD. Un autre objectif important est d'identifier et d'évaluer les risques majeurs affectant la confidentialité, l'intégrité et la disponibilité des données et services. Enfin, nous proposerons un plan d'actions priorisé, réaliste et proportionné aux moyens de la clinique.

## Périmètre et limites

### Périmètre inclus

Le périmètre de l'audit couvre plusieurs domaines essentiels. Les processus examinés incluent l'accueil et l'administratif, la consultation, la gestion des dossiers, la facturation, la sauvegarde et restauration, la gestion des accès et la gestion des incidents. Les systèmes concernés sont les postes utilisateurs, les comptes, le réseau interne, l'accès Internet, l'application patient, le stockage partagé et les sauvegardes. L'organisation sera également examinée, notamment les rôles et responsabilités SSI, la sensibilisation, les procédures et le suivi des prestataires.

### Limites exclues

Certains éléments sont explicitement exclus du périmètre. Les tests d'intrusion et l'exploitation de vulnérabilités ne seront pas réalisés. L'audit physique détaillé des locaux est également exclu. Enfin, l'analyse exhaustive d'un hébergeur ou prestataire externe sera limitée aux éléments contractuels et à la gouvernance.

### Gestion des changements de périmètre

Toute évolution du périmètre doit être justifiée, par exemple en cas de changement d'architecture, d'indisponibilité ou de force majeure. Elle doit également être validée par l'audité et tracée dans le journal de bord, puis reflétée dans les livrables.

## Critères d'audit

### Référentiels principaux

Les travaux s'appuieront principalement sur l'ISO/IEC 27001, qui couvre les clauses 4 à 10 incluant le contexte, le leadership, la planification, le support, les opérations, l'évaluation et l'amélioration. L'ISO/IEC 27002 fournira une sélection de contrôles pertinents pour une petite structure, notamment le contrôle d'accès avec la gestion des identités, l'authentification, les comptes partagés et les droits, la gestion des actifs et inventaires, la sécurité des postes et correctifs avec le patch management, la sauvegarde et restauration, la sensibilisation et formation, la gestion des incidents et journaux, et la gestion fournisseurs avec les contrats et la sous-traitance.

### Référentiels complémentaires

Les guides ANSSI sur l'hygiène informatique, les mots de passe, les sauvegardes et les rançongiciels seront également utilisés. Le RGPD sera appliqué sur les articles 5, 24, 25, 28, 30, 32, 33 et 34, selon la disponibilité des éléments. Enfin, les politiques et procédures internes de la clinique, ainsi que les contrats et exigences métiers, seront pris en compte.

## Première analyse de risques

Plusieurs risques ont été pressentis lors de la phase de cadrage. Le risque d'accès non maîtrisés pourrait résulter de comptes partagés, de mots de passe faibles ou de droits excessifs, entraînant une fuite ou altération de dossiers et une non-conformité. Le risque de perte de données pourrait survenir en cas de sauvegardes absentes ou non testées, provoquant une perte d'historique médical et un arrêt d'activité. Le phishing et la compromission pourraient résulter d'un vol d'identifiants ou de malware, entraînant un rançongiciel ou une fuite de données. Les postes non à jour pourraient être exploités via des correctifs manquants ou un antivirus obsolète. Enfin, l'indisponibilité du système d'information pourrait survenir en cas de panne ou d'attaque sans plan de continuité, entraînant une interruption des soins.

## Organisation, rôles et responsabilités

L'équipe d'audit est structurée autour de plusieurs rôles complémentaires. Ouali Nesrine, chef d'équipe, coordonne l'ensemble de la mission. Les auditeurs sont répartis selon leurs compétences : l'analyste risques se concentre sur la cartographie et la cotation des risques, l'expert technique réalise les observations non intrusives, le responsable de la collecte des preuves gère le journal de bord et le registre de preuves, et l'analyste conformité examine les écarts par rapport aux référentiels ISO et RGPD et formule les recommandations.

Côté audité, le point de contact sera la Direction ou le Référent SI, qui sera en charge de mettre à disposition les documents, les accès en lecture aux éléments nécessaires et les interlocuteurs requis.

## Approche méthodologique

L'approche méthodologique suivra plusieurs phases. Le cadrage permettra de comprendre le contexte, de définir le périmètre, les critères et le planning, et d'identifier les risques d'audit. Le terrain inclura la revue documentaire, les entretiens, les observations techniques non intrusives et la collecte de preuves. L'analyse portera sur les constats, l'évaluation des impacts et probabilités, la cartographie des risques et les recommandations. Enfin, le rapport et la restitution permettront de synthétiser les résultats, de prioriser les actions et de présenter le plan d'actions lors d'une discussion décisionnelle.

## Planning prévisionnel

Le planning s'étale sur 4 semaines. La première semaine sera consacrée au cadrage, incluant l'examen des documents, la définition du périmètre, la sélection des référentiels, la planification et la préparation des entretiens. Les semaines 2 et 3 seront dédiées au terrain, avec les entretiens, la revue documentaire, les observations, la collecte de preuves et les mises à jour du programme. La fin de la semaine 3 sera consacrée à l'analyse des risques et des constats, avec une validation interne et des compléments si nécessaire. Enfin, la semaine 4 sera dédiée au rapport et à la restitution, avec une présentation orale de 15 à 20 minutes.

## Hypothèses, risques de mission et mesures de mitigation

Plusieurs risques de mission ont été identifiés et des mesures de mitigation ont été prévues. Si l'accès aux documents est limité, cela pourrait entraîner des constatations incomplètes. Pour mitiger ce risque, nous demanderons les documents dès le début, prévoirons des alternatives et tracerons les limites. Si la disponibilité des interlocuteurs est faible, cela pourrait retarder le planning. Nous planifierons donc les créneaux dès le premier jour, prévoirons des créneaux courts et effectuerons des relances. La sensibilité des données pourrait restreindre les preuves collectées. Nous anonymiserons donc les données, masquerons les captures et utiliserons des preuves indirectes. Enfin, si le périmètre évolue, cela pourrait entraîner une dérive. Une procédure de changement formalisée a donc été mise en place.

Cette note complète la lettre de mission et servira de base au programme d'audit.

Cordialement,  
Équipe Audit SSI — Efrei Paris
