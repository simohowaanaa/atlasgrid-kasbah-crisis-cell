# Décision 08 — Notifier l'Autorité de façon transparente et évolutive

![Capture de la décision 08](../assets/captures/decisions/08_notification_autorite_transparente.png)

## Décision retenue

Notifier l'Autorité dans le délai prévu par l'exercice avec les faits établis, l'incertitude explicitement signalée, les premières mesures prises, le point de contact et un calendrier de compléments. Ne pas attendre d'avoir une certitude totale sur le périmètre.

## Faits établis au moment du choix

- La preuve **A-03** établit des transferts sortants anormaux totalisant **117,8 Go** depuis FIN-112 puis FILER-RBT vers une infrastructure externe.
- La preuve **A-07** confirme la présence d'échantillons de données clients et contrats sur un site de fuite ; le volume revendiqué par l'attaquant reste une affirmation non confirmée.
- Les preuves **A-01**, **A-05**, **A-12** et **A-13** documentent l'attaque, la propagation, l'impact et les premières mesures de confinement.
- Le scénario impose une notification à l'Autorité dans les **72 heures**.

## Pourquoi ce choix est défendable

L'information disponible est suffisante pour signaler un risque sérieux tout en distinguant précisément les certitudes des hypothèses. Attendre le résultat final de toute l'investigation peut faire perdre du temps et empêcher un accompagnement rapide des personnes ou autorités concernées. Une notification initiale complétée ensuite est plus responsable qu'un dossier tardif présenté comme complet.

Nous avons écarté la notification fondée sur les seuls chiffres des attaquants, car elle risquerait de propager une donnée non vérifiée. Nous avons également écarté l'attente passive, car elle contredirait le délai de l'exercice et la logique de transparence attendue en gestion d'incident.

## Réponse courte au jury

> « Nous avons notifié ce que nous savons, indiqué clairement ce que nous investiguons encore et fixé une date de complément. La transparence ne consiste pas à deviner : elle consiste à partager rapidement des faits qualifiés et à mettre à jour l'autorité. »

## Cadre de conformité et suites

- Le délai de 72 heures est une exigence du **scénario Kasbah**. Dans un cas réel, le DPO et le conseil juridique vérifient les obligations, délais et destinataires applicables.
- La loi n° 09-08 constitue le cadre marocain de protection des données à caractère personnel ; elle soutient une qualification sérieuse des données potentiellement concernées et une gouvernance des informations partagées.
- Le NIST CSF 2.0 soutient la communication coordonnée et la conservation de l'historique des décisions de réponse.
- Joindre une chronologie, les indicateurs confirmés, les mesures prises, les points inconnus, le contact responsable et la date de prochaine mise à jour. Référence commune : [REFERENCES_NORMES_ET_CADRE.md](REFERENCES_NORMES_ET_CADRE.md).
