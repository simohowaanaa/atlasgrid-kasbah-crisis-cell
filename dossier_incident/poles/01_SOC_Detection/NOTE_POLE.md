# Pôle SOC / Détection

## Mission et rendu

Le SOC qualifie tous les signaux, tient la main courante et remet la chronologie de l'incident. Les 20 pièces relevant du SOC sont présentes dans ce dossier, y compris les preuves, fausses pistes et bruits : aucune qualification ne doit être perdue.

## Décision prise

**Isoler FIN-112 du réseau, mais le laisser sous tension** — capture `01_isoler_FIN-112_sous_tension.png`.

FIN-112 était le patient zéro, encore actif et connecté. L'isolement coupe la propagation et le C2 ; le maintien sous tension conserve la mémoire vive, les processus et les connexions utiles à l'investigation. Cette décision est justifiée par les alertes A-01, les journaux A-09/A-10 et la chronologie A-12.

## Position à tenir

- La chaîne confirmée repose sur les accès anormaux `svc_oasisnet`, le canal C2, l'exfiltration, la neutralisation des sauvegardes et le chiffrement MIRAGE.
- Chaque fausse piste et bruit reste documenté, notamment la clé USB, le message de migration légitime, l'archivage et les scans Internet.
- Le livrable de référence est la [chronologie des preuves](../../chronologie/CHRONOLOGIE_PREUVES.md).

## Informations complètes du fil

La transcription intégrale des 35 sections SOC du message source est conservée dans `INFORMATIONS_DU_FIL_COMPLET.txt`.
