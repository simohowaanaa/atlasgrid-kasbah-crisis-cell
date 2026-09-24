<div align="center">

# AtlasGrid — Cellule de crise MIRAGE

**Dossier d'incident • Exercice KASBAH • AtlasGrid, entreprise fictive**

[Accéder à la chronologie](CHRONOLOGIE_PREUVES.md) · [Voir les preuves](preuves_retenues/) · [Préparer la cartographie](cartographie_SI/BRIEF_CARTOGRAPHIE_JURY.md)

</div>

> **Cadre pédagogique.** Ce dépôt reconstitue la gestion d'un incident cyber fictif. Il ne contient aucune donnée réelle.

## En un regard

| Incident | Impact confirmé | Données | État du dossier |
|---|---|---|---|
| Rançongiciel **MIRAGE** | **23 / 40** serveurs chiffrés | **117,8 Go** exfiltrés | **12** preuves · **8** fausses pistes · **7** bruits |

**Services touchés :** paie, facturation, ERP et partages de fichiers.<br>
**Exposition :** SIROCCO a publié un échantillon de données clients et contractuelles. La revendication de 300 Go n'est pas confirmée.

## Démarrer ici

1. **Comprendre l'incident** — lire le [mémoire de crise](MEMOIRE_INCIDENT_MIRAGE.md).
2. **Suivre la chaîne d'attaque** — consulter la [chronologie des preuves](CHRONOLOGIE_PREUVES.md).
3. **Préparer les rendus** — utiliser le [brief de cartographie](cartographie_SI/BRIEF_CARTOGRAPHIE_JURY.md), les fiches et les décisions ci-dessous.

## Chaîne d'attaque confirmée

| Moment | Événement établi | Pièces principales |
|---|---|---|
| J-21 à J-1 | Utilisation anormale du compte VPN `svc_oasisnet` | A-02, A-10 |
| J-11 | Création de la règle sortante `OUT-TEMP-443` | A-09 |
| J-10 à J-1 | Exfiltration de 117,8 Go vers une infrastructure externe | A-03 |
| J-3 | Sabotage de la rétention des sauvegardes | A-05 |
| J-1 · 03:12 | Détection et chiffrement MIRAGE sur FIN-112 | A-01, A-04, A-12 |
| J2 | Publication d'un échantillon sur SIROCCO | A-07 |

> La chronologie complète distingue les faits confirmés, les hypothèses, les fausses pistes et le bruit : [ouvrir la fiche complète](chronologie_complete/FICHE_CHRONOLOGIE_COMPLETE.md).

## Explorer le dossier

| Besoin | Où aller | Ce que vous y trouverez |
|---|---|---|
| Établir les faits | [preuves_retenues/](preuves_retenues/) | 12 fiches de preuve, leurs captures et leur argumentation. |
| Comprendre ce qui a été écarté | [fausses_pistes/](fausses_pistes/) · [bruits/](bruits/) | Les signaux étudiés, leur vérification et leur verdict. |
| Justifier les arbitrages | [decisions/](decisions/) | 8 décisions de crise, leurs captures et leur base de conformité. |
| Retracer tout l'exercice | [chronologie_complete/](chronologie_complete/) | Fiche détaillée et galerie des captures. |
| Construire la cartographie | [cartographie_SI/](cartographie_SI/) | Inventaire, consignes et dépendances du SI. |
| Travailler par responsabilité | [poles_cellule/](poles_cellule/) | Les six pôles, leurs notes et leurs éléments utiles. |
| Retrouver une capture | [assets/captures/](assets/captures/) | Source unique des captures, classées par nature. |

## Les 6 pôles de la cellule

| Pôle | Responsabilité | Livrable attendu |
|---|---|---|
| SOC / Détection | Qualifier les signaux et tenir la main courante | Chronologie de l'incident |
| Forensic | Reconstituer le mode opératoire à partir des traces | Hypothèses d'attaque argumentées |
| Risque / Conformité | Évaluer les risques et obligations | Tableau de risques |
| Continuité d'activité | Préserver les services critiques et organiser la reprise | Plan de containment |
| Communication | Gérer les messages internes, clients et presse | Communiqué et réponses |
| Direction | Arbitrer, prioriser et porter la restitution | Rapport d'incident et plan 30 / 60 / 90 jours |

## Livrables du jury

- **Cartographie simplifiée du SI** : zones, dépendances, actifs critiques et éléments affectés.
- **Chronologie d'incident** : date, heure, pièce A-xx, qualification et décision associée.
- **Communiqué de crise** : une page, uniquement à partir de faits confirmés.
- **Plan 30 / 60 / 90 jours** : action, responsable, échéance, risque couvert et indicateur.
- **Présentation finale** : 10 à 15 minutes, portée par les six pôles sous la forme d'un rapport d'incident.

## Règle essentielle

Chaque affirmation doit renvoyer à une pièce. Une **preuve**, une **hypothèse**, une **fausse piste** et un **bruit** sont quatre statuts différents : ils ne doivent jamais être confondus.

---

<div align="center">

**AtlasGrid · MIRAGE · Exercice KASBAH**

</div>
