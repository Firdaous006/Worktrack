CAHIER DES CHARGES

Application de suivi des heures de
travail pour étudiants étrangers

Projet BTS SIO - Option SISR (2ᵉ année)

Version 1

Année académique 2026 - 2027

Ce document est une base de travail destinée à évoluer.
Les seuils légaux mentionnés (ex. 964 heures/an) sont donnés à titre d'exemple
documenté pour la France et doivent être vérifiés à chaque itération auprès des
sources officielles.



1. Présentation du projet

1.1 Contexte

La France accueille chaque année
un nombre important d'étudiants étrangers dans son enseignement supérieur (329
146 étudiants en mobilité internationale en 2024, soit 11,7 % des effectifs).
Sous certaines conditions, ces étudiants peuvent exercer une activité salariée
en parallèle de leurs études, dans la limite de 964 heures par an en France.
Des dispositifs comparables existent dans d'autres pays (ex. limite
hebdomadaire au Canada).

Le suivi de cette limite est
aujourd'hui réalisé de façon dispersée : plannings papier, bulletins de
salaire, tableurs personnels non structurés, ou absence totale de suivi. Cette
dispersion rend difficile, pour l'étudiant, de savoir à tout moment où il en
est par rapport à son plafond et à l'échéance de son titre de séjour.

1.2 Problématique

Comment permettre à un étudiant
étranger de suivre simplement, de façon centralisée et fiable, son volume
d'heures travaillées par rapport à un seuil réglementaire ou personnel, sans
lui imposer une charge de suivi plus lourde que ce qu'il fait déjà ?

1.3 Objectifs du projet

•  Offrir un outil gratuit, simple et rapide de suivi des
heures travaillées.

•  Réduire la charge de saisie par rapport à une solution
artisanale (tableur).

•  Alerter l'utilisateur avant qu'il n'atteigne son seuil,
plutôt que de le laisser le découvrir trop tard.

•  Garantir la sécurité et la confidentialité de données
personnelles sensibles (statut administratif, revenus, employeurs).

• Démontrer, dans le cadre du BTS SIO SISR, une maîtrise
de l'infrastructure, du déploiement, de la sécurité et de l'administration d'un
service web.

1.4 Public cible

•  Étudiants étrangers en France soumis à la limite de 964
heures annuelles.

•  À terme, étudiants étrangers d'autres pays imposant des
limites similaires, via un seuil personnalisable.

•  Public secondaire : associations étudiantes, services
des relations internationales, avocats en droit des étrangers pouvant relayer
ou intégrer l'outil.

1.5 Limites assumées du projet

L'application ne produit aucune preuve juridiquement
opposable. Les heures saisies restent des déclarations de l'utilisateur.
L'objectif est le confort et l'anticipation personnelle, pas la certification
légale du temps de travail. Cette limite doit être visible en permanence dans
l'interface (mention claire, non dissimulée dans les CGU).

2. Périmètre fonctionnel

Le projet est volontairement
séquencé pour garantir un socle fiable avant d'ajouter des fonctionnalités plus
ambitieuses. Chaque fonctionnalité écartée est documentée avec sa justification
plutôt que simplement omise.



Version



Fonctionnalité



Description



Statut



V1



Compteur d'heures



Saisie manuelle rapide (date,
  durée, employeur optionnel), calcul du cumul en temps réel.



Cœur du projet



V1



Alertes de seuil



Notifications à 80 %, 90 %, 100
  % du seuil applicable, basées sur une date de référence personnalisée (ex.
  validité du titre de séjour).



Cœur du projet



V1



Historique et projections



Vue chronologique des heures
  saisies, rythme moyen, projection de la date d'atteinte du seuil.



Cœur du projet



V1



Démarrer / Terminer



Bouton simple d'horodatage de
  début et fin de service, sans dépendance matérielle.



Cœur du projet



V1



Seuil configurable



L'utilisateur choisit son propre
  seuil et sa période de référence plutôt qu'une base légale figée par pays.



Cœur du projet



V1.5



