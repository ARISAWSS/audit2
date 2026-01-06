# Fiches Constats — Audit SSI Clinique Santé Plus

Date : 24 décembre 2025  
Équipe Audit SSI — Efrei Paris

---

## Constat C-001 : Absence de MFA obligatoire pour tous les comptes Microsoft 365

### Critères de référence

Ce constat s'appuie sur plusieurs référentiels. L'ISO/IEC 27002:2022, contrôle 5.17 sur l'authentification, recommande l'utilisation de mécanismes d'authentification forte. L'ANSSI, dans ses recommandations sur l'hygiène informatique, insiste également sur l'importance de l'authentification forte. Le RGPD, à l'article 32 sur la sécurité du traitement, impose des mesures techniques et organisationnelles appropriées pour garantir un niveau de sécurité adapté au risque.

### Observation

Lors de la revue des comptes Microsoft 365, nous avons examiné les preuves P-002 et P-003 qui nous ont permis de constater plusieurs éléments préoccupants. Seulement 40% des comptes utilisateurs, soit 6 comptes sur 15, ont activé l'authentification multifacteur (MFA). Si les comptes administrateurs, au nombre de 3, ont tous la MFA activée, ce qui est une bonne pratique, aucune politique de Conditional Access n'impose la MFA de manière obligatoire pour l'ensemble des comptes. La politique de sécurité actuelle repose donc sur une activation volontaire par les utilisateurs, ce qui laisse une grande partie des comptes vulnérables.

### Preuves

Plusieurs preuves étayent ce constat. La preuve P-002, datée du 8 décembre 2025, est un export du statut MFA des comptes utilisateurs qui montre clairement que seulement 6 utilisateurs sur 15 ont activé la MFA. La preuve P-003, également du 8 décembre 2025, contient des captures des politiques de sécurité et d'authentification M365 qui confirment l'absence de politique Conditional Access obligatoire. La preuve P-004, du 8 décembre 2025, liste les comptes à privilèges et montre que les administrateurs ont bien la MFA activée. Enfin, la preuve P-005, du 9 décembre 2025, est un rapport de connexions anonymisé qui permet de voir les connexions sans MFA.

### Risque identifié

Le risque principal identifié est la compromission de comptes utilisateurs par phishing ou vol de mots de passe. L'impact de ce risque est élevé car il pourrait entraîner un accès non autorisé aux données de santé, une violation du RGPD et une interruption d'activité. La probabilité est moyenne, compte tenu des menaces ciblées sur le secteur santé et de la faible sensibilisation observée. La criticité est donc élevée, résultant de la combinaison d'un impact élevé et d'une probabilité moyenne.

Pour illustrer ce risque, imaginons un scénario concret. Un attaquant obtient les identifiants d'un utilisateur via un email de phishing. Sans MFA, l'accès au compte est immédiat, permettant l'exfiltration de données patients ou l'accès à MedSimple. Les conséquences pourraient être graves, avec une fuite de données de santé et des sanctions réglementaires.

### Recommandation

Nous recommandons d'implémenter une politique de Conditional Access Microsoft 365 imposant la MFA obligatoire pour 100% des comptes, utilisateurs et administrateurs, avec une activation progressive sur 2 semaines. Cette recommandation est identifiée comme P-1.

Pour mettre en œuvre cette recommandation, plusieurs actions sont nécessaires. Il faut d'abord créer une politique Conditional Access "MFA obligatoire" dans le portail Microsoft 365. Ensuite, il est important de communiquer aux utilisateurs, par email et lors d'une session de 30 minutes, sur l'activation de la MFA, en recommandant l'utilisation de l'application Microsoft Authenticator. L'activation doit se faire progressivement par groupe, en commençant par la direction, puis les médecins, le secrétariat et enfin l'accueil. Il faudra également monitorer les échecs d'authentification et accompagner les utilisateurs en difficulté. Enfin, la politique devra être documentée dans la procédure "Gestion des accès".

Cette action est sous la responsabilité du Prestataire IT, avec validation de la Direction. L'échéance recommandée est le 31 janvier 2026. Le coût estimé est de 0€ car cette fonctionnalité est incluse dans Microsoft 365. La priorité est P1, critique.

---

## Constat C-002 : Stratégie de sauvegarde incomplète et absence de test de restauration récent

### Critères de référence

