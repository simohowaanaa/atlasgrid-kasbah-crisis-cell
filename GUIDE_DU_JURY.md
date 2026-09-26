# Guide de lecture du dossier MIRAGE

## Objet du dossier

Ce dossier explique comment la cellule de crise d'AtlasGrid a compris, contenu et traité l'incident fictif **MIRAGE**. Il est conçu pour pouvoir être lu sans connaissances préalables en cybersécurité.

## Parcours recommandé

| Étape | Durée indicative | Document | Pourquoi le lire |
|---|---:|---|---|
| 1. Vue d'ensemble | 3 min | [Mémoire d'incident](dossier_incident/chronologie/MEMOIRE_INCIDENT_MIRAGE.md) | Comprendre les faits essentiels, les limites connues et les décisions finales. |
| 2. Déroulé précis | 10 min | [Chronologie consolidée](dossier_incident/chronologie/FICHE_CHRONOLOGIE_COMPLETE.md) | Suivre la chaîne d'incident, avec une pièce à l'appui de chaque étape. |
| 3. Vérification | selon besoin | [Preuves](dossier_incident/preuves/) | Ouvrir la fiche et la capture d'origine correspondant à un fait. |
| 4. Analyse critique | selon besoin | [Triage](dossier_incident/triage/) | Voir ce qui a été écarté et pourquoi la cellule ne s'est pas dispersée. |
| 5. Arbitrages | 10 min | [Décisions](dossier_incident/decisions/) | Évaluer les choix de crise et de reprise. |
| 6. Restitution | 10 min | [Livrables du jury](livrables_jury/README.md) | Accéder aux documents PDF par thème. |

## Mots utiles

| Terme | Définition simple |
|---|---|
| **Rançongiciel** | Logiciel malveillant qui chiffre des fichiers et demande souvent une rançon. |
| **Exfiltration** | Transfert non autorisé de données vers l'extérieur. |
| **Compte de service** | Compte technique utilisé par une application ou un prestataire, plutôt que par une personne. |
| **Air-gap** | Copie conservée hors réseau : elle ne peut pas être atteinte directement par l'attaquant. |
| **ERP** | Système central qui relie les fonctions métier, par exemple la paie, la facturation et les données de gestion. |
| **EDR / SIEM** | Outils qui enregistrent et signalent l'activité des postes et des comptes. |

## Ce que le dossier affirme — et ce qu'il n'affirme pas

| Établi | Non établi ou à confirmer |
|---|---|
| L'utilisation nocturne anormale de `svc_oasisnet`, la règle sortante, les 117,8 Go transférés et le chiffrement MIRAGE. | L'étendue exacte de la compromission chez OasisNet. |
| L'indisponibilité ou l'infection des sauvegardes en ligne récentes. | Le contenu exact de toutes les données transférées. |
| L'existence d'un échantillon de données publié par SIROCCO. | Les 300 Go revendiqués, l'identité et la localisation de SIROCCO. |
| La pertinence d'une restauration depuis la copie hors ligne de Settat. | Une garantie de déchiffrement ou d'effacement des données en cas de paiement. |

## Organisation du dépôt

- `dossier_incident/` : l'analyse détaillée et les pièces de travail.
- `livrables_jury/` : les PDF prêts à présenter ou à transmettre.
- `assets/` : les captures source qui appuient les fiches.

La page d'accueil, [README.md](README.md), donne également un chemin rapide vers chaque partie.
