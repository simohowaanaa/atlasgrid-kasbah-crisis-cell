# Preuve A-12 — Chronologie EDR de l'attaque sur FIN-112

![Capture A-12](../../assets/captures/preuves/15_A12_chronologie_EDR_FIN-112.png)

## Fait objectivé

Entre J-1 03:12:09 et 03:15:40, l'EDR enregistre sur FIN-112 : création de `svhost32.exe`, désactivation de Defender, lecture de 9 412 fichiers, connexion à `45.137.184.62:443`, renommage `.mirage` sur quatorze partages, suppression VSS, modification du démarrage, arrêt de WinDefend et création de la note de rançon.

## Pourquoi cette pièce est une preuve

La chronologie EDR ordonne des événements processuels, fichiers, registre et réseau issus d'un même capteur. Elle rend visible le mode opératoire complet : préparation, affaiblissement des protections, chiffrement, propagation et entrave à la reprise.

## Portée et limite

Elle établit les actions observées sur FIN-112 et les partages accessibles depuis celui-ci. Elle ne prouve pas seule l'infection initiale de chaque hôte ni l'auteur humain ; elle doit être croisée avec A-01, A-09, A-10 et A-13.

## Réponse courte au jury

> « A-12 transforme des alertes dispersées en séquence vérifiable. C'est la pièce qui explique pourquoi le confinement devait être immédiat et pourquoi la restauration ne pouvait pas commencer sans assainissement. »

## Conservation et conformité

Exporter la timeline et les artefacts source, préserver l'heure de l'agent EDR, documenter les éventuels écarts d'horloge et produire une copie forensique de FIN-112. Référence : [REFERENCES_CONSERVATION_ET_CONFORMITE.md](REFERENCES_CONSERVATION_ET_CONFORMITE.md).
