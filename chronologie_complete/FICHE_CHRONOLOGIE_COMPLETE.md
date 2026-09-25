# Fiche de chronologie complète — exercice AtlasGrid / MIRAGE

## Portée du document

Cette fiche reconstitue les événements matériels des **actes I, II et III** de l'exercice, depuis la prise de poste de la cellule jusqu'aux choix de reprise après le refus de payer la rançon.

Deux chronologies sont nécessaires :

1. la chronologie **technique réelle**, reconstituée avec les horodatages relatifs `J-21` à `J2` ;
2. la chronologie du **déroulé de l'exercice**, dans l'ordre des 89 sections du fil.

Les captures sont intégrées dans la [galerie chronologique](GALERIE_CAPTURES.md). Chaque capture garde son nom normalisé et reste disponible dans la source unique `assets/captures/`.

### Légende

- **Preuve** : fait technique ou opérationnel établi.
- **Fausse piste** : signal crédible, investigué puis écarté par des éléments vérifiables.
- **Bruit** : événement réel, sans corrélation suffisante avec MIRAGE.
- **Décision** : arbitrage choisi par la cellule et tracé.

## 1. Chronologie technique reconstituée

| Moment | Événement établi et explication | Qualification | Captures / dossiers |
|---|---|---|---|
| J-21 à J-1, nuits | Le compte prestataire `svc_oasisnet` ouvre des sessions VPN entre environ 02:00 et 05:00, sans MFA et depuis des IP incompatibles avec son profil. Les événements SIEM confirment plus de 90 ouvertures RemoteInteractive. | Preuve A-02, A-10 | [VPN](../assets/captures/preuves/04_A02_VPN_svc_oasisnet_anormal.png), [SIEM](../assets/captures/preuves/13_A10_SIEM_acces_svc_oasisnet.png) |
| J-11, 02:03 | `svc_oasisnet` crée la règle `OUT-TEMP-443` depuis FIN-112 vers HTTPS, avec journalisation désactivée. Cette préparation permet ensuite une communication sortante non contrôlée. | Preuve A-09 | [Pare-feu](../assets/captures/preuves/10_A09_regle_firewall_C2.png) |
| J-10 à J-1, nuits | FIN-112 puis FILER-RBT transfèrent au total **117,8 Go** vers `45.137.184.62:443`, avec le même SNI et la même empreinte JA3. Le volume est établi ; le contenu précis et les 300 Go revendiqués ne le sont pas encore. | Preuve A-03 | [Proxy](../assets/captures/preuves/14_A03_proxy_exfiltration_117_8Go.png) |
| J-3, 01:12 | La rétention des sauvegardes est modifiée par `svc_oasisnet`. Les travaux J-3, J-2 et J-1 deviennent exclus, compromettant la restauration avant même le chiffrement. | Preuve A-05 | [Sauvegardes](../assets/captures/preuves/08_A05_sauvegardes_modifiees_indisponibles.png) |
| J-1, 03:11–03:12 | Le compte reçoit des privilèges spéciaux. Sur FIN-112, `svhost32.exe`, binaire non signé, démarre depuis `services.exe` ; Defender détecte MIRAGE mais sa quarantaine échoue. | Preuve A-01, A-10, A-12 | [EDR alerte](../assets/captures/preuves/02_A01_EDR_FIN-112_MIRAGE.png), [chronologie EDR](../assets/captures/preuves/15_A12_chronologie_EDR_FIN-112.png) |
| J-1, 03:12–03:16 | Defender est désactivé ; 9 412 fichiers sont lus ; FIN-112 contacte l'adresse externe ; 14 partages sont renommés `.mirage` ; VSS, BCD et catalogue de sauvegarde sont supprimés ; une note de rançon est créée. | Preuve A-01, A-09, A-12 | [A-01](../assets/captures/preuves/02_A01_EDR_FIN-112_MIRAGE.png), [A-09](../assets/captures/preuves/10_A09_regle_firewall_C2.png), [A-12](../assets/captures/preuves/15_A12_chronologie_EDR_FIN-112.png) |
| J-1, 03:15:39–03:15:41 | La note `LISEZMOI_MIRAGE.txt` apparaît sur FILER-RBT-02. Ses attributs NTFS ne concordent pas avec les dates affichées, signe d'une incohérence de traces à conserver et analyser. | Preuve A-04 | [Métadonnées NTFS](../assets/captures/preuves/11_A04_metadonnees_MIRAGE_alterees.png) |
| J1, 03:15 puis 15:28 | La suppression des clichés est confirmée et les dépôts BKP-01 / BKP-02 deviennent injoignables. Il faut vérifier la copie hors ligne plutôt que promettre une restauration. | Preuve A-05 | [Sauvegardes](../assets/captures/preuves/08_A05_sauvegardes_modifiees_indisponibles.png) |
| J1, 06:41:22 (+0100) | Un phishing `atlasgrid-it.info` est reçu : SPF/DMARC en échec, DKIM absent, lien de saisie d'identifiants. Le phishing est réel, mais son lien causal avec MIRAGE n'est pas établi. | Preuve A-11 | [En-têtes](../assets/captures/preuves/01_A11_entetes_phishing_atlasgrid-it.png) |
| J2, 10:00 | L'inventaire constate 23 serveurs chiffrés sur 40, dont paie, facturation, ERP et serveurs de fichiers. L'OT/SCADA reste isolé et intact ; MSG-01 et DC-01 sont dégradés. | Preuve A-13 | [Impact](../assets/captures/preuves/12_A13_inventaire_serveurs_impact.png) |
| J2, 10:15 | Une fraude au président demande 480 000 MAD. Le virement est bloqué. C'est un incident financier confirmé mais distinct de la chaîne MIRAGE. | Preuve A-23 | [BEC](../assets/captures/preuves/18_A23_BEC_fraude_au_president.png) |
| J2, 15:20 | SIROCCO publie un échantillon de 2 400 lignes de données clients et contractuelles. Cela corrobore l'exposition ; le volume de 300 Go affiché par le groupe reste non confirmé. | Preuve A-07 | [Leak site](../assets/captures/preuves/31_A07_leaksite_SIROCCO_donnees_clients.png) |
| J3, 09:30 | L'inventaire de reprise indique que la sauvegarde en ligne est indisponible depuis J-3. La copie LTO-9, isolée à Settat, date de J-42 et n'a jamais été testée ; elle reste néanmoins séparée du réseau compromis. | Preuve A-06 | [Registre](../assets/captures/preuves/32_A06_registre_moyens_sauvegarde.png), [air-gap](../assets/captures/preuves/34_A06_copie_airgap_Settat.png) |
| J3 | L'analyse Veeam établit que le point RP-J-1 est suspect et que RP-J-0 est infecté par MIRAGE. Restaurer depuis ces points risquerait de réintroduire le rançongiciel. | Preuve A-30 | [Analyse d'intégrité](../assets/captures/preuves/35_A30_integrite_sauvegardes_en_ligne.png) |