Ce constat s'appuie sur l'ISO/IEC 27002:2022, contrôle 8.13 sur la sauvegarde de l'information, qui recommande la mise en place de sauvegardes régulières et testées. L'ANSSI recommande également une stratégie de sauvegarde suivant le principe 3-2-1, c'est-à-dire 3 copies des données, sur 2 supports différents, dont 1 hors site. Le RGPD, à l'article 32 sur la sécurité du traitement, impose également des mesures appropriées pour garantir la sécurité des données.

### Observation

Lors de la revue de la stratégie de sauvegarde, nous avons examiné les preuves P-022, P-023, P-024 et P-025 qui nous ont permis de constater plusieurs éléments. Les sauvegardes quotidiennes des documents SharePoint et OneDrive sont bien en place et automatisées via Microsoft 365, ce qui est positif. Les sauvegardes hebdomadaires des 2 postes critiques, l'accueil et la direction, vers le NAS local sont documentées. Une copie hors site existe également sur un cloud prestataire, mais le chiffrement n'a pas pu être vérifié dans le contrat fourni. Le point le plus préoccupant est que le dernier test de restauration remonte à 8 mois, en avril 2025, comme le montre la preuve P-025. Par ailleurs, il n'existe pas de sauvegarde dédiée de la base MedSimple, qui repose uniquement sur les sauvegardes de l'éditeur ou de l'hébergeur. Enfin, les objectifs RTO et RPO ne sont pas documentés formellement.

### Preuves

Plusieurs preuves étayent ce constat. La preuve P-022, datée du 5 décembre 2025, contient le plan de sauvegarde détaillant la fréquence, le périmètre et la rétention. La preuve P-023, du 15 décembre 2025, contient les logs des jobs de sauvegarde sur 30 jours qui montrent que les sauvegardes fonctionnent correctement. La preuve P-024, également du 15 décembre 2025, est une preuve de la copie hors site chiffrée sous forme de contrat ou rapport. La preuve P-025, du 18 décembre 2025, est le PV du test de restauration qui montre que le dernier test remonte à avril 2025. Enfin, la preuve P-026, également du 18 décembre 2025, est la preuve d'un élément restauré de manière anonymisée.

### Risque identifié

Le risque principal identifié est la perte définitive de données critiques en cas d'incident, qu'il s'agisse d'un rançongiciel, d'une panne matérielle ou d'une erreur humaine. L'impact de ce risque est très élevé car il pourrait entraîner une perte des dossiers patients, une interruption des soins, une non-conformité au RGPD et à l'HDS, et un arrêt d'activité. La probabilité est moyenne, compte tenu du fait que le secteur santé est ciblé et que la dépendance au système d'information est forte. La criticité est donc très élevée.

Pour illustrer ce risque, imaginons un scénario concret. Un rançongiciel chiffre les postes et le NAS local. La restauration depuis la copie hors site n'a pas été testée récemment et échoue, peut-être à cause d'une incompatibilité ou d'une corruption. Les données sont alors perdues définitivement, avec des conséquences dramatiques pour la clinique et ses patients.

### Recommandation

Nous recommandons de compléter la stratégie de sauvegarde selon le principe 3-2-1 et de formaliser les tests de restauration trimestriels. Cette recommandation est identifiée comme P-2.

Pour mettre en œuvre cette recommandation, plusieurs actions sont nécessaires. Il faut d'abord documenter les objectifs RTO et RPO, en fixant par exemple un RTO de 24 heures et un RPO de 24 heures, ce qui semble réaliste pour la clinique. Il faut ensuite vérifier le chiffrement de la copie hors site en demandant une attestation au prestataire. Il serait également souhaitable d'ajouter une sauvegarde export de MedSimple, avec un export hebdomadaire automatisé vers un stockage sécurisé, si cette fonctionnalité est disponible. Les tests de restauration doivent être planifiés trimestriellement, avec un PV et une preuve de fichier restauré à chaque fois. Enfin, il faut créer une procédure de restauration documentée avec les étapes, les contacts et l'escalade.

Cette action est sous la responsabilité du Prestataire IT, avec validation de la Direction. L'échéance recommandée est le 28 février 2026. Le coût estimé est de 500€ par an si l'export MedSimple est payant. La priorité est P1, critique.

---

## Constat C-003 : Retard dans l'application des correctifs de sécurité sur les postes de travail

### Critères de référence

Ce constat s'appuie sur l'ISO/IEC 27002:2022, contrôle 8.8 sur la gestion des vulnérabilités techniques, qui recommande l'application rapide des correctifs de sécurité. L'ANSSI, dans ses recommandations sur l'hygiène informatique, insiste également sur l'importance des mises à jour. Le RGPD, à l'article 32 sur la sécurité du traitement, impose également des mesures appropriées.

