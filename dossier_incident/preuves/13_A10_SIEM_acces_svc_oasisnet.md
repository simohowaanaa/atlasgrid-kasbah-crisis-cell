# Preuve A-10 — Corrélations SIEM du compte `svc_oasisnet`

![Capture A-10](../../assets/captures/preuves/13_A10_SIEM_acces_svc_oasisnet.png)

## Fait objectivé

Le SIEM associe à `svc_oasisnet` des connexions RemoteInteractive (Event ID 4624) à J-21 et J-14, l'attribution de privilèges spéciaux (4672) à J-1 03:11, puis la création de `svhost32.exe` (4688), la désactivation de Defender (4657) et l'effacement du journal de sécurité (1102).

## Pourquoi cette pièce est une preuve

Les événements Windows, centralisés dans le SIEM, apportent des identifiants d'événements, comptes, hôtes et heures. La succession reconstitue des actions administratives anormales autour de la compromission de FIN-112 et peut être rapprochée de l'EDR et du VPN.

## Portée et limite

Le journal établit l'utilisation du compte, non l'identité physique de son utilisateur. L'effacement du journal réduit aussi la visibilité ; il faut préserver les copies déjà centralisées et chercher des sources indépendantes.

## Réponse courte au jury

> « A-10 relie les phases de l'incident dans une source centralisée : accès distant, privilèges, exécution, désactivation de protection et effacement. Mais nous n'attribuons pas ces actions au prestataire sans preuve complémentaire sur l'usage du compte. »

## Conservation et conformité

Exporter les événements avec leur fuseau, les règles de corrélation et le contexte de collecte ; restreindre les identifiants de comptes aux personnes habilitées. La copie centralisée est critique, car le journal local a été effacé. Référence : [REFERENCES_CONSERVATION_ET_CONFORMITE.md](REFERENCES_CONSERVATION_ET_CONFORMITE.md).
