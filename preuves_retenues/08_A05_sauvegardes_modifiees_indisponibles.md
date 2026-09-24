# Preuve A-05 — Sabotage et indisponibilité des sauvegardes

![Capture A-05](../assets/captures/preuves/08_A05_sauvegardes_modifiees_indisponibles.png)

## Fait objectivé

Le jour J-3 à 01:12, `svc_oasisnet` modifie la rétention des sauvegardes. Les travaux quotidiens de J-3, J-2 et J-1 sont ensuite exclus. À J1 03:15, FIN-112 exécute `vssadmin delete shadows /all`, puis à 15:28 les dépôts BKP-01 et BKP-02 deviennent injoignables.

## Pourquoi cette pièce est une preuve

Les journaux de Veeam et les événements d'exécution décrivent une succession horodatée : modification de politique, exclusions de travaux, suppression des clichés et indisponibilité des dépôts. La disponibilité de la capacité de restauration est donc directement compromise.

## Portée et limite

A-05 prouve la dégradation des sauvegardes en ligne, pas la destruction de toute copie hors ligne. La vérification de la copie air-gap au site secondaire reste nécessaire avant toute décision de reconstruction.

## Réponse courte au jury

> « La sauvegarde n'était pas seulement indisponible : sa rétention avait été modifiée avant le chiffrement. Nous avons donc traité la restauration comme un sujet d'investigation et non comme une hypothèse rassurante. »

## Conservation et conformité

Mettre les consoles et dépôts sous contrôle d'accès renforcé, exporter les journaux Veeam, préserver les configurations et ne lancer aucune restauration sur l'original sans validation. Cette mesure protège la disponibilité et l'intégrité des preuves et du plan de reprise. Référence : [REFERENCES_CONSERVATION_ET_CONFORMITE.md](REFERENCES_CONSERVATION_ET_CONFORMITE.md).
