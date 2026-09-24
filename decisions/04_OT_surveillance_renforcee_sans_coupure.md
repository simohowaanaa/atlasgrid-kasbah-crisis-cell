# Décision 04 — Renforcer la surveillance OT sans coupure immédiate

![Capture de la décision 04](../assets/captures/decisions/04_OT_surveillance_renforcee_sans_coupure.png)

## Décision retenue

Maintenir le réseau industriel OT/SCADA isolé et opérationnel, augmenter immédiatement sa surveillance et préparer des critères explicites de coupure. Aucune coupure préventive de l'OT n'est ordonnée tant qu'aucun indicateur de compromission OT n'est établi.

## Faits établis au moment du choix

- L'inventaire **A-13** indique que l'environnement SCADA est sur un réseau isolé et ne le classe pas parmi les hôtes chiffrés observés.
- Les traces de propagation de **A-12** concernent les partages SMB des environnements bureautiques et serveurs identifiés, pas une session OT confirmée.
- L'activité de reconnaissance nouvelle vers l'OT a été bloquée ; elle justifie une vigilance accrue, sans démontrer une compromission de la conduite industrielle.

## Pourquoi ce choix est défendable

Une coupure OT peut entraîner un impact physique, industriel et de sécurité. La décision distingue donc une **tentative ou un risque** d'une compromission avérée. Le réseau déjà isolé réduit l'exposition ; une surveillance renforcée, des journaux centralisés et des critères de bascule permettent de maîtriser le risque sans créer un incident opérationnel par excès de prudence.

Ne rien faire aurait ignoré un signal préoccupant. Couper immédiatement l'OT aurait été disproportionné au regard des faits établis et aurait pu créer un risque plus important que celui que la mesure cherchait à éviter.

## Réponse courte au jury

> « En environnement industriel, la coupure est une décision de sûreté autant que de cybersécurité. Nous avons augmenté la surveillance tout de suite, conservé l'isolement existant et défini les conditions factuelles qui déclencheraient une coupure. »

## Cadre de conformité et suites

- La priorisation selon les impacts de disponibilité, d'intégrité et de confidentialité est conforme à la logique de sécurité des SI sensibles portée par la DGSSI.
- Le NIST CSF 2.0 recommande des mesures d'atténuation pilotées par l'analyse de l'incident et par le risque ; ici, la surveillance est renforcée et traçable.
- Formaliser des seuils de coupure : exécution inconnue sur HMI, session non autorisée, modification de configuration, trafic sortant anormal ou alerte d'intégrité. Référence commune : [REFERENCES_NORMES_ET_CADRE.md](REFERENCES_NORMES_ET_CADRE.md).