### Observation

Lors de l'observation de 3 postes échantillons, l'accueil, un médecin et la direction, nous avons examiné les preuves P-012, P-013, P-014 et P-015 qui nous ont permis de constater des retards dans l'application des correctifs. Sur le poste accueil, la dernière mise à jour Windows date du 15 novembre 2025, soit un retard de 15 jours par rapport aux correctifs critiques de novembre. Sur le poste médecin, la dernière mise à jour date du 8 novembre 2025, soit un retard de 22 jours. Sur le poste direction, la dernière mise à jour date du 20 novembre 2025, soit un retard de 10 jours. Aucune politique formelle de gestion des correctifs n'existe, avec des délais cibles, des exceptions et des tests. Le prestataire IT effectue des mises à jour "à la demande" mais il n'y a pas de cycle automatisé.

### Preuves

Plusieurs preuves étayent ce constat. La preuve P-012, datée du 12 décembre 2025, contient des captures de Windows Update du poste accueil qui montrent clairement le retard. La preuve P-013, également du 12 décembre 2025, est un reporting de patch du prestataire IT ou un ticket si disponible. La preuve P-014, du 13 décembre 2025, montre la couverture antivirus/EDR avec l'inventaire des postes. Enfin, la preuve P-015, également du 13 décembre 2025, contient les alertes des 90 derniers jours et leur statut de traitement, de manière anonymisée.

### Risque identifié

Le risque principal identifié est l'exploitation de vulnérabilités connues non corrigées. L'impact de ce risque est élevé car il pourrait entraîner une compromission du poste, une propagation de malware et une exfiltration de données. La probabilité est moyenne, compte tenu du fait que les vulnérabilités sont publiques et que les attaquants automatisés exploitent rapidement les failles connues. La criticité est donc élevée.

Pour illustrer ce risque, imaginons un scénario concret. Une vulnérabilité critique Windows, par exemple référencée CVE-2025-xxxx, est exploitée par un rançongiciel. Les postes non mis à jour sont compromis en premier, permettant la propagation sur le réseau et l'infection de l'ensemble du système d'information.

### Recommandation

Nous recommandons de mettre en place une politique de gestion des correctifs avec application automatique dans un délai de 7 jours pour les correctifs critiques. Cette recommandation est identifiée comme P-3.

Pour mettre en œuvre cette recommandation, plusieurs actions sont nécessaires. Il faut d'abord définir une politique de correctifs avec des délais différenciés : 7 jours pour les correctifs critiques, 30 jours pour les correctifs importants, et trimestriellement pour les correctifs optionnels. Il faut ensuite configurer Windows Update for Business, ou un équivalent via le prestataire, pour un déploiement automatisé. Il faut également créer une procédure d'exception pour les cas où un logiciel métier serait incompatible, avec des tests préalables sur un poste pilote. Il faudra monitorer la conformité avec un rapport mensuel de l'état des mises à jour, fourni par le prestataire à la direction. Enfin, cette politique devra être documentée dans une procédure SSI intitulée "Gestion des correctifs".

Cette action est sous la responsabilité du Prestataire IT, avec validation de la Direction. L'échéance recommandée est le 15 février 2026. Le coût estimé est de 0€ car cette fonctionnalité est incluse dans Windows. La priorité est P1, critique.

---

## Constat C-004 : Isolation insuffisante du réseau Wi‑Fi invité

### Critères de référence

Ce constat s'appuie sur l'ISO/IEC 27002:2022, contrôles 8.20 sur la séparation dans les réseaux et 8.21 sur la sécurisation des services réseau, qui recommandent une séparation claire entre les réseaux. L'ANSSI recommande également une séparation et une isolation des réseaux.

### Observation

Lors de la revue de la configuration réseau, nous avons examiné les preuves P-018, P-019, P-020 et P-021 qui nous ont permis de constater plusieurs éléments. Le Wi‑Fi invité, nommé "SANTEPLUS-INVITES", utilise bien WPA2, ce qui est conforme, mais le WPS est activé, ce qui représente un risque. L'isolation invité est partiellement en place car le réseau invité est sur un VLAN séparé, mais les règles de pare-feu permettent un accès partiel au réseau interne, avec les ports 80, 443 et 53 ouverts vers l'interne. Il n'y a pas de limitation de bande passante pour le réseau invité et pas de portail captif avec authentification ou acceptation de conditions générales d'utilisation.

