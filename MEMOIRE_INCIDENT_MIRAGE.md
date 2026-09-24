# Mémoire de crise — AtlasGrid / MIRAGE

Dernière consolidation : 24 septembre 2026. Ce dossier résume les actes I et II avant le dernier acte. Il doit être lu avec la **main courante** : une affirmation externe ne doit jamais dépasser les faits confirmés ci-dessous.

## Situation confirmée

- Incident de ransomware nommé **MIRAGE**, avec extension `.mirage`, affectant 23 serveurs sur 40.
- Les fonctions métier directement touchées sont la paie (PAIE-01), la facturation (FACT-02), les partages de fichiers (FILER-RBT-02 et FILER-CASA-01) et l'ERP (ERP-APP-01 et ERP-DB-01). MSG-01 et DC-01 sont dégradés ; DC-02, WEB-PUB-01 et SCADA-HMI restent intacts.
- Les sauvegardes ont été sabotées : `svc_oasisnet` a modifié la rétention à J-3 ; les trois derniers travaux ont été ignorés ; BKP-01 et BKP-02 sont injoignables. FIN-112 a aussi exécuté `vssadmin delete shadows /all`.
- L'accès `svc_oasisnet` présente des connexions VPN nocturnes non conformes, sans MFA, depuis des IP inhabituelles. Le compte a créé la règle `OUT-TEMP-443`, utilisée ensuite par FIN-112 pour joindre `45.137.184.62:443`.
- Les journaux proxy établissent une exfiltration suspectée de **117,8 Go** sur dix nuits, d'abord depuis FIN-112 puis depuis FILER-RBT, vers `45.137.184.62:443`, SNI `cdn-sync-eu.storage-blob[.]net`, même JA3.
- FIN-112 est le patient zéro établi : le binaire non signé `C:\Windows\svhost32.exe` est lancé à J-1 03:12, Defender est neutralisé, des fichiers sont lus puis renommés en `.mirage`, les mécanismes de récupération sont supprimés et une note MIRAGE est créée.
- Le groupe SIROCCO a publié un échantillon contenant des lignes de données clients et contractuelles. Cela corrobore une exposition ; le chiffre de 300 Go annoncé par l'attaquant n'est pas confirmé par les journaux disponibles.

## Chronologie utile

| Moment | Fait établi | Source |
|---|---|---|
| J-21 à J-1 | Connexions VPN nocturnes anormales de `svc_oasisnet`, sans MFA ; plus de 90 sessions de type 10 sur 21 jours. | A-02, A-10 |
| J-11 02:03 | Création par `svc_oasisnet` de la règle `OUT-TEMP-443`, sans journalisation, de FIN-112 vers HTTPS. | A-09 |
| J-10 à J-1 | Exfiltration nocturne totalisant 117,8 Go vers `45.137.184.62:443`. | A-03 |
| J-3 01:12 | Modification de la politique de rétention des sauvegardes par `svc_oasisnet` ; les sauvegardes J-3, J-2 et J-1 sont ignorées. | A-05 |
| J-1 03:12–03:16 | Exécution de `svhost32.exe` sur FIN-112, neutralisation de Defender, C2, chiffrement `.mirage`, effacement/altération de traces. | A-01, A-04, A-09, A-10, A-12 |
| J-1 15:28 | BKP-01 et BKP-02 deviennent injoignables. | A-05 |
| J2 | 23/40 serveurs confirmés chiffrés ; publication d'un échantillon SIROCCO. | A-13, A-07 |

## Preuves et qualifications conservées

