# Pôle Forensic — fiche visuelle

## Rôle dans la crise

Le pôle Forensic reconstitue le mode opératoire, préserve les traces et sépare les faits établis des hypothèses. Il ne transforme pas une revendication ou un signal isolé en attribution.

## Conclusion à porter

Les éléments convergent vers l'usage anormal de `svc_oasisnet`, une préparation réseau et sauvegarde, puis l'exécution de MIRAGE sur FIN-112. SIROCCO est crédible car son échantillon recoupe le risque d'exposition ; DarkAtlas est écarté faute de concordance technique.

## Captures et explications

### A-01 — Alerte EDR : binaire MIRAGE sur FIN-112

![A-01](../../assets/captures/preuves/02_A01_EDR_FIN-112_MIRAGE.png)

### A-02 — VPN : point d'entrée ou usage de compte à investiguer

![A-02](../../assets/captures/preuves/04_A02_VPN_svc_oasisnet_anormal.png)

### A-05 — Sauvegardes : préparation de l'attaque et entrave à la reprise

![A-05](../../assets/captures/preuves/08_A05_sauvegardes_modifiees_indisponibles.png)

### A-09 — Pare-feu : ouverture du chemin de commande

![A-09](../../assets/captures/preuves/10_A09_regle_firewall_C2.png)

### A-04 — NTFS : horodatages de note de rançon incohérents

![A-04](../../assets/captures/preuves/11_A04_metadonnees_MIRAGE_alterees.png)

### A-10 — SIEM : corrélation accès, privilèges et effacement de trace

![A-10](../../assets/captures/preuves/13_A10_SIEM_acces_svc_oasisnet.png)

### A-03 — Proxy : exfiltration suspectée de 117,8 Go, volume objectivé

![A-03](../../assets/captures/preuves/14_A03_proxy_exfiltration_117_8Go.png)

### A-12 — Chronologie EDR : trois minutes de propagation et sabotage

![A-12](../../assets/captures/preuves/15_A12_chronologie_EDR_FIN-112.png)

### A-18 — Revendication DarkAtlas : extrait initial à contrôler

![A-18 — extrait](../../assets/captures/fausses_pistes/27_A18_revendication_DarkAtlas_extrait.png)

### A-18 — Revendication DarkAtlas invalidée

Les échantillons publics et les indicateurs différents empêchent de lier ce groupe à MIRAGE.

![A-18 — analyse](../../assets/captures/fausses_pistes/28_A18_revendication_DarkAtlas_invalidee.png)

### A-07 — Publication SIROCCO : exposition corroborée, volume non confirmé

![A-07](../../assets/captures/preuves/31_A07_leaksite_SIROCCO_donnees_clients.png)

## Réponse orale proposée

> « Notre reconstitution ne repose pas sur un indicateur unique : elle croise VPN, SIEM, pare-feu, proxy, EDR, sauvegardes et artefacts NTFS. Nous prouvons une chaîne d'actions ; nous ne prétendons pas connaître l'identité physique de l'attaquant. »

Voir aussi [NOTE_POLE.md](NOTE_POLE.md) et [INFORMATIONS_DU_FIL_COMPLET.txt](INFORMATIONS_DU_FIL_COMPLET.txt).
