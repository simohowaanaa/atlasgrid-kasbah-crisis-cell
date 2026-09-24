# Preuve A-13 — Inventaire de l'impact sur les serveurs

![Capture A-13](../assets/captures/preuves/12_A13_inventaire_serveurs_impact.png)

## Fait objectivé

Le jour J2 à 10:00, l'inventaire recense **23 serveurs chiffrés sur 40**, dont PAIE-01, FACT-02, FILER-RBT-02, FILER-CASA-01, ERP-APP-01 et ERP-DB-01. MSG-01 et DC-01 sont dégradés ; DC-02, WEB-PUB-01 et SCADA-HMI sont indiqués intacts, l'OT étant isolé du réseau bureautique.

## Pourquoi cette pièce est une preuve

Cette pièce décrit l'état constaté de chaque actif à une heure donnée et permet de mesurer l'impact sur les métiers, les dépendances et la continuité. Elle est vérifiable par les hôtes, les responsables de service et les traces de chiffrement associées.

## Portée et limite

Elle ne démontre pas à elle seule la cause du chiffrement ni l'état futur de chaque service. C'est une photographie d'impact à J2, à rapprocher des alertes EDR, des journaux et des tests de restauration.

## Réponse courte au jury

> « Nous avons priorisé à partir d'un inventaire daté, pas d'une impression générale. Cela explique le confinement ciblé, la protection de l'OT et l'ordre de reprise des services métiers. »

## Conservation et conformité

Archiver la version datée de l'inventaire, l'auteur de chaque statut et les critères de qualification « chiffré », « dégradé » ou « intact ». La priorisation doit intégrer les impacts sur confidentialité, intégrité et disponibilité. Référence : [REFERENCES_CONSERVATION_ET_CONFORMITE.md](REFERENCES_CONSERVATION_ET_CONFORMITE.md).
