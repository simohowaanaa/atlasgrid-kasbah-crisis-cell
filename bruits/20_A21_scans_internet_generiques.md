# Bruit A-21 — Scans Internet génériques

![Capture A-21](20_A21_scans_internet_generiques.png)

## Signal enregistré

Des scans Internet attribuables à des services de cartographie tels que Censys ou Shodan sont observés. Les requêtes sont limitées à des paquets SYN et aucun actif interne AtlasGrid n'est atteint.

## Contexte et raison du classement

Ce type de scan est courant sur les adresses exposées publiquement. Il n'existe ni session établie, ni exploitation, ni corrélation avec FIN-112, `svc_oasisnet`, l'adresse de commande ou la fenêtre de propagation MIRAGE. Le signal ne justifie donc pas d'être intégré à la chaîne d'attaque.

## Réponse courte au jury

> « Nous l'avons vu et journalisé. Mais un scan générique sans connexion établie ni actif atteint est du bruit Internet, pas une preuve d'intrusion AtlasGrid. »

## Suite et conformité

Conserver les journaux réseau et vérifier périodiquement l'exposition publique ; ne déclencher une investigation approfondie qu'en cas de tentative d'exploitation, de connexion réussie ou de corrélation nouvelle. Référence : [REFERENCES_TRIAGE_ET_CONFORMITE.md](REFERENCES_TRIAGE_ET_CONFORMITE.md).
