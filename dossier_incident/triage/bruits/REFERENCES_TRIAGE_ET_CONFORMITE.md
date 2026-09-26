# Références communes — qualification des bruits

Un bruit est un événement observable mais sans connexion établie avec l'incident MIRAGE et sans hypothèse d'attaque suffisamment crédible pour justifier une investigation approfondie. Il est enregistré pour conserver la vision d'ensemble, puis traité avec une priorité proportionnée.

## Méthode de triage

1. Identifier le signal, sa source et son horodatage.
2. Rechercher un contexte normal : ticket, maintenance, signature, appareil connu, activité planifiée ou source externe générique.
3. Vérifier l'absence de corrélation avec les hôtes, comptes, indicateurs et fenêtre temporelle de MIRAGE.
4. Conserver la justification de classement et le signal d'origine.
5. Réouvrir le signal si un élément nouveau crée une corrélation technique vérifiable.

## Cadre de conformité

- Le [NIST CSF 2.0](https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=957258) soutient l'analyse, la priorisation et la documentation de la réponse à incident.
- Le [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final) rappelle l'importance de l'amélioration continue à partir des analyses réalisées.
- La [loi marocaine n° 09-08](https://www.cndp.ma/images/lois/Loi-09-08-Fr.pdf) impose de limiter l'accès aux journaux contenant des données personnelles, notamment pour les connexions d'utilisateurs et les tickets de support.

## Formule commune pour le jury

> « Nous avons enregistré ce signal afin de ne rien ignorer, puis nous l'avons classé comme bruit parce que son contexte normal et l'absence de corrélation ne justifient pas de le rattacher à MIRAGE. »

Le classement « bruit » n'efface jamais l'événement. Il permet à la cellule de concentrer ses efforts sur les éléments qui portent un risque démontré.
