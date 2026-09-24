# Preuve A-07 — Publication SIROCCO de données clients

![Capture A-07](31_A07_leaksite_SIROCCO_donnees_clients.png)

## Fait objectivé

Le jour J2 à 15:20, le CSIRT capture en lecture seule le site `.onion` **SIROCCO LEAKS**. Il y trouve `clients_extrait.csv`, comportant 2 400 lignes de données clients et contractuelles. Le site revendique 300 Go et affiche un compte à rebours de 24 heures.

## Pourquoi cette pièce est une preuve

La copie datée du site et le fichier échantillon établissent une publication effective de données clients et contractuelles. Elle corrobore le risque d'exposition déjà signalé par les transferts proxy A-03.

## Portée et limite

La publication de l'échantillon est établie ; en revanche, les **300 Go** annoncés restent une revendication de l'attaquant non confirmée. La capture ne prouve pas non plus à elle seule l'origine exacte de chaque donnée : la comparaison avec les systèmes internes est nécessaire.

## Réponse courte au jury

> « Nous avons une preuve de publication, pas une preuve du volume annoncé. Nous notifions le risque réel et qualifions l'échantillon, sans reprendre la communication de l'attaquant comme un fait établi. »

## Conservation et conformité

Conserver la capture en lecture seule, l'horodatage, le contexte de collecte et l'empreinte du fichier sans rediffuser les données. L'accès aux 2 400 lignes est strictement limité, car elles relèvent potentiellement de la loi n° 09-08. Référence : [REFERENCES_CONSERVATION_ET_CONFORMITE.md](REFERENCES_CONSERVATION_ET_CONFORMITE.md).
