# Preuves retenues

Une preuve établit un fait observable dans le dossier. Elle ne transforme pas pour autant une hypothèse plus large en certitude.

| Phase | Pièces | Ce qu'elles permettent d'affirmer |
|---|---|---|
| Accès et préparation | [A-08](36_A08_rapport_preliminaire_OasisNet.md), [A-02](04_A02_VPN_svc_oasisnet_anormal.md), [A-10](13_A10_SIEM_acces_svc_oasisnet.md), [A-09](10_A09_regle_firewall_C2.md) | Une compromission prestataire possible, puis l'usage anormal de `svc_oasisnet` et la préparation d'un canal sortant. |
| Transfert et sabotage | [A-03](14_A03_proxy_exfiltration_117_8Go.md), [A-05](08_A05_sauvegardes_modifiees_indisponibles.md) | 117,8 Go de transferts nocturnes et la dégradation des sauvegardes en ligne. |
| Exécution de MIRAGE | [A-01](02_A01_EDR_FIN-112_MIRAGE.md), [A-12](15_A12_chronologie_EDR_FIN-112.md), [A-04](11_A04_metadonnees_MIRAGE_alterees.md) | L'exécution sur FIN-112, le chiffrement et l'altération des mécanismes de récupération. |
| Impact et exposition | [A-13](12_A13_inventaire_serveurs_impact.md), [A-07](31_A07_leaksite_SIROCCO_donnees_clients.md) | L'impact sur 23 serveurs et la publication d'un échantillon de données. |
| Éléments à conserver séparément | [A-11](01_A11_entetes_phishing_atlasgrid-it.md), [A-23](18_A23_BEC_fraude_au_president.md) | Un phishing et une fraude BEC réels, mais dont le lien causal avec MIRAGE n'est pas démontré. |
| Source de reprise | [A-06](32_A06_registre_moyens_sauvegarde.md), [A-30](35_A30_integrite_sauvegardes_en_ligne.md) | Pourquoi les points en ligne ne sont pas utilisés et pourquoi l'air-gap de Settat est retenu. |

La [chronologie consolidée](../chronologie/FICHE_CHRONOLOGIE_COMPLETE.md) remet ces pièces dans l'ordre des événements.
