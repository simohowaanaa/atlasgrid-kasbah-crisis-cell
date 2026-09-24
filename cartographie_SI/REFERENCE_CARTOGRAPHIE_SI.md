# Référence — cartographie du SI AtlasGrid

Source : dossier de prise de poste, conservé dans les deux captures de ce dossier. Les données sont fictives et destinées à l'exercice.

## Contexte

- AtlasGrid est un opérateur d'énergie basé à Casablanca : production et distribution, environ 1 200 salariés, siège et plusieurs sites d'exploitation.
- Ses clients sont de grands comptes industriels et des collectivités, avec des engagements contractuels de disponibilité.
- La paie et la facturation sont internes. Une partie du SI et les sauvegardes en ligne sont exploitées par OasisNet.
- La DSI interne est réduite : quelques administrateurs et un référent sécurité. OasisNet dispose d'accès d'administration à distance.
- Les systèmes industriels — supervision et SCADA — sont gérés à part, sur un réseau volontairement isolé du reste du SI.

## Inventaire des systèmes

| Service / actif | Serveur(s) | Technologie | Exploité par |
|---|---|---|---|
| Annuaire — authentification et droits | DC-01, DC-02 | Windows Server 2019, Active Directory | Interne |
| Messagerie | MSG-01 | Microsoft Exchange 2019 | Interne |
| ERP — achats, stocks, comptabilité | ERP-APP-01, ERP-DB-01 | Sage X3, SQL Server | Interne |
| Paie | PAIE-01 | Sage Paie, SQL Server | Interne |
| Facturation | FACT-02 | Application interne, SQL Server | Interne |
| Serveurs de fichiers | FILER-RBT-02, FILER-CASA-01 | Windows Server, partages SMB | Interne |
| Portail client | WEB-CLI-01 | Application web, IIS | Interne, exposé |
| Site web public | Non précisé | CMS WordPress | Hébergeur externe |
| Intranet et téléphonie | INTRA-01, IPBX-01 | SharePoint, IPBX (VoIP) | Interne |
| VPN d'administration | VPN-GW | FortiGate SSL-VPN | Interne + OasisNet |
| Sauvegarde en ligne | VBR-01, BKP-01/02 | Veeam Backup & Replication | OasisNet |
| Copie hors ligne | Site secondaire | Bandes LTO-9, air-gap | Interne |
| Antivirus / EDR | Console centrale | Microsoft Defender for Endpoint | Interne |
| Supervision industrielle | SCADA-HMI-* | SCADA / IHM, réseau isolé | Interne |
| Postes utilisateurs | Par service, ex. FIN-112, RH-031 | Non précisé | Interne |

## Relations et dépendances explicitement connues

- L'annuaire porte l'authentification et les droits : DC-01 et DC-02 sont donc transverses.
- L'ERP dépend de son applicatif ERP-APP-01 et de sa base ERP-DB-01.
- La facturation repose sur FACT-02 ; le portail client WEB-CLI-01 porte l'accès en ligne des grands comptes.
- Les documents métiers sont sur FILER-RBT-02 et FILER-CASA-01.
- OasisNet a un accès distant via le VPN d'administration et exploite les sauvegardes en ligne Veeam.
- La copie hors ligne LTO-9 au site secondaire constitue le recours de dernier ressort.
- SCADA-HMI-* est isolé du réseau bureautique ; cette séparation doit être préservée sur la cartographie.

## À faire apparaître dans la cartographie

1. Distinguer les zones : utilisateurs, services internes, services exposés, administration/OasisNet, sauvegardes et OT/SCADA.
2. Mettre en évidence les actifs critiques : annuaire, paie, facturation, ERP, partages de fichiers, portail client, sauvegardes et VPN d'administration.
3. Relier les dépendances confirmées et signaler comme **à valider** toute relation non indiquée par le dossier.
4. Mettre en valeur les points de vigilance : accès distant prestataire, sauvegardes en ligne, portail exposé et séparation OT.

## Contrats et interlocuteurs

| Interlocuteur | Information utile |
|---|---|
| OasisNet | Exploite une partie du SI et les sauvegardes en ligne ; accès d'administration à distance ; disponibilité contractuelle. |
| Assureur cyber | Police couvrant les incidents ; obligations de déclaration et de préservation des preuves. |
| Clients grands comptes | Engagements de disponibilité au contrat, par exemple 99,5 %. |
| Autorité de régulation | Cadre de notification en cas d'incident majeur. |

## Livrable demandé par le dossier initial

- Une cartographie simplifiée : systèmes regroupés en zones et reliés selon leurs dépendances.
- Une liste des actifs critiques, avec une criticité justifiée.
- Les dépendances les plus préoccupantes, en particulier les services dont dépendent plusieurs autres actifs.
