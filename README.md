<div align="center">

<p>
  <img src="assets/logos/organisateurs.png" alt="EMSI et CyberSup, organisateurs de l'exercice" width="640">
</p>

# AtlasGrid — Cellule de crise MIRAGE

**Dossier d'incident • Exercice KASBAH • AtlasGrid, entreprise fictive**

*Exercice organisé par EMSI et CyberSup.*

[Chronologie technique](CHRONOLOGIE_PREUVES.md) · [Chronologie complète](chronologie_complete/FICHE_CHRONOLOGIE_COMPLETE.md) · [PDF prêt à partager](output/pdf/Chronologie_Incident_AtlasGrid_MIRAGE.pdf) · [Cartographie SI](cartographie_SI/BRIEF_CARTOGRAPHIE_JURY.md)

</div>

> **Cadre pédagogique.** Ce dépôt reconstitue la gestion d'un incident cyber fictif. Il ne contient aucune donnée réelle.

## En un regard

| Incident | Impact confirmé | Données | État du dossier |
|---|---|---|---|
| Rançongiciel **MIRAGE** | **23 / 40** serveurs chiffrés | **117,8 Go** exfiltrés | Acte III consolidé : **15** preuves · **8** fausses pistes · **10** bruits documentés |

**Services touchés :** paie, facturation, ERP et partages de fichiers.<br>
**Exposition :** SIROCCO a publié un échantillon de données clients et contractuelles. La revendication de 300 Go n'est pas confirmée.<br>
**Reprise décidée :** refus de payer, restauration depuis l'air-gap de Settat, priorité au cœur ERP et remise en service client par paliers.

> **Position de la cellule.** La cause la plus étayée est la compromission du compte partagé `svc_oasisnet`, après une compromission rapportée chez OasisNet. L'étendue exacte côté prestataire reste à confirmer ; l'attribution de SIROCCO n'est pas établie au-delà de la revendication et de l'échantillon publié.

## Parcours du jury

1. **Comprendre en deux minutes** — lire le [mémoire de crise](MEMOIRE_INCIDENT_MIRAGE.md).
2. **Vérifier chaque fait** — suivre la [chronologie des preuves](CHRONOLOGIE_PREUVES.md), puis ouvrir les captures associées.
3. **Évaluer les choix de crise** — consulter les [décisions documentées](decisions/) : confinement, communication, assurance, non-paiement et reprise.
4. **Télécharger le rendu** — utiliser le [PDF de chronologie prêt à partager](output/pdf/Chronologie_Incident_AtlasGrid_MIRAGE.pdf).

## Chaîne d'attaque confirmée

| Moment | Événement établi | Pièces principales |
|---|---|---|
| J-42 | Compromission initiale signalée chez OasisNet après hameçonnage d'un technicien | A-08 |
| J-21 à J-1 | Utilisation anormale du compte VPN `svc_oasisnet` | A-02, A-10 |
| J-11 | Création de la règle sortante `OUT-TEMP-443` | A-09 |
| J-10 à J-1 | Exfiltration de 117,8 Go vers une infrastructure externe | A-03 |
| J-3 | Sabotage de la rétention des sauvegardes | A-05 |
| J-1 · 03:12 | Détection et chiffrement MIRAGE sur FIN-112 | A-01, A-04, A-12 |
| J2 | Publication d'un échantillon sur SIROCCO | A-07 |
| J3 | Sauvegardes en ligne compromises ; reprise depuis Settat décidée | A-06, A-30 |
| J3 | Reprise client progressive, avec contrôles à chaque palier | Décision Direction |

> La chronologie complète distingue les faits confirmés, les hypothèses, les fausses pistes et le bruit : [ouvrir la fiche complète](chronologie_complete/FICHE_CHRONOLOGIE_COMPLETE.md).

## Décisions finales de reprise

| Décision | Pourquoi elle est défendable | Résultat attendu |
|---|---|---|
| Ne pas payer | Aucun déchiffrement ou effacement des données n'est garanti ; une source indépendante existe. | Ne pas financer l'extorsion. |
| Restaurer depuis Settat | Les points en ligne récents sont suspects ou infectés ; l'air-gap est isolé. | Reprise fiable, mais plus lente. |
| Prioriser l'ERP | Paie et facturation dépendent du socle ERP. | Remise en service cohérente des métiers. |
| Rouvrir par paliers | Chaque service est validé avant extension de la reprise. | Stabilité et confiance client maintenues. |

Voir les justifications et les captures dans [les décisions de l'Acte III](decisions/09_ne_pas_payer_reprise_independante.md), [la priorité ERP](decisions/11_priorite_restauration_ERP.md), [le choix de l'air-gap](decisions/12_restauration_airgap_Settat.md) et [la reprise client](decisions/13_reprise_progressive_clients.md).

## Explorer le dossier

| Besoin | Où aller | Ce que vous y trouverez |
|---|---|---|
| Établir les faits | [preuves_retenues/](preuves_retenues/) | 15 fiches de preuve, leurs captures et leur argumentation. |
| Comprendre ce qui a été écarté | [fausses_pistes/](fausses_pistes/) · [bruits/](bruits/) | Les signaux étudiés, leur vérification et leur verdict. |
| Justifier les arbitrages | [decisions/](decisions/) | Les décisions de crise et de reprise, leurs captures et leur base de conformité. |
| Retracer tout l'exercice | [chronologie_complete/](chronologie_complete/) | Fiche détaillée et galerie des captures. |
| Construire la cartographie | [cartographie_SI/](cartographie_SI/) | Inventaire, consignes et dépendances du SI. |
| Travailler par responsabilité | [poles_cellule/](poles_cellule/) | Les six pôles, leurs notes et leurs éléments utiles. |
| Retrouver une capture | [assets/captures/](assets/captures/) | Source unique des captures, classées par nature. |
| Partager le rendu | [output/pdf/](output/pdf/) | PDF de chronologie prêt à déposer ou envoyer. |

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
