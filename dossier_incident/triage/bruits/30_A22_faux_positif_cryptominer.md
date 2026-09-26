# Bruit A-22 — Faux positif « cryptominer »

![Capture A-22](../../../assets/captures/bruits/30_A22_faux_positif_cryptominer.png)

## Signal enregistré

Une alerte évoque un cryptominer, signal qui pourrait détourner des ressources ou indiquer l'exécution d'un logiciel indésirable.

## Contexte et raison du classement

L'exécutable concerné est **7-Zip signé** et l'activité correspond à une compilation nocturne planifiée. Aucun processus de minage, connexion vers un pool, persistance anormale ou indicateur commun avec MIRAGE n'est trouvé.

## Réponse courte au jury

> « Nous avons vérifié l'alerte au niveau du processus, de la signature, de la tâche planifiée et du réseau. Tout correspond à une activité interne prévue : c'est un faux positif, pas un second incident. »

## Suite et conformité

Conserver l'alerte et la validation de la tâche, puis ajuster la règle de détection si cela réduit les faux positifs sans masquer un comportement réellement suspect. Référence : [REFERENCES_TRIAGE_ET_CONFORMITE.md](REFERENCES_TRIAGE_ET_CONFORMITE.md).