### Preuves

Plusieurs preuves étayent ce constat. La preuve P-018, datée du 14 décembre 2025, contient la configuration Wi‑Fi montrant WPA2/3, WPS et les SSID. La preuve P-019, également du 14 décembre 2025, contient les règles d'isolation du réseau invité avec les VLAN et ACL. La preuve P-020, du 14 décembre 2025, est un export des règles de pare-feu et NAT, anonymisé. Enfin, la preuve P-021, également du 14 décembre 2025, est une liste des services exposés sur Internet avec leur justification.

### Risque identifié

Le risque principal identifié est un accès non autorisé au réseau interne depuis le Wi‑Fi invité. L'impact de ce risque est moyen car l'accès serait limité mais pourrait permettre d'accéder à certaines ressources internes et d'exfiltrer des données. La probabilité est faible à moyenne, car elle dépend de la motivation d'un attaquant physique. La criticité est donc moyenne.

Pour illustrer ce risque, imaginons un scénario concret. Un attaquant se connecte au Wi‑Fi invité et exploite les règles de pare-feu permissives pour accéder à des ressources internes comme des partages, des imprimantes ou des postes non sécurisés.

### Recommandation

Nous recommandons de renforcer l'isolation du réseau Wi‑Fi invité et de désactiver le WPS. Cette recommandation est identifiée comme P-4.

Pour mettre en œuvre cette recommandation, plusieurs actions sont nécessaires. Il faut d'abord désactiver le WPS sur le routeur ou le point d'accès. Il faut ensuite modifier les règles de pare-feu pour bloquer tout trafic du VLAN invité vers le réseau interne, sauf l'accès Internet sortant. Il serait également souhaitable de limiter la bande passante invité, par exemple à 5 Mbps par client. En option, il serait possible de mettre en place un portail captif avec acceptation de conditions générales d'utilisation, si cette fonctionnalité est disponible. Enfin, cette configuration devra être documentée dans une procédure intitulée "Gestion réseau invité".

Cette action est sous la responsabilité du Prestataire IT. L'échéance recommandée est le 31 janvier 2026. Le coût estimé est de 0€ car il s'agit uniquement de configuration. La priorité est P2, importante.

---

## Constat C-005 : Procédure de gestion des incidents incomplète et exercice table-top révélant des lacunes

### Critères de référence

Ce constat s'appuie sur l'ISO/IEC 27002:2022, contrôles 5.24 sur la gestion des événements de sécurité et 5.25 sur la gestion des incidents de sécurité, qui recommandent une procédure claire et testée. Le RGPD, aux articles 33 sur la notification d'une violation à l'autorité de contrôle et 34 sur la communication d'une violation à la personne concernée, impose également des délais stricts.

### Observation

Lors de la revue de la procédure d'incidents et de l'exercice table-top rançongiciel, nous avons examiné les preuves P-027 et P-028 qui nous ont permis de constater plusieurs lacunes. La procédure d'incident existe mais manque de détails sur plusieurs points importants. Les rôles et responsabilités ne sont pas clairement définis, notamment qui fait quoi et comment se fait l'escalade. Les délais de notification RGPD ne sont pas mentionnés explicitement, notamment le délai de 72 heures pour la CNIL et la communication aux personnes concernées. La procédure de communication externe, notamment avec les patients et les autorités, n'est pas détaillée.

L'exercice table-top réalisé le 19 décembre 2025 a révélé plusieurs problèmes. Il y avait une confusion sur le délai CNIL, certains pensant qu'il était de 7 jours au lieu de 72 heures. Il n'existe pas de kit de crise avec les contacts urgents et les modèles de communication. La décision de communication aux patients n'est pas préparée, notamment qui décide, quel message et quand le communiquer. Enfin, il n'existe pas de procédure de restauration documentée avec les étapes et les contacts du prestataire.

### Preuves

Plusieurs preuves étayent ce constat. La preuve P-027, datée du 16 décembre 2025, contient la procédure de gestion des incidents et l'arbre d'appel. La preuve P-028, du 19 décembre 2025, est le PV de l'exercice table-top rançongiciel avec les actions identifiées.

### Risque identifié

Le risque principal identifié est une réaction inadaptée en cas d'incident majeur, qu'il s'agisse d'un rançongiciel ou d'une fuite de données. L'impact de ce risque est très élevé car il pourrait entraîner une violation du RGPD, des sanctions de la CNIL, une perte de confiance des patients et une interruption d'activité. La probabilité est moyenne, compte tenu du fait que le secteur santé est ciblé. La criticité est donc très élevée.

