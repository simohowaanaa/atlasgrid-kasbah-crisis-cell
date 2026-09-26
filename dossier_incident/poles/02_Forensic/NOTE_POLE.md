# Pôle Forensic

## Mission et rendu

Le pôle Forensic reconstitue le mode opératoire sans transformer une hypothèse en fait. Le dossier rassemble les éléments techniques nécessaires : EDR, SIEM, VPN, pare-feu, proxy, sauvegardes, métadonnées NTFS et revendications publiques.

## Conclusions et décisions analytiques

- **Préserver FIN-112 sous tension après son isolement.** Le pôle confirme l'intérêt forensique : préserver mémoire, processus et traces de C2, tout en empêchant la propagation.
- **Reconstituer une chaîne d'attaque cohérente.** Accès `svc_oasisnet` anormaux, règle `OUT-TEMP-443`, exfiltration vers `45.137.184.62`, sabotage des sauvegardes, exécution de `svhost32.exe`, chiffrement `.mirage` et effacement de traces.
- **Écarter DarkAtlas.** A-18 montre un échantillon déjà public, une extension, une chronologie et un canal de rançon incompatibles avec MIRAGE. Il ne faut pas attribuer l'incident à DarkAtlas.
- **Conserver la publication SIROCCO comme élément à corroborer.** A-07 contient un échantillon de données clients cohérent avec l'exfiltration, mais les 300 Go revendiqués ne sont pas confirmés par les journaux internes.

## Rendu attendu

Des hypothèses d'attaque argumentées, chacune séparant explicitement les faits établis des limites de l'enquête.

## Informations complètes du fil

La transcription intégrale des 6 sections Forensic du message source est conservée dans `INFORMATIONS_DU_FIL_COMPLET.txt`.
