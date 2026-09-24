# Galerie chronologique des captures — AtlasGrid / MIRAGE

Cette galerie accompagne la [fiche de chronologie complète](FICHE_CHRONOLOGIE_COMPLETE.md). Les visuels sont affichés dans l'ordre du déroulé de l'exercice ; ils restent stockés dans leurs dossiers d'origine, sans duplication inutile.

## 0. Briefing et périmètre initial

### Dossier de prise de poste — organisation et inventaire initial

![Dossier de prise de poste : organisation et inventaire](../assets/captures/contexte/01_dossier_prise_de_poste_inventaire_SI.png)

### Dossier de prise de poste — contrats, sauvegardes et attendus

![Dossier de prise de poste : contrats et attendus](../assets/captures/contexte/02_dossier_prise_de_poste_contrats_et_consigne.png)

## 1. Acte I — signaux faibles et premières qualifications

### 01 — A-11 : hameçonnage `atlasgrid-it.info` — Preuve

Le message est techniquement un phishing ; son lien causal avec MIRAGE reste à établir.

![A-11 — En-têtes du phishing](../assets/captures/preuves/01_A11_entetes_phishing_atlasgrid-it.png)

### 02 — A-01 : détection MIRAGE sur FIN-112 — Preuve

L'EDR établit la compromission de FIN-112 et l'écriture massive de fichiers.

![A-01 — EDR FIN-112](../assets/captures/preuves/02_A01_EDR_FIN-112_MIRAGE.png)

### 03 — A-19 : clé USB du parking — Fausse piste

Support suspect analysé en sandbox, mais jamais connecté à AtlasGrid.

![A-19 — Clé USB parking](../assets/captures/fausses_pistes/03_A19_cle_USB_parking_sandbox.png)

### 04 — A-02 : sessions VPN `svc_oasisnet` — Preuve

Accès nocturnes sans MFA et hors profil normal du prestataire.

![A-02 — VPN anormal](../assets/captures/preuves/04_A02_VPN_svc_oasisnet_anormal.png)

### 05 — A-20 : courriel de migration vérifié — Fausse piste

Ce message ressemble au leurre, mais ses contrôles d'authentification et son lien intranet sont valides.

![A-20 — Courriel de migration légitime](../assets/captures/fausses_pistes/05_A20_courriel_migration_legitime.png)

### 06 — A-14 : badge du datacenter — Fausse piste

La badgeuse est en maintenance et aucune corrélation technique indépendante n'existe.

![A-14 — Badge non fiable](../assets/captures/fausses_pistes/06_A14_badge_DATACENTER_non_fiable.png)

### 07 — A-17 : copie USB de paie — Fausse piste

Copie de 44 Mo autorisée par ticket, sans sortie réseau et sans lien avec l'exfiltration.

![A-17 — USB paie autorisée](../assets/captures/fausses_pistes/07_A17_USB_paie_sauvegarde_autorisee.png)

### 08 — A-05 : sauvegardes sabotées — Preuve

La rétention est modifiée avant l'attaque et les dépôts deviennent ensuite indisponibles.

![A-05 — Sauvegardes](../assets/captures/preuves/08_A05_sauvegardes_modifiees_indisponibles.png)

### Décision — Isoler FIN-112 sans l'éteindre

Le confinement coupe la propagation tout en préservant mémoire, processus et connexions utiles à l'enquête.

![Décision : isoler FIN-112 sous tension](../assets/captures/decisions/01_isoler_FIN-112_sous_tension.png)

## 2. Acte II — ransomware, propagation et reconstitution technique

### 09 — A-09 : règle pare-feu et canal de commande — Preuve

La règle `OUT-TEMP-443` ouvre un flux non journalisé, ensuite utilisé à intervalles réguliers par FIN-112.

![A-09 — Règle firewall](../assets/captures/preuves/10_A09_regle_firewall_C2.png)

### 10 — A-04 : métadonnées NTFS de la note MIRAGE — Preuve

Les dates contradictoires imposent de retenir la chronologie corroborée par les autres sources.

