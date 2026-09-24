# AtlasGrid — cellule de crise MIRAGE

> Exercice pédagogique fictif KASBAH. Aucune donnée réelle n'est présente dans ce dépôt.

Ce dépôt rassemble les travaux de la cellule de crise AtlasGrid : preuves, fausses pistes, décisions, cartographie du système d'information, chronologie et préparation des livrables de jury.

## Point de situation

- **Incident :** ransomware MIRAGE.
- **Impact confirmé :** 23 serveurs chiffrés sur 40, incluant la paie, la facturation, l'ERP et les partages de fichiers.
- **Exfiltration objectivée :** 117,8 Go vers une infrastructure externe.
- **Données :** SIROCCO publie un échantillon de données clients et contractuelles ; le volume de 300 Go revendiqué n'est pas confirmé.
- **Éléments qualifiés :** 12 preuves, 8 fausses pistes et 7 bruits.

## Commencer ici

| Objectif | Document de référence |
|---|---|
| Construire la cartographie du SI | [Brief de cartographie](cartographie_SI/BRIEF_CARTOGRAPHIE_JURY.md) |
| Comprendre les systèmes et dépendances | [Référence cartographie](cartographie_SI/REFERENCE_CARTOGRAPHIE_SI.md) |
| Reconstituer l'attaque | [Chronologie des preuves](CHRONOLOGIE_PREUVES.md) |
| Consulter la synthèse de crise | [Mémoire de crise MIRAGE](MEMOIRE_INCIDENT_MIRAGE.md) |
| Préparer les quatre rendus | [Guide des rendus](presentations/02_rendus_ecrits/README.md) |
| Préparer l'oral final | [Guide de présentation](presentations/01_presentation_finale/README.md) |

## Organisation du dépôt

| Dossier | Contenu |
|---|---|
| [`preuves_retenues/`](preuves_retenues/) | Les 12 captures qualifiées comme preuves, leurs fiches d'argumentation et le protocole de conservation. |
| [`fausses_pistes/`](fausses_pistes/) | Les 8 pistes examinées puis écartées, leurs fiches de qualification et leur méthode d'analyse. |
| [`bruits/`](bruits/) | Les 7 signaux sans lien établi avec MIRAGE, leurs fiches de triage et leur méthode de qualification. |
| [`decisions/`](decisions/) | Les 8 captures de décision, leurs fiches d'argumentation et les références de conformité. |
| [`cartographie_SI/`](cartographie_SI/) | Le dossier de prise de poste, l'inventaire et le brief de production de la cartographie. |
| [`poles_cellule/`](poles_cellule/) | Les six pôles, leurs captures, notes de décision et informations complètes du fil. |
| [`presentations/`](presentations/) | Les supports HTML, leurs consignes et le plan de travail. |
| [`capture/`](capture/) | L'archive complète des captures, renommées et numérotées. |

## Les six pôles

- **SOC / Détection** : qualification des signaux et chronologie de l'incident.
- **Forensic** : hypothèses d'attaque et analyse des traces.
- **Risque / Conformité** : risques, obligations de notification et assurance.
- **Continuité d'activité** : actifs critiques, containment et reprise.
- **Communication** : salariés, clients et presse.
- **Direction** : arbitrages, rapport d'incident et plan 30/60/90 jours.

Chaque pôle possède un fichier `NOTE_POLE.md` et une transcription source dans `INFORMATIONS_DU_FIL_COMPLET.txt`.

## Livrables à finaliser

1. Cartographie du SI : une page, zones, dépendances, actifs vitaux et éléments touchés.
2. Communiqué de crise : une page, faits prouvés uniquement.
3. Chronologie d'incident : tableau avec date, heure, pièce, verdict et décision.
4. Plan de remédiation 30/60/90 jours : action, responsable, échéance, risque couvert et indicateur.
5. Présentation finale : 10 à 15 minutes, six porte-parole, format recommandé « rapport d'incident ».

## Règle de travail

Chaque affirmation doit renvoyer à une pièce. Les faits confirmés, les hypothèses, les fausses pistes et les bruits ne doivent jamais être confondus.