Pour illustrer ce risque, imaginons un scénario concret. Un rançongiciel chiffre les systèmes. L'équipe ne sait pas qui contacter en urgence, ne respecte pas le délai CNIL de 72 heures, et communique mal aux patients, aggravant ainsi la crise et les conséquences réglementaires.

### Recommandation

Nous recommandons de compléter la procédure de gestion des incidents et de créer un kit de crise opérationnel. Cette recommandation est identifiée comme P-5.

Pour mettre en œuvre cette recommandation, plusieurs actions sont nécessaires. Il faut d'abord enrichir la procédure d'incidents avec un RACI détaillé, c'est-à-dire définir qui est responsable, qui est consulté et qui est informé pour chaque action. Il faut également définir des délais stricts, notamment 72 heures pour la CNIL et la communication aux patients si le risque est élevé. Il faut créer un arbre de décision pour savoir quand notifier et qui valide. Il faut ensuite créer un kit de crise avec une liste de contacts urgents, notamment la CNIL, le prestataire IT, l'avocat et l'assurance cyber. Il faut également préparer des modèles de communication pour la CNIL, les patients et éventuellement la presse. Il faut créer une checklist d'actions avec l'isolation, l'analyse, la restauration et la communication. Il faut planifier des exercices trimestriels avec des scénarios variés comme un rançongiciel, une fuite de données ou un déni de service. Enfin, il faut former le personnel clé, notamment la direction et l'IT, sur la procédure lors d'une session de 2 heures.

Cette action est sous la responsabilité de la Direction, avec le support du DPO s'il existe, sinon du prestataire. L'échéance recommandée est le 15 février 2026. Le coût estimé est de 0€ car il s'agit de rédaction interne. La priorité est P1, critique.

---

## Constat C-006 : Clauses RGPD incomplètes dans les contrats avec les prestataires

### Critères de référence

Ce constat s'appuie sur le RGPD, article 28 sur le responsable du traitement et le sous-traitant, qui impose des clauses spécifiques dans les contrats. L'ISO/IEC 27002:2022, contrôle 5.19 sur la gestion des relations avec les fournisseurs, recommande également une contractualisation claire.

### Observation

Lors de la revue des contrats et DPA, nous avons examiné les preuves P-029 et P-030 qui nous ont permis de constater plusieurs manques. Le contrat avec le prestataire IT contient bien un DPA, Data Processing Agreement, mais il manque plusieurs clauses importantes. La clause sur la notification d'incidents n'est pas explicite, notamment le délai et le contenu de la notification. La clause sur les sous-traitants ultérieurs ne mentionne pas l'autorisation préalable. La clause sur l'audit sécurité ne mentionne pas la possibilité d'audit ou de rapport tiers.

Le contrat avec l'hébergeur MedSimple contient une attestation HDS fournie, ce qui est conforme, mais le DPA est générique et non spécifique à la clinique. Enfin, il n'existe pas de registre des sous-traitants listant qui traite quelles données et pour quels besoins.

### Preuves

Plusieurs preuves étayent ce constat. La preuve P-029, datée du 6 décembre 2025, contient les contrats prestataires et les DPA selon l'article 28 du RGPD. La preuve P-030, également du 6 décembre 2025, contient l'attestation HDS ou sa justification.

### Risque identifié

Le risque principal identifié est une non-conformité au RGPD et une responsabilité en cas d'incident chez le prestataire. L'impact de ce risque est élevé car il pourrait entraîner des sanctions de la CNIL, une responsabilité civile et une perte de confiance. La probabilité est faible à moyenne, car elle dépend de la survenance d'un incident chez le prestataire. La criticité est donc moyenne.

Pour illustrer ce risque, imaginons un scénario concret. Le prestataire IT subit une fuite de données. Le DPA incomplet ne permet pas de déterminer clairement les responsabilités, et la clinique est tenue responsable par défaut, avec des conséquences réglementaires et financières.

### Recommandation

Nous recommandons de compléter les DPA avec les clauses manquantes et de créer un registre des sous-traitants. Cette recommandation est identifiée comme P-6.