![A-04 — Métadonnées altérées](../assets/captures/preuves/11_A04_metadonnees_MIRAGE_alterees.png)

### 11 — A-13 : inventaire de l'impact — Preuve

23 serveurs sur 40 sont chiffrés ; l'inventaire pilote le confinement et la reprise.

![A-13 — Inventaire impact](../assets/captures/preuves/12_A13_inventaire_serveurs_impact.png)

### 12 — A-10 : corrélation SIEM — Preuve

Les événements Windows recoupent le VPN, les privilèges, l'exécution du binaire et l'effacement des traces.

![A-10 — SIEM](../assets/captures/preuves/13_A10_SIEM_acces_svc_oasisnet.png)

### 13 — A-03 : transferts proxy de 117,8 Go — Preuve

Le proxy mesure les flux nocturnes vers une même destination externe ; le contenu exact reste à qualifier.

![A-03 — Exfiltration proxy](../assets/captures/preuves/14_A03_proxy_exfiltration_117_8Go.png)

### 14 — A-12 : chronologie EDR de FIN-112 — Preuve

Les trois minutes d'attaque reconstituent la séquence : exécution, désactivation, lecture, C2, chiffrement et sabotage.

![A-12 — Chronologie EDR](../assets/captures/preuves/15_A12_chronologie_EDR_FIN-112.png)

### Décision — Isoler les segments critiques

Les flux et partages non indispensables sont coupés tout en préservant les activités indispensables.

![Décision : isoler les segments critiques](../assets/captures/decisions/02_isoler_segments_critiques.png)

### Décision — Communication interne mesurée

La cellule répond à la rumeur, sans dévoiler de détails sensibles ni promettre l'absence d'impact.

![Décision : communication interne](../assets/captures/decisions/03_communication_interne_rassurer_sans_detail.png)

## 3. Diversions, incidents parallèles et triage

### 15 — A-16 : pic de trafic lié à la presse — Fausse piste

Le trafic provient de visiteurs humains après un article ; le cache tient et aucun DDoS n'est établi.

![A-16 — Trafic presse légitime](../assets/captures/fausses_pistes/17_A16_pic_trafic_presse_legitime.png)

### 16 — A-23 : fraude au président — Preuve, mais incident distinct

La demande de 480 000 MAD est bloquée. Elle est confirmée, sans être artificiellement reliée à MIRAGE.

![A-23 — BEC](../assets/captures/preuves/18_A23_BEC_fraude_au_president.png)

### 17 — A-15 : jeton d'ex-salarié — Fausse piste

Le jeton résiduel est un défaut de gestion d'accès à corriger, mais aucune activité MIRAGE ne lui est associée.

![A-15 — Jeton résiduel](../assets/captures/fausses_pistes/19_A15_jeton_ex_salarie_sans_lien.png)

### 18 — A-21 : scans Internet génériques — Bruit

Les SYN Censys/Shodan ne touchent pas d'actif interne et ne constituent pas une intrusion AtlasGrid.

![A-21 — Scans génériques](../assets/captures/bruits/20_A21_scans_internet_generiques.png)

### 19 — A-25 : PsExec de maintenance — Bruit

Outil signé, utilisé dans le cadre du ticket #4502 ; aucune corrélation avec MIRAGE.

![A-25 — Maintenance PsExec](../assets/captures/bruits/21_A25_PsExec_maintenance_autorisee.png)

### 20 — A-27 : archivage trimestriel — Bruit

Opération autorisée par le ticket #4381 : les fichiers restent lisibles et ne sont pas chiffrés.

![A-27 — Archivage autorisé](../assets/captures/bruits/22_A27_archivage_trimestriel_autorise.png)

### 21 — Décision OT : surveillance renforcée

Une reconnaissance est détectée sans session compromise. L'OT, déjà isolé, est maintenu avec des critères de coupure explicites.

