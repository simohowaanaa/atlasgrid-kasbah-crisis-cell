# Brief de production — cartographie du SI AtlasGrid

**Destinataire :** membre chargé de dessiner la cartographie

**But :** produire une page qui permet au jury de voir immédiatement les zones du SI, les dépendances, les actifs vitaux, les éléments touchés et les accès à risque. Ce brief reprend les informations nécessaires à la production du schéma sans nécessiter de relire le fil de crise.

## 1. Format du rendu

- **Une page** en PDF ou image, lisible à trois mètres.
- En-tête obligatoire : nom de la cellule, ville, date/heure, titre « Cartographie du système d'information AtlasGrid », pôle pilote « Continuité d'activité + SOC ».
- Utiliser des **zones**, des **flèches de dépendance** et une légende simple.
- Ajouter un encadré « À protéger en priorité » avec les trois priorités ci-dessous.
- Chaque élément touché ou suspect doit afficher la référence de la pièce qui le justifie.

## 2. Légende obligatoire

| Apparence | Signification |
|---|---|
| Rouge | Actif vital |
| Gris | Actif secondaire |
| Hachuré ou bord rouge | Actif touché / dégradé |
| Orange | Accès ou dépendance à risque |
| Vert | Actif intact ou isolé à préserver |
| Flèche pleine | Dépendance confirmée |
| Flèche pointillée | Lien fonctionnel ou technique à valider |

Ne pas représenter comme établi un lien absent des sources. Les liens incertains doivent être en pointillé et marqués « à valider ».

## 3. Zones à dessiner

### A. Utilisateurs, clients et Internet

- Postes utilisateurs par service, notamment **FIN-112** (direction financière) et **RH-031**.
- Grands comptes clients, reliés au portail client.
- Internet et hébergeur externe, reliés au site web public.

### B. Services exposés

- **WEB-CLI-01** : portail client, application web IIS, exploité en interne et exposé. Son indisponibilité a été signalée par un client ; l'impact exact est à valider.
- **Site web public** : CMS WordPress chez un hébergeur externe. Distinguer ce site du portail client ; le pic de trafic A-16 était lié à un article de presse, pas à une attaque DDoS.

### C. Services internes transverses

- **DC-01, DC-02** : Active Directory, authentification et droits.
- **MSG-01** : messagerie Exchange 2019.
- **INTRA-01, IPBX-01** : intranet SharePoint et téléphonie VoIP.
- **Console Microsoft Defender for Endpoint** : protection et détection.

### D. Applications et données métier

- **PAIE-01** : Sage Paie, SQL Server.
- **FACT-02** : facturation, application interne et SQL Server.
- **ERP-APP-01, ERP-DB-01** : Sage X3 et base SQL Server, achats, stocks, comptabilité.
- **FILER-RBT-02, FILER-CASA-01** : serveurs de fichiers et partages SMB, documents métiers.

### E. Administration et prestataire

- **VPN-GW** : FortiGate SSL-VPN d'administration.
- **OasisNet** : prestataire ayant un accès distant et exploitant une partie de l'infrastructure.
- Compte de service **`svc_oasisnet`** : accès VPN anormaux sans MFA, à mettre en évidence comme risque majeur.

### F. Sauvegarde et reprise

- **VBR-01, BKP-01, BKP-02** : sauvegardes en ligne Veeam, exploitées par OasisNet.
- **Site secondaire, bandes LTO-9** : copie hors ligne air-gap, recours de dernier ressort.

### G. Réseau industriel / OT

- **SCADA-HMI-*** : supervision énergie/eau, réseau industriel isolé, exploité en interne.
- L'isolation doit apparaître clairement : aucune flèche de circulation libre depuis le SI bureautique. La passerelle OT reste sous surveillance renforcée.

## 4. État actuel des actifs

| Actif | Criticité | État à afficher | Justification |
|---|---|---|---|
| FIN-112 | Secondaire, mais point d'entrée / patient zéro | Isolé du réseau, laissé sous tension | A-01, A-12, décision SOC |
| PAIE-01 | Vital | Chiffré, paie du mois bloquée | A-13 |
| FACT-02 | Vital | Chiffré, clôture impossible | A-13 |
| ERP-APP-01 et ERP-DB-01 | Vital | Chiffrés | A-13 |
| FILER-RBT-02 et FILER-CASA-01 | Vital | Chiffrés ; note MIRAGE sur FILER-RBT-02 | A-04, A-12, A-13 |
| MSG-01 | Important | Partiellement dégradé | A-13 |
| DC-01 | Vital | Partiellement dégradé | A-13 |
| DC-02 | Vital | Intact, réplication OK | A-13 |
| VPN-GW / `svc_oasisnet` | Vital | Accès anormal et suspect ; sans MFA | A-02, A-10 |
| VBR-01 / BKP-01 / BKP-02 | Vital | Sauvegardes altérées ; BKP-01 et BKP-02 injoignables | A-05 |
| Site secondaire LTO-9 | Vital pour la reprise | À préserver, état non documenté | Dossier de prise de poste |
| WEB-CLI-01 | Important | Indisponibilité signalée par client, périmètre à valider | Message client |
| Site web public | Secondaire | Sain ; hausse de trafic liée à la presse | A-16 |
| SCADA-HMI-* / OT | Vital pour la sûreté | Intact, isolé, sous surveillance renforcée | A-13, décision Continuité |

