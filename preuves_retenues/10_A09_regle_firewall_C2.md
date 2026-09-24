# Preuve A-09 — Règle pare-feu et canal de commande

![Capture A-09](../assets/captures/preuves/10_A09_regle_firewall_C2.png)

## Fait objectivé

Le jour J-11 à 02:03, `svc_oasisnet` crée la règle `OUT-TEMP-443`, autorisant FIN-112 à joindre HTTPS avec journalisation désactivée. Le jour J-1, FIN-112 contacte ensuite `45.137.184.62:443` avec une régularité d'environ 60 secondes ; 2 118 sessions et la même empreinte JA3 sont relevées.

## Pourquoi cette pièce est une preuve

La configuration du pare-feu et les journaux de flux sont deux sources techniques indépendantes. Ensemble, elles démontrent l'ouverture d'un chemin de sortie non justifié et son utilisation régulière par l'hôte compromis, ce qui est cohérent avec un canal de commande.

## Portée et limite

Le mot « C2 » est une qualification technique fondée sur le comportement ; il ne démontre pas, seul, l'identité de l'attaquant ni le contenu chiffré échangé. Cette pièce est renforcée par A-01, A-03 et A-12.

## Réponse courte au jury

> « Nous avons un changement de configuration anormal, puis l'utilisation répétée exacte du flux créé. La conclusion ne repose pas sur une réputation d'IP, mais sur le lien chronologique entre la règle et le comportement de FIN-112. »

## Conservation et conformité

Conserver l'export de configuration avant et après changement, les journaux de flux, l'identité du compte ayant modifié la règle et les heures associées. Bloquer le flux après collecte, en documentant la mesure de confinement. Référence : [REFERENCES_CONSERVATION_ET_CONFORMITE.md](REFERENCES_CONSERVATION_ET_CONFORMITE.md).
