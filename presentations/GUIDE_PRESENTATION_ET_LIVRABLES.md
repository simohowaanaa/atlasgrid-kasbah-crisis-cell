# Guide — présentation finale et livrables

Ce dossier est réservé à la présentation que vous préparerez. Quand elle sera prête, ajoutez-y le fichier PowerPoint ou PDF final : il remplacera les anciens supports HTML.

## Ce que la présentation doit raconter

Durée cible : **10 à 15 minutes**. Présentez l'incident comme un rapport clair, fondé sur les pièces du dossier. Ne mélangez jamais un fait prouvé, une hypothèse, une fausse piste et un bruit.

### Trame conseillée (8 à 10 diapositives)

1. **Contexte et alerte initiale** : AtlasGrid, l'incident MIRAGE, le périmètre de crise.
2. **Impact métier confirmé** : 23 serveurs touchés sur 40 ; paie, facturation, ERP et fichiers affectés.
3. **Chronologie de l'attaque** : accès VPN `svc_oasisnet`, règle pare-feu, exfiltration de 117,8 Go, sabotage des sauvegardes, chiffrement de FIN-112, publication SIROCCO.
4. **Les preuves déterminantes** : sélectionner les pièces les plus convaincantes parmi les 12 preuves, avec leurs références A-xx.
5. **Ce qui a été écarté** : expliquer au moins une fausse piste et un bruit pour démontrer la méthode de qualification.
6. **Décisions de crise** : isolement sous tension, containment par segments, maintien surveillé de l'OT, communication et notification.
7. **Risques et conformité** : données concernées, assurance, obligation de notification et conservation des preuves.
8. **Continuité d'activité** : actifs prioritaires, mesures de reprise et dépendances critiques.
9. **Plan 30 / 60 / 90 jours** : actions, responsables, échéances et indicateurs.
10. **Conclusion** : situation connue, limites restantes et prochaine décision attendue de la Direction.

## Répartition entre les six pôles

- **SOC / Détection** : qualification des alertes et chronologie.
- **Forensic** : mode opératoire reconstitué et limites des conclusions.
- **Risque / Conformité** : risques, assurance et obligations.
- **Continuité d'activité** : containment, services critiques et reprise.
- **Communication** : salariés, clients, presse et messages validés.
- **Direction** : arbitrages, priorités et plan 30 / 60 / 90 jours.

## Livrables à remettre

1. **Cartographie simplifiée du SI** : zones, dépendances, actifs critiques et éléments impactés.
2. **Chronologie de l'incident** : date, heure, pièce A-xx, qualification et décision associée.
3. **Communiqué de crise** : une page, fondée exclusivement sur des faits confirmés.
4. **Plan de remédiation 30 / 60 / 90 jours** : action, responsable, échéance, risque couvert et indicateur.
5. **Présentation finale** : le support de l'oral, avec les références vers les preuves et décisions.

## Documents à utiliser

- `../CHRONOLOGIE_PREUVES.md` pour la chaîne d'attaque.
- `../MEMOIRE_INCIDENT_MIRAGE.md` pour la synthèse de crise.
- `../chronologie_complete/FICHE_CHRONOLOGIE_COMPLETE.md` pour l'ensemble des événements.
- `../preuves_retenues/`, `../fausses_pistes/`, `../bruits/` et `../decisions/` pour les fiches et les captures.
- `../cartographie_SI/BRIEF_CARTOGRAPHIE_JURY.md` pour la cartographie.
