<div align="center">

<p>
  <img src="assets/logos/organisateurs.png" alt="EMSI et CyberSup, organisateurs de l'exercice" width="640">
</p>

# AtlasGrid — dossier de gestion de crise MIRAGE

**Dossier d'incident fictif · Exercice KASBAH · AtlasGrid**

*Exercice organisé par EMSI et CyberSup.*

[Guide du jury](GUIDE_DU_JURY.md) · [Comprendre l'incident](dossier_incident/chronologie/MEMOIRE_INCIDENT_MIRAGE.md) · [Livrables PDF](livrables_jury/README.md)

</div>

> **Cadre pédagogique.** Ce dépôt reconstitue un incident cyber fictif. Il ne contient aucune donnée réelle et doit être lu comme un dossier de formation.

## Commencer ici

Ce dépôt est volontairement organisé pour un lecteur non technique.

1. Lire le [guide du jury](GUIDE_DU_JURY.md) : il explique les mots employés et le parcours recommandé.
2. Lire le [mémoire d'incident](dossier_incident/chronologie/MEMOIRE_INCIDENT_MIRAGE.md) : la version courte de ce qui s'est passé.
3. Suivre la [chronologie consolidée](dossier_incident/chronologie/FICHE_CHRONOLOGIE_COMPLETE.md) : chaque étape renvoie à une pièce.
4. Consulter les [livrables prêts à partager](livrables_jury/README.md) : chronologie, containment, risques, rapport de direction et plan de remédiation.

## En une minute

| Sujet | Ce qui est établi |
|---|---|
| Incident | Le rançongiciel **MIRAGE** a touché l'environnement AtlasGrid. |
| Impact | **23 des 40 serveurs** sont chiffrés, dont l'ERP, la paie, la facturation et les partages de fichiers. |
| Données | **117,8 Go** de transferts sortants sont confirmés ; l'affirmation de 300 Go de SIROCCO n'est pas confirmée. |
| Accès anormal | Le compte prestataire partagé `svc_oasisnet` a été utilisé la nuit, hors de son profil habituel. |
| Reprise | La cellule refuse de payer, restaure depuis l'air-gap de Settat, remet l'ERP en premier puis rouvre les services clients par paliers. |

> **Point de prudence.** Le rapport OasisNet étaye une compromission amont possible, mais son périmètre exact reste à confirmer. SIROCCO a publié un échantillon de données, sans qu'une identité ou une localisation du groupe puisse être démontrée par le dossier.

## La chaîne d'incident, en langage simple

1. Un accès prestataire (`svc_oasisnet`) est utilisé de façon anormale.
2. Une règle réseau temporaire ouvre une sortie non contrôlée.
3. Des données sont transférées vers une infrastructure externe.
4. Les mécanismes de sauvegarde en ligne sont dégradés avant le chiffrement.
5. MIRAGE se lance sur FIN-112, chiffre des systèmes et détruit des possibilités de restauration locale.
6. La cellule isole, communique, refuse la rançon, puis redémarre depuis une copie hors ligne vérifiée.

La version complète, sourcée et nuancée est disponible dans la [chronologie consolidée](dossier_incident/chronologie/FICHE_CHRONOLOGIE_COMPLETE.md).

## Où trouver l'information

| Si vous cherchez… | Ouvrez… | Vous y trouverez… |
|---|---|---|
| Le récit court de l'incident | [Chronologie](dossier_incident/chronologie/) | Mémoire, chronologie technique, chronologie complète et galerie de captures. |
| Les faits établis | [Preuves](dossier_incident/preuves/) | 15 fiches de preuve, les captures associées et les limites de chaque constat. |
| Les éléments écartés | [Triage](dossier_incident/triage/) | Fausses pistes et bruits, avec la raison de leur classement. |
| Les choix de la cellule | [Décisions](dossier_incident/decisions/) | 12 décisions documentées : confinement, communication, assurance, reprise et retour des clients. |
| Les dépendances du SI | [Cartographie](dossier_incident/cartographie/) | Zones, actifs critiques et dépendances utiles à la reprise. |
| Les rôles de la cellule | [Pôles](dossier_incident/poles/) | Notes de travail des six pôles. |
| Les documents de restitution | [Livrables jury](livrables_jury/) | PDF classés par usage pour la présentation et la direction. |

## Décisions finales de reprise

| Décision | Justification | Référence |
|---|---|---|
| Ne pas payer | Aucun déchiffrement ni effacement des données n'est garanti ; une copie indépendante existe. | [Décision 09](dossier_incident/decisions/09_ne_pas_payer_reprise_independante.md) |
| Restaurer depuis Settat | Les sauvegardes en ligne récentes sont suspectes ou infectées ; l'air-gap est déconnecté. | [Décision 12](dossier_incident/decisions/12_restauration_airgap_Settat.md) |
| Prioriser l'ERP | La paie et la facturation dépendent du socle ERP. | [Décision 11](dossier_incident/decisions/11_priorite_restauration_ERP.md) |
| Rouvrir par paliers | Chaque étape est validée avant d'étendre la remise en service. | [Décision 13](dossier_incident/decisions/13_reprise_progressive_clients.md) |

## Règle de lecture du dossier

Chaque affirmation renvoie à une pièce. Les statuts ne se confondent pas : une **preuve** établit un fait, une **fausse piste** a été investiguée puis réfutée, et un **bruit** est un signal réel mais sans lien démontré avec MIRAGE.

---

<div align="center">

**AtlasGrid · MIRAGE · Exercice KASBAH**

</div>