Import de planning par photo



Upload d'une ou plusieurs photos
  de planning ; extraction automatique des créneaux via une API de vision, avec
  écran de confirmation avant tout enregistrement.



Validation utilisateur
  obligatoire



V2



Tags NFC personnels



Tags NFC achetés et configurés
  par l'utilisateur lui-même (pas de badge employeur) pour un horodatage en un
  geste. Limité aux terminaux compatibles Web NFC (Android).



Optionnel, sous réserve de
  prototypage



V2



Multi-pays



Extension des seuils
  pré-documentés et sourcés (2-3 pays au lancement), sinon seuil personnalisé.



Sous réserve de veille juridique
  tenable



V2



Intégration pages avocats



Widget intégrable sur des pages
  de conseil juridique pour étudiants étrangers.



Dépend de partenariats



Écarté



Lecture de badge employeur



Écarté : le badge appartient à
  l'employeur, lecture non autorisée et techniquement fermée (formats
  propriétaires chiffrés).



Non retenu - justifié

Le tag NFC (V2) est un objet acheté et configuré par
l'utilisateur lui-même — il ne s'agit à aucun moment d'un badge d'accès
employeur, ce qui aurait posé un problème d'autorisation et de format
propriétaire.

3. Sécurité et protection des données - cœur du projet

Compte tenu de la nature des
données traitées (statut administratif, revenus, identité, parfois photos de
documents de planning), la sécurité n'est pas un chapitre parmi d'autres : elle
conditionne la légitimité même du projet. Un incident de sécurité sur ce type
de données aurait un impact direct sur des personnes utilisant cette solution.

3.1 Principes directeurs

•  Minimisation : ne collecter que les données strictement
nécessaires au suivi des heures.

•  Chiffrement systématique : au repos et en transit, sans
exception.

•  Transparence : l'utilisateur sait à tout moment quelles
données sont stockées et pourquoi.

•  Réversibilité : export et suppression complète des
données à la demande de l'utilisateur.

3.2 Authentification et gestion des accès

•  Authentification forte recommandée (mot de passe
robuste + option MFA).

•  Hachage des mots de passe avec algorithme adapté
(Argon2 ou bcrypt), jamais de stockage en clair dans la base de donnée.

•  Séparation stricte des rôles (utilisateur standard /
administration technique) avec droits minimaux.

• Journalisation des tentatives de connexion et détection
d'anomalies (connexions inhabituelles).

3.3 Chiffrement des données

•  Chiffrement en transit : TLS obligatoire sur l'ensemble
des échanges (HTTPS, certificat renouvelé automatiquement).

•  Chiffrement au repos : base de données et fichiers
uploadés (photos de planning, justificatifs) chiffrés sur le stockage.

•  Isolation des photos de planning : suppression
automatique après extraction et validation, pour limiter la durée de
conservation d'une donnée sensible non indispensable une fois traitée.

3.4 Hébergement et conformité RGPD

•  Hébergement en France ou dans l'Union européenne
exclusivement, affiché clairement à l'utilisateur.

•  Registre des traitements et base légale identifiée pour
chaque donnée collectée.

•  Politique de confidentialité rédigée en langage clair,
disponible en français et en anglais dès la V1.

•  Procédure documentée de réponse aux demandes d'exercice
des droits (accès, rectification, effacement).

3.5 Traçabilité et niveaux de fiabilité des données

Pour ne pas laisser croire à une
fiabilité qu'elles n'ont pas, les heures enregistrées sont classées par niveau:

•  Heures déclarées manuellement par l'utilisateur.

•  Heures issues d'un import de planning, validées par
l'utilisateur avant enregistrement.

