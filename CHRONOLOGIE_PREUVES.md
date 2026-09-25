# Chronologie des preuves — incident MIRAGE

Cette chronologie ne contient que les pièces qualifiées **Preuve**. Les repères `J-21`, `J-11`, `J-3`, `J-1`, `J1` et `J2` sont conservés tels qu'ils apparaissent dans les sources. Ils ne sont pas convertis en dates calendaires, faute d'horodatage absolu commun.

## Chaîne principale établie

| Moment | Fait établi | Pièces |
|---|---|---|
| J-21 à J-1, 02:00–05:00 | Le compte prestataire `svc_oasisnet` ouvre à plusieurs reprises des sessions VPN hors horaires, sans MFA, depuis des IP incompatibles avec le profil OasisNet. Plus de 90 sessions RemoteInteractive sont recensées. | A-02, A-10 |
| J-11 02:03 | `svc_oasisnet` crée la règle pare-feu `OUT-TEMP-443` de FIN-112 vers HTTPS, avec journalisation désactivée. | A-09 |
| J-10 à J-1, nuits | Des transferts TLS sortants ont lieu vers `45.137.184.62:443`, d'abord depuis FIN-112 puis FILER-RBT. Volume total : 117,8 Go ; SNI `cdn-sync-eu.storage-blob[.]net`, même empreinte JA3. | A-03 |
| J-3 01:12 | `svc_oasisnet` modifie la politique de rétention des sauvegardes. Les travaux quotidiens J-3, J-2 et J-1 sont ensuite ignorés. | A-05 |
| J-1 03:11 | `svc_oasisnet` reçoit des privilèges spéciaux. | A-10 |
| J-1 03:12:09 | FIN-112 lance le binaire non signé `C:\Windows\svhost32.exe`, depuis `services.exe`. Defender identifie MIRAGE ; la quarantaine échoue. | A-01, A-10, A-12 |
| J-1 03:12:41 | La surveillance en temps réel de Defender est désactivée. | A-12 |
| J-1 03:13:02–03:13:55 | 9 412 fichiers sont lus ; l'EDR relève une écriture de masse. | A-01, A-12 |
| J-1 03:14:07–03:14:31 | FIN-112 communique avec `45.137.184.62:443` grâce à `OUT-TEMP-443` ; le C2 se répète environ toutes les 60 secondes. | A-09, A-12 |
| J-1 03:15:03–03:15:22 | Les fichiers de 14 partages sont renommés `.mirage`. `vssadmin delete shadows /all`, `bcdedit` et `wbadmin delete catalog` sont exécutés ; le service Defender est arrêté. | A-01, A-05, A-12 |
| J-1 03:15:39–03:15:41 | `LISEZMOI_MIRAGE.txt` est créé sur FILER-RBT-02. Ses métadonnées NTFS présentent une incohérence : les dates affichées J1 11:00:07 ne concordent pas avec les traces de création/accès à J-1 03:15. | A-04 |
| J1 03:15 | FIN-112 exécute également la suppression des clichés VSS. | A-05 |
| J1 06:41:22 +0100 | Le serveur AtlasGrid reçoit un phishing provenant de `atlasgrid-it.info` : SPF et DMARC en échec, DKIM absent, lien de saisie d'identifiants. | A-11 |
| J1 15:28 | Les dépôts BKP-01 et BKP-02 deviennent injoignables. | A-05 |
| J2 10:00 | L'inventaire confirme 23 serveurs chiffrés sur 40 : paie, facturation, ERP et partages de fichiers sont directement touchés. | A-13 |
| J2 15:20 | SIROCCO publie un échantillon de données clients et contractuelles, ce qui corrobore une exposition. | A-07 |
| J3 09:30 | L'inventaire confirme que la sauvegarde en ligne est hors service depuis J-3. La copie LTO-9 de Settat est hors réseau, date de J-42 et constitue la source de reprise indépendante. | A-06 |
| J3 | L'analyse d'intégrité montre que RP-J-1 est suspect et RP-J-0 infecté par MIRAGE ; les derniers points en ligne ne doivent pas être utilisés pour restaurer. | A-30 |

## Événement confirmé, mais distinct de la chaîne MIRAGE

| Moment | Fait établi | Pièce |
|---|---|---|
| J2 10:15 | Tentative de fraude au président : usurpation de la PDG, demande de virement de 480 000 MAD vers un IBAN étranger. Aucun virement n'a été effectué. | A-23 |

