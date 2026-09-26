# Pôle SOC / Détection — fiche visuelle

## Rôle dans la crise

Le SOC reçoit les signaux, les qualifie et tient la main courante. Son enjeu est de faire émerger la chaîne technique MIRAGE sans confondre une preuve, une fausse piste ou un bruit.

## Ce que le pôle doit démontrer au jury

La chaîne retenue est : accès VPN anormaux `svc_oasisnet` → règle pare-feu de sortie → transferts externes et sabotage des sauvegardes → exécution de MIRAGE sur FIN-112. Les signaux sans corrélation sont conservés, mais ne détournent pas la réponse.

## Captures de preuve suivies par le SOC

### A-11 — Phishing confirmé, lien causal non établi

![A-11](../../../assets/captures/preuves/01_A11_entetes_phishing_atlasgrid-it.png)

### A-01 — Détection MIRAGE sur FIN-112

![A-01](../../../assets/captures/preuves/02_A01_EDR_FIN-112_MIRAGE.png)

### A-02 — Sessions VPN `svc_oasisnet` anormales

![A-02](../../../assets/captures/preuves/04_A02_VPN_svc_oasisnet_anormal.png)

### A-05 — Sauvegardes modifiées et devenues indisponibles

![A-05](../../../assets/captures/preuves/08_A05_sauvegardes_modifiees_indisponibles.png)

### A-09 — Règle pare-feu et canal de commande

![A-09](../../../assets/captures/preuves/10_A09_regle_firewall_C2.png)

### A-10 — Corrélation SIEM du compte et des privilèges

![A-10](../../../assets/captures/preuves/13_A10_SIEM_acces_svc_oasisnet.png)

### A-03 — Transferts proxy de 117,8 Go

![A-03](../../../assets/captures/preuves/14_A03_proxy_exfiltration_117_8Go.png)

## Décision SOC

### Isoler FIN-112 sans couper son alimentation

La décision stoppe la propagation et préserve les éléments volatiles de l'enquête : mémoire, processus et connexions.

![Décision SOC](../../../assets/captures/decisions/01_isoler_FIN-112_sous_tension.png)

## Fausses pistes investiguées puis écartées

### A-19 — Clé USB du parking, non connectée au SI

![A-19](../../../assets/captures/fausses_pistes/03_A19_cle_USB_parking_sandbox.png)

### A-20 — Vrai courriel de migration Exchange

![A-20](../../../assets/captures/fausses_pistes/05_A20_courriel_migration_legitime.png)

### A-14 — Badge datacenter non fiable

![A-14](../../../assets/captures/fausses_pistes/06_A14_badge_DATACENTER_non_fiable.png)

### A-17 — Copie de paie locale autorisée

![A-17](../../../assets/captures/fausses_pistes/07_A17_USB_paie_sauvegarde_autorisee.png)

### A-16 — Pic de trafic expliqué par la presse

![A-16](../../../assets/captures/fausses_pistes/17_A16_pic_trafic_presse_legitime.png)

## Bruits enregistrés, sans lien MIRAGE

### A-21 — Scans Internet génériques

![A-21](../../../assets/captures/bruits/20_A21_scans_internet_generiques.png)

### A-25 — PsExec de maintenance autorisée

![A-25](../../../assets/captures/bruits/21_A25_PsExec_maintenance_autorisee.png)

### A-27 — Archivage trimestriel autorisé

![A-27](../../../assets/captures/bruits/22_A27_archivage_trimestriel_autorise.png)

### A-26 — Connexion Paris légitime

![A-26](../../../assets/captures/bruits/24_A26_connexion_Paris_legitime.png)

### A-40 — Ticket OasisNet d'un autre client

![A-40](../../../assets/captures/bruits/25_A40_ticket_OasisNet_autre_client.png)

### A-41 — Assistance distante autorisée

![A-41](../../../assets/captures/bruits/29_A41_assistance_distance_autorisee.png)

### A-22 — Faux positif CoinMiner

![A-22](../../../assets/captures/bruits/30_A22_faux_positif_cryptominer.png)

## Réponse orale proposée

> « Le SOC a priorisé les éléments reliés, horodatés et corroborés. Nous avons traité les signaux douteux sans les ignorer, mais nous n'avons engagé le confinement qu'à partir de la chaîne technique démontrée. »

Voir aussi [NOTE_POLE.md](NOTE_POLE.md) et [INFORMATIONS_DU_FIL_COMPLET.txt](INFORMATIONS_DU_FIL_COMPLET.txt).