•  Heures associées à un justificatif (bulletin de
salaire, capture d'écran datée).

•  Historique complet des modifications : chaque
changement d'une heure déjà enregistrée est conservé avec horodatage, jamais
écrasé silencieusement.

3.6 Sauvegarde et plan de reprise

•  Sauvegardes automatiques régulières, chiffrées, avec
test de restauration documenté (une sauvegarde non testée n'est pas une
sauvegarde fiable).

•  Procédure de reprise d'activité formalisée en cas
d'incident (perte de service, corruption de données).

3.7 Journalisation et supervision

•  Journalisation des accès et actions sensibles
(connexion, modification d'heures, export de données), sans conserver de
données personnelles superflues dans les journaux.

•  Supervision de l'infrastructure (disponibilité, charge,
tentatives d'intrusion) avec alertes à l'administrateur.

3.8 Gestion des risques liés aux données sensibles

•  Analyse d'impact relative à la protection des données
(AIPD) à envisager compte tenu du public cible vulnérable.

•  Plan de réponse à incident : notification à la CNIL et
aux utilisateurs concernés en cas de violation de données, dans les délais
réglementaires.

•  Aucune donnée revendue, partagée à des tiers
commerciaux ou utilisée à des fins autres que le service rendu à l'utilisateur.

4. Architecture technique (volet SISR)

4.1 Vue d'ensemble

Architecture web classique à
trois niveaux : interface utilisateur, logique métier (API), base de données —
hébergée sur une infrastructure maîtrisée de bout en bout pour démontrer les
compétences SISR (et non sur une plateforme low-code).

4.2 Infrastructure envisagée

•  Serveur(s) applicatif(s) sous environnement virtualisé
ou conteneurisé (Docker).

•  Reverse proxy avec terminaison TLS (ex. Nginx + Let's
Encrypt).

•  Base de données relationnelle avec sauvegardes
planifiées.

•  Environnements distincts développement / recette /
production.

4.3 Déploiement

•  Déploiement scripté et documenté (reproductibilité en
cas de migration ou de reconstruction).

5. Planning prévisionnel (6 à 9 mois)



Phase



Durée indicative



Livrables



Cadrage



Mois 1



Cahier des charges finalisé,
  choix techniques, maquettes d'interface, modélisation des données.



Socle applicatif



Mois 2-4



Authentification, compteur,
  historique, alertes, infrastructure de base (serveur, base de données,
  reverse proxy, TLS).



Sécurisation &
  fiabilisation



Mois 4-5



Chiffrement, gestion des accès,
  journalisation, sauvegarde/restauration testée, traçabilité des
  modifications.



Import photo (V1.5)



Mois 5-6



Intégration API de vision, écran
  de validation utilisateur, tests sur plannings réels variés.



Tests & recette



Mois 6-7



Tests utilisateurs (cercle
  restreint, ex. étudiants ), corrections, durcissement sécurité.



Diffusion initiale



Mois 7-8



Mise en avant premiers contacts
  associations/relations internationales.

Bilan & perspectives V2


Mois 8-9


Bilan d'usage, priorisation V2
  (tags NFC, intégration avocats).

6. Stratégie de diffusion et d'adoption

6.1 Canaux envisagés

•  Associations étudiantes internationales et services des
relations internationales.

•  Contenu éditorial ciblé (article expliquant le calcul
des 964 heures) associé à l'outil.

•  Intégration à des pages de conseil juridique pour
étudiants étrangers (partenariat avocats).

•  Communautés en ligne d'étudiants étrangers (réseaux
sociaux, forums par ville universitaire).

6.2 Positionnement

L'outil est gratuit, non commercial, et ne remplace aucun
dispositif administratif officiel. Ce positionnement est un argument de
confiance à mettre en avant auprès des relais institutionnels et associatifs,
plus enclins à recommander un service sans intérêt commercial caché.

7. Risques et limites du projet

•  Risque d'adoption : sans relais de diffusion actif,
l'usage restera limité à un cercle restreint - l'incubateur et les partenariats
sont donc déterminants, pas seulement les fonctionnalités.

•  Risque juridique : toute confusion entre suivi
personnel et preuve officielle doit être évitée par une communication claire et
continue.

•  Risque de maintenance : les seuils légaux évoluent ;
une veille doit être organisée ou le champ doit rester volontairement limité à
quelques pays documentés.