## Lecture prudente

- La chaîne technique établie est : accès anormaux `svc_oasisnet` → règle de sortie → exfiltration et sabotage des sauvegardes → exécution sur FIN-112 → chiffrement MIRAGE → indisponibilité des sauvegardes et impact métier. La reprise s'appuie ensuite sur la copie air-gap de Settat, les points en ligne récents étant compromis ou suspects.
- Le phishing A-11 est bien confirmé, mais il ne faut pas le présenter comme la porte d'entrée démontrée de MIRAGE sans preuve de corrélation supplémentaire.
- Les 300 Go annoncés par SIROCCO ne sont pas confirmés. Le volume objectivé par les journaux proxy est de 117,8 Go.

## Annexe — détails complets des 14 preuves

### A-02 — Journal VPN FortiGate

- J-21, 02:04–04:52 : `svc_oasisnet`, IP `196.200.114.41`, sans MFA, 1,2 Go sortants.
- J-19, 02:11–03:58 : même IP, sans MFA, 0,8 Go.
- J-16, 02:22–04:39 : IP `102.118.53.17`, sans MFA, 1,4 Go.
- J-14, 01:57–04:20 : même IP, sans MFA, 1,6 Go.
- J-11, 02:03–04:41 : même IP, sans MFA, 1,7 Go.
- J-9, 02:30–05:01 : même IP, sans MFA, 2,1 Go.
- J-4, 02:12–04:44 : même IP, sans MFA, 1,9 Go.
- J-1, 02:15–04:35 : même IP, sans MFA, 1,8 Go.
- Référence attendue : heures ouvrées 09:00–18:00, MFA obligatoire et adresses OasisNet autorisées.

### A-10 — SIEM / journal de sécurité Windows

- J-21 02:04 et J-14 01:57 : EventID 4624, ouverture de session type 10 (RemoteInteractive) par `svc_oasisnet`.
- J-1 03:11 : EventID 4672, privilèges spéciaux attribués à `svc_oasisnet`.
- J-1 03:12 : EventID 4688, création de `C:\Windows\svhost32.exe` par `admin_local`, parent `services.exe`.
- J-1 03:15 : EventID 4657, `Defender DisableRTP = 1`.
- J-1 03:16 : EventID 1102, journal de sécurité effacé.

### A-09 — Pare-feu et canal de commande

- J-11 02:03 : création par `svc_oasisnet` de `OUT-TEMP-443`, source FIN-112, destination HTTPS quelconque, journalisation désactivée.
- J-1 03:14:07, 03:15:07, 03:16:07 et 03:17:08 : connexions de FIN-112 vers `45.137.184.62:443` ; balise régulière d'environ 60 secondes.
- Total : 2 118 sessions vers cette destination ; empreinte JA3 `a0e9f5d2b3c1e847f6...`.

### A-03 — Proxy Zscaler / exfiltration

- J-10, 02:10–04:40 : FIN-112, 11,2 Go.
- J-9, 02:20–04:35 : FIN-112, 12,8 Go.
- J-8, 02:05–04:50 : FILER-RBT, 9,7 Go.
- J-7, 02:15–04:30 : FILER-RBT, 13,4 Go.
- J-6, 02:00–04:45 : FILER-RBT, 12,1 Go.
- J-5, 02:25–04:20 : FILER-RBT, 10,9 Go.
- J-4, 02:10–04:55 : FILER-RBT, 14,0 Go.
- J-3, 02:05–04:25 : FILER-RBT, 12,6 Go.
- J-2, 02:30–04:40 : FILER-RBT, 11,8 Go.
- J-1, 02:15–04:35 : FILER-RBT, 9,3 Go.
- Destination commune : `45.137.184.62:443`, TLS, SNI `cdn-sync-eu.storage-blob[.]net`, même JA3 ; total 117,8 Go.

### A-05 — Sauvegardes

- J-7 à J-4, 01:00 : `Daily-Backup-Job` réussit normalement.
- J-3, 01:12 : `svc_oasisnet` modifie la politique de rétention.
- J-3, J-2 et J-1, 01:15 : les travaux quotidiens sont ignorés parce qu'exclus par la nouvelle politique.
- J1, 03:15 : FIN-112 exécute `vssadmin delete shadows /all` (T1490).
- J1, 15:28 : BKP-01 puis BKP-02 sont injoignables.

### A-01 — Alerte EDR Defender