## 2. Chronologie du déroulé de l'exercice

| Séquences du fil | Événements et explication | Statut / conséquences |
|---|---|---|
| **1–2 — Briefing** | La PDG confie la cellule de crise, décrit les lenteurs et alertes dispersées, puis fournit le dossier de prise de poste. Le premier rendu demandé est la cartographie des actifs critiques et dépendances. | Cadre initial ; voir les deux captures du dossier de prise de poste dans la galerie. |
| **3–8 — Premiers signaux** | Le SOC signale une campagne de phishing, des lenteurs et des tickets multiples. A-11 et A-01 sont versés à l'analyse. OasisNet évoque d'abord une maintenance dégradée. Un salarié confirme avoir saisi des identifiants sur un message suspect. | A-11 et A-01 sont qualifiés preuves ; l'hypothèse « simple maintenance » reste alors insuffisante. |
| **9–14 — Clé USB et premiers recoupements** | Une clé USB trouvée sur le parking est analysée en sandbox. Le VPN prestataire A-02 et les fichiers `.mirage` apparaissent. La clé n'ayant jamais été connectée au SI, elle est écartée. | A-19 est une fausse piste ; A-02 devient un élément central de la chaîne d'accès. |
| **15–18 — Impact client et patient zéro** | Le portail de facturation devient inaccessible. Le courriel A-20 est vérifié comme authentique. FIN-112 est identifié comme patient zéro, isolé du réseau tout en restant sous tension. | Décision : confinement de FIN-112, conservation des traces mémoire et C2. |
| **19–26 — Triage humain, interne et sauvegardes** | Une anomalie de badge est investiguée ; les équipes demandent une communication ; une clé de paie est contrôlée ; A-20 est confirmé légitime. Le journal A-05 révèle le sabotage des sauvegardes. | A-14 et A-17 sont écartées ; A-05 est retenue comme preuve critique. |
| **27–35 — Acte II : rançon et reconstitution** | La note SIROCCO annonce 20 BTC. Sont ensuite qualifiés : règle C2 A-09, métadonnées A-04, impact A-13, authentifications A-10, exfiltration A-03 et chronologie EDR A-12. La PDG demande des options tracées. | Passage officiel d'un incident ambigu à une crise de ransomware avec extorsion. |
| **36–43 — Diversions et BEC** | Le stagiaire est mis hors de cause ; le DDoS apparent est expliqué par un article de presse ; un ancien compte et une copie de paie sont examinés. Une fraude au président A-23 est détectée et bloquée. | A-14, A-16, A-15 et A-17 sont écartées ; A-23 est une preuve d'incident parallèle. |
| **44–55 — Confinement et communication interne** | Les serveurs encore actifs font l'objet d'un arbitrage : isolement ciblé des segments critiques, conservation de l'OT et du site public. La cellule répond à la rumeur interne sans promettre ce qu'elle ne peut démontrer. | Décisions : segmentation ciblée ; communication interne rassurante, mais limitée aux faits. |
| **56–65 — OT, assurance et autres bruits** | Une reconnaissance vers l'OT est détectée mais sans session établie : surveillance renforcée, pas de coupure immédiate. Archivage A-27, accès Paris A-26 et ticket A-40 sont triés. Le sinistre est déclaré à l'assureur. | Décisions : maintien OT sous critères de coupure ; déclaration immédiate de l'assureur. A-27, A-26 et A-40 sont des bruits. |
| **66–74 — Attribution prudente et presse** | La piste d'un salarié en litige est vérifiée. DarkAtlas revendique l'attaque, mais son échantillon et ses indicateurs ne concordent pas. L'assureur ouvre le dossier. Maghreb Éco demande une réaction avant 17:00 ; AtlasGrid répond factuellement. | A-24 et A-18 sont écartées. Décision : donner une version vérifiée à la presse ; l'article reste équilibré. |
| **75–82 — Assistance, faux positif et client** | Une prise en main distante est validée par le ticket HELP-3391 et MFA ; un faux positif CoinMiner est attribué à 7-Zip et une compilation planifiée. Le client Chérifienne des Mines demande une garantie ; la cellule répond avec les faits confirmés et un calendrier de mise à jour. | A-41 et A-22 sont des bruits. Décision : réponse client factuelle, sans attestation non prouvée. |
| **83–89 — Autorité et preuve d'exposition** | L'Autorité demande des éléments sous 72 h. La cellule notifie immédiatement, l'accusé de réception est favorable. DarkAtlas est définitivement invalidé. SIROCCO publie ensuite l'échantillon A-07. | Décision : notification transparente et évolutive. A-07 corrobore le risque d'exposition. |
| **Acte III — Reconstruire** | Les sauvegardes sont inventoriées puis analysées. La cellule refuse de payer, retient la copie air-gap de Settat et priorise le cœur ERP, dont dépendent la paie et la facturation. | Reprise à partir de l'air-gap : AD, ERP et base, paie/facturation, puis partages de fichiers. ETA annoncée : 5 à 10 jours ; perte de données estimée : six semaines. |