Pour mettre en œuvre cette recommandation, plusieurs actions sont nécessaires. Il faut d'abord compléter le DPA du prestataire IT avec une clause de notification d'incidents précisant un délai de 24 heures et le contenu de la notification, notamment la nature, les données concernées et les mesures prises. Il faut également ajouter une clause sur les sous-traitants ultérieurs précisant qu'une autorisation préalable écrite est nécessaire. Il faut ajouter une clause sur l'audit précisant la possibilité d'un audit annuel ou d'un rapport tiers, par exemple une certification ISO 27001. Il faut ensuite demander un DPA spécifique à l'hébergeur MedSimple si possible, sinon valider le DPA générique. Il faut créer un registre des sous-traitants sous forme de tableau listant le nom, les données traitées, la finalité, la base légale et les garanties. Enfin, il faut réviser annuellement les contrats et DPA, notamment lors de l'ajout de nouveaux prestataires.

Cette action est sous la responsabilité de la Direction, avec le support juridique si disponible. L'échéance recommandée est le 28 février 2026. Le coût estimé est de 0€ à 500€ si une consultation juridique est nécessaire. La priorité est P2, importante.

---

## Constat C-007 : Absence de politique de verrouillage automatique des sessions

### Critères de référence

Ce constat s'appuie sur l'ISO/IEC 27002:2022, contrôle 5.16 sur la gestion des privilèges d'accès, qui recommande un verrouillage des sessions. L'ANSSI, dans ses recommandations sur l'hygiène informatique, insiste également sur l'importance du verrouillage de session.

### Observation

Lors de l'observation des postes, nous avons examiné la preuve P-017 qui nous a permis de constater des incohérences dans la configuration du verrouillage. Sur le poste direction, le verrouillage automatique est configuré à 10 minutes, ce qui est acceptable mais non optimal. Sur les postes accueil et secrétariat, le verrouillage est configuré à 30 minutes ou absent, ce qui n'est pas sécurisé. Il n'existe pas de politique centralisée, via GPO ou équivalent, imposant un délai uniforme. Enfin, il n'y a pas de sensibilisation sur l'importance du verrouillage manuel avec la combinaison de touches Win+L.

### Preuves

La preuve P-017, datée du 12 décembre 2025, contient les paramètres de verrouillage de session et de timeout observés sur les différents postes.

### Risque identifié

Le risque principal identifié est un accès non autorisé aux postes laissés sans surveillance. L'impact de ce risque est moyen car il pourrait permettre un accès aux données locales, aux applications ouvertes et une exfiltration. La probabilité est faible car elle nécessite une présence physique, mais le contexte clinique avec des visiteurs et des patients augmente ce risque. La criticité est donc moyenne.

Pour illustrer ce risque, imaginons un scénario concret. Un poste accueil reste déverrouillé pendant une pause. Un visiteur accède aux applications ouvertes comme MedSimple ou la messagerie et consulte ou modifie des données patients.

### Recommandation

Nous recommandons d'implémenter une politique de verrouillage automatique des sessions avec un délai maximum de 5 minutes et de sensibiliser le personnel. Cette recommandation est identifiée comme P-7.

Pour mettre en œuvre cette recommandation, plusieurs actions sont nécessaires. Il faut d'abord configurer le verrouillage automatique à 5 minutes maximum, via GPO ou paramètres locaux selon l'infrastructure. Il faut ensuite sensibiliser le personnel, notamment lors de la formation MFA, sur l'importance du verrouillage avec un rappel sur l'utilisation de Win+L. Il faut monitorer la conformité avec une vérification trimestrielle sur un échantillon de postes. Enfin, cette politique devra être documentée dans une procédure intitulée "Sécurisation des postes".

Cette action est sous la responsabilité du Prestataire IT, avec communication à la Direction. L'échéance recommandée est le 31 janvier 2026. Le coût estimé est de 0€ car il s'agit uniquement de configuration. La priorité est P2, importante.

---

## Synthèse des constats

Au total, 7 constats ont été identifiés lors de cet audit. Quatre constats sont critiques (P1) et nécessitent une attention prioritaire avant le 28 février 2026. Il s'agit de l'absence de MFA obligatoire (C-001), de la stratégie de sauvegarde incomplète (C-002), du retard dans l'application des correctifs (C-003) et de la procédure d'incidents incomplète (C-005). Trois constats sont importants (P2) et peuvent être traités en parallèle. Il s'agit de l'isolation Wi‑Fi invité insuffisante (C-004), des clauses RGPD incomplètes (C-006) et de l'absence de politique de verrouillage session (C-007).

Équipe Audit SSI — Efrei Paris  
Date de finalisation : 24 décembre 2025
