# Pôle Continuité d'activité

## Mission et rendu

Le pôle protège les actifs critiques, mesure l'impact métier, propose le containment et remet le plan de continuité.

## Décisions prises

**Isoler uniquement les segments critiques** — capture `02_isoler_segments_critiques.png`.

La propagation touchait de nouveaux partages. Ce choix limite l'extension de l'incident tout en évitant un arrêt global qui aggraverait immédiatement la paie, la facturation et les activités encore saines.

**Renforcer la surveillance OT sans couper** — capture `04_OT_surveillance_renforcee_sans_coupure.png`.

Des tentatives de reconnaissance vers la passerelle OT sont détectées, mais aucune session n'est établie vers le segment industriel. Le réseau OT, déjà isolé, reste en production sous surveillance renforcée et avec une capacité de coupure immédiate si le seuil de risque est franchi.

## Priorités de continuité

- A-13 : 23 serveurs sur 40 sont chiffrés ; paie, facturation, ERP et partages sont prioritaires.
- A-05 : les sauvegardes sont indisponibles ou altérées ; restaurer exige des copies saines ou une reconstruction contrôlée.
- La décision SOC d'isoler FIN-112 soutient directement le containment tout en préservant les preuves.

## Informations complètes du fil

La transcription intégrale des 11 sections Continuité d'activité du message source est conservée dans `INFORMATIONS_DU_FIL_COMPLET.txt`.