## 3. Décisions à replacer dans la chronologie

| Décision | Moment du déroulé | Motif synthétique | Capture |
|---|---|---|---|
| Isoler FIN-112 sous tension | Séquences 15–18 | Arrêter la propagation et préserver les traces volatiles. | [Capture](../assets/captures/decisions/01_isoler_FIN-112_sous_tension.png) |
| Isoler les segments critiques | Séquences 44–55 | Réduire le rayon d'impact tout en préservant les services essentiels. | [Capture](../assets/captures/decisions/02_isoler_segments_critiques.png) |
| Communiquer en interne sans détails sensibles | Séquences 44–55 | Réduire la rumeur, protéger l'enquête et éviter une promesse non vérifiée. | [Capture](../assets/captures/decisions/03_communication_interne_rassurer_sans_detail.png) |
| Surveiller l'OT sans coupure immédiate | Séquences 56–65 | L'OT est isolé et non compromis ; une coupure préventive aurait un coût opérationnel et de sûreté élevé. | [Capture](../assets/captures/decisions/04_OT_surveillance_renforcee_sans_coupure.png) |
| Déclarer l'assureur immédiatement | Séquences 56–65 | Respecter la règle des 48 h du scénario et préserver la couverture. | [Capture](../assets/captures/decisions/05_declaration_assureur_immediate.png) |
| Répondre à la presse | Séquences 66–74 | Ne pas laisser une revendication externe devenir le seul récit public. | [Capture](../assets/captures/decisions/06_communication_presse_repondre_version.png) |
| Répondre factuellement au client | Séquences 75–82 | Informer sans attester une absence d'exposition non établie. | [Capture](../assets/captures/decisions/07_reponse_client_rester_factuel.png) |
| Notifier l'Autorité avec les faits connus | Séquences 83–89 | Respecter le délai de 72 h propre à l'exercice et compléter l'analyse ensuite. | [Capture](../assets/captures/decisions/08_notification_autorite_transparente.png) |
| Ne pas payer la rançon | Acte III | Aucune garantie de déchiffrement ou d'effacement ; la reprise hors ligne évite de financer l'extorsion. | [Capture](../assets/captures/decisions/09_direction_ne_pas_payer.png) |
| Restaurer le cœur ERP en priorité | Acte III | ERP constitue le socle commun dont dépendent la paie et la facturation. | [Capture](../assets/captures/decisions/11_priorite_restauration_ERP.png) |
| Restaurer depuis l'air-gap de Settat | Acte III | Les derniers points en ligne sont suspects ou infectés ; l'air-gap est la source indépendante. | [Capture](../assets/captures/decisions/12_choix_airgap_Settat.png) |

## 4. Points à retenir pour l'oral

1. La chaîne la plus étayée est : accès anormaux `svc_oasisnet` → règle de sortie → exfiltration et sabotage des sauvegardes → exécution sur FIN-112 → chiffrement MIRAGE → impact métier et exposition corroborée.
2. Le phishing A-11 est confirmé, mais il ne doit pas être présenté comme la porte d'entrée technique démontrée.
3. Le volume objectivé est 117,8 Go ; les 300 Go annoncés par SIROCCO sont une revendication non confirmée.
4. Les fausses pistes, les bruits et les incidents parallèles sont conservés parce qu'ils démontrent une méthode de triage rigoureuse.
5. La galerie contient les captures des actes I à III, y compris les décisions de reprise et les pièces A-06 et A-30.

Voir la [galerie de toutes les captures](GALERIE_CAPTURES.md) et les fiches détaillées dans [`preuves_retenues/`](../preuves_retenues/), [`fausses_pistes/`](../fausses_pistes/), [`bruits/`](../bruits/) et [`decisions/`](../decisions/).
