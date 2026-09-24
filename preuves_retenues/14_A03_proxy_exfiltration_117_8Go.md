# Preuve A-03 — Transferts sortants anormaux de 117,8 Go

![Capture A-03](../assets/captures/preuves/14_A03_proxy_exfiltration_117_8Go.png)

## Fait objectivé

De J-10 à J-1, des transferts TLS nocturnes sont observés vers `45.137.184.62:443`, d'abord depuis FIN-112 puis depuis FILER-RBT. Le volume total objectivé est de **117,8 Go** ; le SNI est `cdn-sync-eu.storage-blob[.]net` et la même empreinte JA3 est relevée sur les flux.

## Pourquoi cette pièce est une preuve

Les journaux proxy enregistrent les hôtes sources, périodes, volumes, destination et caractéristiques TLS. La répétition, le volume et le basculement vers un serveur de fichiers établissent un transfert externe anormal, cohérent avec une exfiltration.

## Portée et limite

Les journaux confirment 117,8 Go transférés, pas la nature exacte de chaque fichier ni les 300 Go revendiqués par SIROCCO. Le contenu TLS n'est pas établi par cette seule pièce ; la qualification des données requiert les journaux de fichiers et les échantillons publiés.

## Réponse courte au jury

> « Nous séparons ce qui est mesuré de ce qui est revendiqué : 117,8 Go sont prouvés par le proxy. Les 300 Go affichés par l'attaquant restent une revendication tant qu'ils ne sont pas corroborés. »

## Conservation et conformité

Conserver les exports proxy complets, la configuration de rétention, le mapping hôte-utilisateur et les données de contexte réseau. Ces journaux pouvant révéler des usages individuels, leur accès reste limité et traçable. Référence : [REFERENCES_CONSERVATION_ET_CONFORMITE.md](REFERENCES_CONSERVATION_ET_CONFORMITE.md).
