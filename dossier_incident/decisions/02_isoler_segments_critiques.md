# Décision 02 — Isoler les segments critiques

![Capture de la décision 02](../../assets/captures/decisions/02_isoler_segments_critiques.png)

## Décision retenue

Mettre en quarantaine les segments et partages non indispensables touchés par la propagation, tout en maintenant uniquement les flux indispensables aux activités critiques, sous contrôle renforcé.

## Faits établis au moment du choix

- La preuve **A-13** fait état de **23 serveurs sur 40 chiffrés**, dont des actifs de fichiers, de messagerie et de services métiers.
- La preuve **A-12** atteste une propagation latérale depuis FIN-112 via des partages SMB.
- La preuve **A-05** établit l'indisponibilité de sauvegardes en ligne et interdit de compter sur une restauration immédiate pour absorber une propagation supplémentaire.

## Pourquoi ce choix est défendable

L'isolement par segments limite le rayon d'impact sans provoquer une coupure aveugle de toute l'entreprise. Il protège les actifs non encore atteints, réduit les flux latéraux et donne du temps à la cellule pour vérifier les sauvegardes et les dépendances métier. Cette solution équilibre la disponibilité des services vitaux avec l'urgence de casser la chaîne de propagation.

Une coupure générale aurait pu immobiliser inutilement des fonctions critiques ; ne rien segmenter aurait laissé l'attaquant réutiliser les chemins SMB déjà démontrés. Le périmètre doit être revu régulièrement selon les journaux et les résultats d'investigation.

## Réponse courte au jury

> « Nous n'avons pas choisi entre sécurité et continuité : nous avons limité les flux qui portaient le risque prouvé, tout en préservant les services nécessaires. Chaque exception de flux était justifiée, temporaire et surveillée. »

## Cadre de conformité et suites

- Le NIST CSF 2.0 prévoit des actions d'atténuation proportionnées aux incidents ; la segmentation documentée est une mesure de confinement réversible et vérifiable.
- L'analyse des impacts sur confidentialité, intégrité et disponibilité soutient la priorisation des systèmes critiques prévue par le cadre DGSSI relatif aux systèmes sensibles.
- Produire une matrice « segment / flux autorisé / propriétaire / date de révision » et faire valider les exceptions par la continuité d'activité et la direction. Référence commune : [REFERENCES_NORMES_ET_CADRE.md](REFERENCES_NORMES_ET_CADRE.md).