- J-1, 03:12:09 : `Ransom:Win32/Mirage.A` sur FIN-112, sévérité haute, fichier `C:\Windows\svhost32.exe`, quarantaine échouée, binaire non signé, classification `ML.HighConfidence`.
- J-1, 03:13:55 : `Behavior:Win32/MassFileWrite`, sévérité haute.
- J-1, 03:14:31 : flux sortant vers `45.137.184.62:443`, blocage contourné.
- J-1, 03:15:22 : protection temps réel altérée ; acteur indiqué : `admin_local`.

### A-12 — Chronologie EDR de FIN-112

- J-1 03:12:09 : `svhost32.exe` est créé, non signé, parent `services.exe`.
- 03:12:41 : `Defender\DisableRealtimeMonitoring = 1`.
- 03:13:02 : lecture de 9 412 fichiers `.docx`, `.xlsx`, `.pdf`, `.dwg` et `.dbf`.
- 03:14:31 : connexion vers `45.137.184.62:443`.
- 03:15:03 : renommage `.mirage` sur 14 partages.
- 03:15:07 : `vssadmin delete shadows /all` ; 03:15:08 : `bcdedit /set recoveryenabled no` ; 03:15:09 : `wbadmin delete catalog -quiet`.
- 03:15:22 : arrêt forcé de WinDefend ; 03:15:40 : création de `LISEZMOI_MIRAGE.txt` sur 14 partages.

### A-04 — Métadonnées NTFS

- Objet : `LISEZMOI_MIRAGE.txt`, 14 copies, une par partage chiffré ; hôte FILER-RBT-02, propriétaire `svc_oasisnet`.
- `$FILE_NAME` créé à J-1 03:15:39 ; `$STANDARD_INFORMATION` accédé à J-1 03:15:41.
- Les métadonnées affichent pourtant création et modification à J1 11:00:07 : incohérence temporelle révélant une manipulation de traces.

### A-11 — Hameçonnage

- J1 06:41:22 +0100 : `mx.atlasgrid.ma` reçoit le message depuis `mail.atlasgrid-it.info` (`193.42.55.108`).
- Expéditeur : `support-messagerie@atlasgrid-it.info` ; SPF en échec, DKIM absent, DMARC en échec.
- Objet : « Migration de votre messagerie · action requise avant ce soir » ; lien de saisie d'identifiants : `atlasgrid-it.info/owa/login`.

### A-13 — Étendue de l'impact

- J2 10:00 : 23 serveurs chiffrés sur 40.
- Chiffrés : PAIE-01, FACT-02, FILER-RBT-02, FILER-CASA-01, ERP-APP-01, ERP-DB-01, entre autres.
- Dégradés : MSG-01 et DC-01. Intacts : DC-02, WEB-PUB-01 et SCADA-HMI, ce dernier étant isolé du réseau bureautique.

### A-23 — Fraude au président

- J2 10:15 : message reçu au service comptable, signé « Salima Idrissi », émis depuis `salima.idrissi@atlasgrid-finance.co`.
- Objet : « Virement urgent et confidentiel » ; demande de 480 000 MAD vers un nouvel IBAN étranger. Aucun transfert n'est exécuté.

### A-07 — Publication SIROCCO

- J2 15:20 : capture du site `.onion` SIROCCO LEAKS par le CSIRT, en lecture seule.
- Le site revendique AtlasGrid, annonce 300 Go et affiche un compte à rebours de 24 h.
- Lot de preuve : `clients_extrait.csv`, 2 400 lignes avec données clients et contractuelles. Ces données corroborent l'exposition ; le chiffre de 300 Go reste une revendication non confirmée.

### A-06 — Registre des moyens de sauvegarde

- J3 09:30 : la sauvegarde en ligne quotidienne est hors service depuis J-3.
- Copie trimestrielle LTO-9 : site secondaire de Settat, sans liaison réseau et conservée dans un coffre ignifugé.
- Dernière copie : J-42, volume 38 To, dernier test de restauration absent, estimation de reprise : 5 à 10 jours.

### A-30 — Analyse d'intégrité Veeam

- RP-J-2 est indiqué sain ; RP-J-1 est suspect car le chargeur `svhost32.exe` est présent.
- RP-J-0 est infecté par `MIRAGE.A` et une tâche planifiée.
- La copie air-gap de Settat n'est pas concernée. La restauration depuis les deux derniers points en ligne réintroduirait le rançongiciel.