| Pièce | Qualification | Ce qu'elle établit / pourquoi elle est écartée |
|---|---|---|
| A-01 | Preuve | Détection MIRAGE et écriture de masse sur FIN-112 ; quarantaine échouée, binaire non signé. |
| A-02 | Preuve | Accès VPN anormaux de `svc_oasisnet`, sans MFA et hors profil de l'infogérant. |
| A-03 | Preuve | 117,8 Go de flux TLS nocturnes vers la même destination externe. |
| A-04 | Preuve | Horodatages NTFS incohérents sur `LISEZMOI_MIRAGE.txt`, attribué à `svc_oasisnet` sur FILER-RBT-02. |
| A-05 | Preuve | Sabotage de la rétention des sauvegardes et indisponibilité des dépôts. |
| A-07 | Preuve | Échantillon SIROCCO avec données clients/contractuelles ; exposition corroborée à préserver. |
| A-09 | Preuve | Règle OUT-TEMP-443 créée par `svc_oasisnet` et C2 régulier de FIN-112. |
| A-10 | Preuve | Sessions RemoteInteractive, privilèges spéciaux, lancement de `svhost32.exe` et effacement du journal de sécurité. |
| A-11 | Preuve | Phishing `atlasgrid-it.info` : SPF/DMARC en échec, DKIM absent, demande d'identifiants. |
| A-12 | Preuve | Chronologie EDR de FIN-112 : désactivation Defender, lecture de 9 412 fichiers, chiffrement et suppression des sauvegardes locales. |
| A-13 | Preuve | Inventaire de l'impact et priorités métier : 23/40 serveurs chiffrés. |
| A-16 | Fausse piste | Pic de trafic dû à l'article Maghreb Éco, visiteurs humains, cache efficace et aucune dégradation d'origine. |
| A-23 | Preuve | Tentative BEC : domaine sosie, virement de 480 000 MAD demandé ; aucun virement effectué. |
| A-15 | Fausse piste | Ancien jeton mobile d'un ex-salarié non révoqué ; aucune action privilégiée ni lien avec MIRAGE. |
| A-21 | Bruit | Scans Internet génériques Censys/Shodan, SYN seuls et aucun actif interne atteint. |
| A-25 | Bruit | PsExec officiel/signé, maintenance autorisée par le ticket #4502, sans corrélation MIRAGE. |
| A-27 | Bruit | Archivage trimestriel autorisé par le ticket #4381, fichiers relisibles et sans chiffrement. |
| A-26 | Bruit | Connexions à Paris du directeur commercial, appareil connu et activité de messagerie normale. |
| A-40 | Bruit | Ticket OasisNet concernant un autre client et l'extension `.lockb`, sans actif AtlasGrid. |
| A-24 | Fausse piste | Salarié en litige sans accès VPN/AD/badge dans la fenêtre d'attaque et en arrêt documenté. |
| A-18 | Fausse piste | Revendication DarkAtlas incohérente : données publiques, extension/chronologie/canal de rançon différents. |
| A-41 | Bruit | Assistance à distance autorisée, ticket HELP-3391, opérateur identifié et MFA valide. |
| A-22 | Bruit | Faux positif CoinMiner : 7-Zip signé, compilation nocturne planifiée et aucune corrélation MIRAGE. |
| A-19 | Fausse piste | Clé USB-appât analysée sans jamais être connectée à un poste AtlasGrid. |
| A-20 | Fausse piste | Vrai message de migration interne : SPF/DKIM/DMARC valides, intranet AtlasGrid, aucune demande d'identifiants. |
| A-14 | Fausse piste | Badge du stagiaire : lecteur en maintenance, horodatages non fiables, caméra indisponible, aucune corrélation AD/EDR. |
| A-17 | Fausse piste | Copie paie locale autorisée (ticket #4471), en heures ouvrées, 44 Mo et sans sortie réseau. |

## Décisions déjà prises et leurs effets

- **FIN-112 isolé du réseau mais laissé sous tension** : la propagation a été contenue tout en préservant la mémoire et les connexions utiles à l'investigation.
- **Assureur cyber déclaré immédiatement** : dossier ouvert, couverture préservée ; tout coût majeur — y compris une rançon — nécessite un accord écrit.
- **Presse** : réponse factuelle donnée à Maghreb Éco ; l'article est resté équilibré et la communication interne s'est apaisée.
- **Client Chérifienne des Mines** : réponse prudente et factuelle, sans attester une absence d'exposition non prouvée.
- **Autorité** : notification transparente envoyée et reçue ; les éléments complémentaires sont demandés sous 72 heures.
- **OT / SCADA** : service maintenu avec surveillance renforcée ; une nouvelle reconnaissance a été bloquée, aucune session vers le segment industriel n'est établie.

## Garde-fous pour l'acte final

1. Ne pas présenter le phishing A-11 comme la cause technique démontrée de l'intrusion : il est confirmé, mais son lien causal avec MIRAGE reste à établir.
2. Ne pas confirmer le volume de 300 Go, l'identité réelle des opérateurs ou l'exposition d'un client particulier sans recoupement Forensic.
3. Préserver les preuves, les horodatages et les décisions. Continuer à distinguer **fait**, **hypothèse** et **fausse piste** dans toute communication.
4. Préparer une restauration priorisée : identité/services de contrôle, sauvegardes saines ou reconstruction, puis paie, facturation, ERP et partages de fichiers.
5. Garder l'assureur, le régulateur, le Forensic et la direction dans la boucle avant tout engagement financier ou réponse à SIROCCO.

## Captures renommées

Les fichiers sont centralisés dans `assets/captures/`, classés par qualification. Les deux copies archivistiques sans information supplémentaire ont été retirées ; l'extrait initial DarkAtlas est conservé car il est distinct de son analyse finale.

| N° | Fichier | Contenu |
|---:|---|---|
| 01 | `01_A11_entetes_phishing_atlasgrid-it.png` | A-11 — en-têtes du phishing |
| 02 | `02_A01_EDR_FIN-112_MIRAGE.png` | A-01 — alertes Defender |
| 03 | `03_A19_cle_USB_parking_sandbox.png` | A-19 — clé USB-appât |
| 04 | `04_A02_VPN_svc_oasisnet_anormal.png` | A-02 — VPN prestataire |
| 05 | `05_A20_courriel_migration_legitime.png` | A-20 — courriel authentique |
| 06 | `06_A14_badge_DATACENTER_non_fiable.png` | A-14 — badgeuse non fiable |
| 07 | `07_A17_USB_paie_sauvegarde_autorisee.png` | A-17 — copie paie autorisée |
| 08 | `08_A05_sauvegardes_modifiees_indisponibles.png` | A-05 — sauvegardes |
| 10 | `10_A09_regle_firewall_C2.png` | A-09 — règle et C2 |
| 11 | `11_A04_metadonnees_MIRAGE_alterees.png` | A-04 — métadonnées NTFS |
| 12 | `12_A13_inventaire_serveurs_impact.png` | A-13 — impact serveurs |
| 13 | `13_A10_SIEM_acces_svc_oasisnet.png` | A-10 — SIEM |
| 14 | `14_A03_proxy_exfiltration_117_8Go.png` | A-03 — exfiltration |
| 15 | `15_A12_chronologie_EDR_FIN-112.png` | A-12 — chronologie EDR |
| 17 | `17_A16_pic_trafic_presse_legitime.png` | A-16 — trafic légitime |
| 18 | `18_A23_BEC_fraude_au_president.png` | A-23 — BEC |
| 19 | `19_A15_jeton_ex_salarie_sans_lien.png` | A-15 — jeton résiduel |
| 20 | `20_A21_scans_internet_generiques.png` | A-21 — scans génériques |
| 21 | `21_A25_PsExec_maintenance_autorisee.png` | A-25 — maintenance |
| 22 | `22_A27_archivage_trimestriel_autorise.png` | A-27 — archivage |
| 23 | `23_decision_OT_surveillance_renforcee.png` | Décision OT |
| 24 | `24_A26_connexion_Paris_legitime.png` | A-26 — connexion Paris |
| 25 | `25_A40_ticket_OasisNet_autre_client.png` | A-40 — autre client |
| 26 | `26_A24_salarie_litige_hors_de_cause.png` | A-24 — piste insider écartée |
| 27 | `27_A18_revendication_DarkAtlas_extrait.png` | A-18 — extrait partiel conservé |
| 28 | `28_A18_revendication_DarkAtlas_invalidee.png` | A-18 — analyse complète |
| 29 | `29_A41_assistance_distance_autorisee.png` | A-41 — prise en main légitime |
| 30 | `30_A22_faux_positif_cryptominer.png` | A-22 — faux positif |
| 31 | `31_A07_leaksite_SIROCCO_donnees_clients.png` | A-07 — échantillon SIROCCO |