**Note d'impact global :** 23 serveurs sur 40 sont chiffrés (A-13).

## 5. Flèches et dépendances à tracer

### Dépendances confirmées

1. **DC-01 / DC-02 → services internes** : l'annuaire porte l'authentification et les droits.
2. **ERP-APP-01 ↔ ERP-DB-01** : l'applicatif ERP dépend de sa base SQL.
3. **FILER-RBT-02 / FILER-CASA-01 → paie, facturation, ERP** : les partages portent les documents métiers. Le dossier de rendu illustre ce lien ; si le schéma ne peut pas confirmer un lien applicatif précis, utiliser une flèche pointillée « documents métiers à valider ».
4. **VPN-GW ↔ OasisNet ↔ sauvegardes en ligne** : OasisNet possède un accès distant et exploite Veeam, VBR-01, BKP-01 et BKP-02.
5. **BKP-01 / BKP-02 → site secondaire LTO-9** : représenter la copie hors ligne comme solution de reprise distincte de la sauvegarde en ligne compromise.
6. **WEB-CLI-01 ↔ clients grands comptes** : accès de facturation en ligne.
7. **SCADA-HMI-* ↔ réseau OT isolé** : isolation à maintenir ; pas de dépendance bureautique non prouvée.

### Chemin d'attaque à mettre en évidence, sans suraffirmer

Utiliser une flèche orange ou rouge, numérotée avec les pièces :

1. `svc_oasisnet` utilise le VPN hors horaires et sans MFA — **A-02, A-10**.
2. Le compte crée la règle pare-feu `OUT-TEMP-443` depuis FIN-112 — **A-09**.
3. FIN-112 et FILER-RBT envoient 117,8 Go vers `45.137.184.62:443` — **A-03**.
4. La rétention des sauvegardes est modifiée et les travaux sont ignorés — **A-05**.
5. FIN-112 exécute `svhost32.exe`, neutralise Defender, chiffre les partages en `.mirage` et efface des traces — **A-01, A-04, A-12**.

**Important :** le phishing A-11 est une preuve confirmée, mais ne doit pas être dessiné comme la porte d'entrée technique certaine de MIRAGE. L'indiquer séparément comme « phishing confirmé, lien causal à établir ».

## 6. Encadré « À protéger en priorité »

1. **OT / SCADA** : protection de la sûreté des personnes et de la distribution d'énergie ; conserver l'isolation et la surveillance renforcée.
2. **Fichiers métier et reprise** : FILER-RBT-02, FILER-CASA-01, VBR-01, BKP-01/02 et copie LTO-9 ; indispensables à la paie, à la facturation et à la restauration.
3. **VPN d'administration et identités** : VPN-GW, `svc_oasisnet`, DC-01 et DC-02 ; ils conditionnent l'accès à l'ensemble du SI.

## 7. Ce qui ne doit pas figurer comme une menace active

- Clé USB du parking : elle n'a jamais été connectée — A-19.
- Vrai courriel de migration interne — A-20.
- Badge du stagiaire : lecteur non fiable et aucune corrélation — A-14.
- Copie USB du service paie : autorisée — A-17.
- Pic de trafic sur le site public : lié à la presse — A-16.
- Ancien salarié, scans Internet, PsExec légitime, archivage, connexion depuis Paris, ticket ransomware OasisNet, DarkAtlas, assistance à distance et faux positif cryptominer : tous écartés ou sans lien.

## 8. Contrôle final avant export

- Les sept zones sont distinctes et nommées.
- Les 23 serveurs chiffrés et les actifs dégradés sont visibles.
- La légende distingue vital, secondaire, touché, à risque et intact.
- Les flèches de dépendance sont compréhensibles sans explication orale.
- Les trois priorités sont visibles.
- Les références A-01, A-02, A-03, A-04, A-05, A-09, A-10, A-12 et A-13 sont affichées près des éléments qu'elles soutiennent.
- Le schéma reste sur une page et comporte l'en-tête de cellule.