![Décision OT — capture d'origine](../assets/captures/decisions/23_decision_OT_surveillance_renforcee.png)

![Décision OT — fiche de décision](../assets/captures/decisions/04_OT_surveillance_renforcee_sans_coupure.png)

### 22 — A-26 : connexion Paris — Bruit

Appareil connu, activité de messagerie normale et contexte de déplacement : aucune corrélation MIRAGE.

![A-26 — Connexion Paris](../assets/captures/bruits/24_A26_connexion_Paris_legitime.png)

### 23 — A-40 : ticket OasisNet d'un autre client — Bruit

Le ticket mentionne `.lockb`, mais ne concerne aucun actif AtlasGrid ni les indicateurs MIRAGE.

![A-40 — Autre client](../assets/captures/bruits/25_A40_ticket_OasisNet_autre_client.png)

### 24 — A-24 : salarié en litige — Fausse piste

Les journaux VPN, AD et badge ainsi que l'arrêt de travail écartent la personne de la fenêtre d'attaque.

![A-24 — Salarié hors de cause](../assets/captures/fausses_pistes/26_A24_salarie_litige_hors_de_cause.png)

### 25 — A-18 : extrait initial de la revendication DarkAtlas

La première capture est conservée comme élément de veille ; elle exigeait une comparaison avec les preuves internes.

![A-18 — Extrait DarkAtlas](../assets/captures/fausses_pistes/27_A18_revendication_DarkAtlas_extrait.png)

### 26 — A-18 : revendication DarkAtlas invalidée — Fausse piste

Les données sont publiques et les indicateurs (extension, chronologie, canal) ne correspondent pas à MIRAGE.

![A-18 — Analyse DarkAtlas](../assets/captures/fausses_pistes/28_A18_revendication_DarkAtlas_invalidee.png)

### 27 — A-41 : assistance distante — Bruit

Session autorisée, opérateur identifié, ticket HELP-3391 et MFA valide.

![A-41 — Assistance distante](../assets/captures/bruits/29_A41_assistance_distance_autorisee.png)

### 28 — A-22 : faux positif cryptominer — Bruit

L'alerte vise 7-Zip signé pendant une compilation nocturne ; ni minage ni lien MIRAGE ne sont établis.

![A-22 — Faux positif](../assets/captures/bruits/30_A22_faux_positif_cryptominer.png)

## 4. Pression externe, obligations et exposition

### Décision — Déclarer l'assureur immédiatement

La déclaration respecte le délai de 48 heures propre au scénario et préserve l'accès aux experts et à la couverture.

![Décision : assureur](../assets/captures/decisions/05_declaration_assureur_immediate.png)

### Décision — Répondre à Maghreb Éco

AtlasGrid fournit une version factuelle, sans reprendre la revendication des attaquants comme un fait.

![Décision : presse](../assets/captures/decisions/06_communication_presse_repondre_version.png)

### Décision — Répondre factuellement à Chérifienne des Mines

Le client reçoit les mesures prises et un engagement de mise à jour, sans attestation non prouvée sur son exposition.

![Décision : client](../assets/captures/decisions/07_reponse_client_rester_factuel.png)

### Décision — Notifier l'Autorité de manière transparente

La notification comporte les faits connus, les inconnues et un calendrier de compléments dans le délai de l'exercice.

![Décision : Autorité](../assets/captures/decisions/08_notification_autorite_transparente.png)

### 29 — A-07 : publication SIROCCO — Preuve d'exposition

L'échantillon de données clients et contractuelles est réel. Les 300 Go annoncés demeurent une revendication qui n'est pas confirmée par les journaux internes.

![A-07 — Leak site SIROCCO](../assets/captures/preuves/31_A07_leaksite_SIROCCO_donnees_clients.png)

## Vérification de lecture

- Les événements datés techniquement doivent être cités à partir de la [chronologie technique](FICHE_CHRONOLOGIE_COMPLETE.md#1-chronologie-technique-reconstituée).
- Les deux copies archivistiques A-20 et A-13 ont été retirées ; la capture DarkAtlas initiale est conservée avec son analyse d'invalidation, car elles documentent deux moments distincts.
- La galerie montre des événements de l'exercice, pas une attribution nominative de l'attaque. Toute prise de parole doit respecter les qualifications retenues : preuve, fausse piste, bruit ou décision.
