# Pôle Direction — fiche visuelle

## Rôle dans la crise

La Direction reçoit l'état de situation, arbitre les priorités, valide la communication et porte le rapport d'incident ainsi que le plan 30 / 60 / 90 jours. Elle ne remplace pas l'enquête : elle décide à partir de faits qualifiés.

## Situation consolidée à présenter

MIRAGE a chiffré 23 serveurs sur 40. Les sauvegardes en ligne ont été sabotées, 117,8 Go de transferts externes sont objectivés et SIROCCO publie un échantillon de données clients. Le pôle doit préserver trois limites : ne pas confirmer 300 Go, l'exposition d'un client particulier ni l'identité des attaquants sans conclusion complémentaire.

## Captures qui portent l'arbitrage

### A-11 — Phishing réel, mais cause de MIRAGE non prouvée

![A-11](../../assets/captures/preuves/01_A11_entetes_phishing_atlasgrid-it.png)

### A-01 — MIRAGE sur FIN-112

![A-01](../../assets/captures/preuves/02_A01_EDR_FIN-112_MIRAGE.png)

### A-02 — Accès prestataire anormaux

![A-02](../../assets/captures/preuves/04_A02_VPN_svc_oasisnet_anormal.png)

### A-05 — Sauvegardes sabotées

![A-05](../../assets/captures/preuves/08_A05_sauvegardes_modifiees_indisponibles.png)

### A-09 — Chemin de sortie et comportement C2

![A-09](../../assets/captures/preuves/10_A09_regle_firewall_C2.png)

### A-04 — Incohérence de métadonnées à prendre en compte

![A-04](../../assets/captures/preuves/11_A04_metadonnees_MIRAGE_alterees.png)

### A-13 — Mesure de l'impact métier

![A-13](../../assets/captures/preuves/12_A13_inventaire_serveurs_impact.png)

### A-10 — Corrélations SIEM

![A-10](../../assets/captures/preuves/13_A10_SIEM_acces_svc_oasisnet.png)

### A-03 — Exfiltration de 117,8 Go objectivée

![A-03](../../assets/captures/preuves/14_A03_proxy_exfiltration_117_8Go.png)

### A-12 — Chronologie de l'attaque sur FIN-112

![A-12](../../assets/captures/preuves/15_A12_chronologie_EDR_FIN-112.png)

### A-23 — Fraude au président, incident distinct et bloqué

![A-23](../../assets/captures/preuves/18_A23_BEC_fraude_au_president.png)

### A-07 — Échantillon publié par SIROCCO

![A-07](../../assets/captures/preuves/31_A07_leaksite_SIROCCO_donnees_clients.png)

## Les huit arbitrages de direction

### 1. Confinement de FIN-112 avec préservation des traces

![Décision 1](../../assets/captures/decisions/01_isoler_FIN-112_sous_tension.png)

### 2. Isolement ciblé des segments critiques

![Décision 2](../../assets/captures/decisions/02_isoler_segments_critiques.png)

### 3. Communication interne mesurée

![Décision 3](../../assets/captures/decisions/03_communication_interne_rassurer_sans_detail.png)

### 4. OT maintenu sous surveillance renforcée

![Décision 4](../../assets/captures/decisions/04_OT_surveillance_renforcee_sans_coupure.png)

### 5. Déclaration immédiate à l'assureur

![Décision 5](../../assets/captures/decisions/05_declaration_assureur_immediate.png)

### 6. Réponse factuelle à la presse

![Décision 6](../../assets/captures/decisions/06_communication_presse_repondre_version.png)

### 7. Réponse prudente au client

![Décision 7](../../assets/captures/decisions/07_reponse_client_rester_factuel.png)

### 8. Notification transparente à l'Autorité

![Décision 8](../../assets/captures/decisions/08_notification_autorite_transparente.png)

## Réponse orale proposée

> « Nous avons contenu l'attaque, préservé les preuves, maintenu les fonctions essentielles sous contrôle et communiqué sans dépasser les faits. Nos décisions sont traçables, proportionnées et révisables à mesure que l'enquête progresse. »

Voir aussi [NOTE_POLE.md](NOTE_POLE.md) et [INFORMATIONS_DU_FIL_COMPLET.txt](INFORMATIONS_DU_FIL_COMPLET.txt).
