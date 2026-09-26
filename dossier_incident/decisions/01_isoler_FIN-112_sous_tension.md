# Décision 01 — Isoler FIN-112 en le laissant sous tension

![Capture de la décision 01](../../assets/captures/decisions/01_isoler_FIN-112_sous_tension.png)

## Décision retenue

Retirer immédiatement **FIN-112** du réseau, tout en le laissant allumé et sans effectuer de redémarrage, d'arrêt forcé ou de nettoyage avant l'acquisition des éléments utiles à l'enquête.

## Faits établis au moment du choix

- La preuve **A-01** montre, le jour J à 03:12, l'exécution sur FIN-112 d'un binaire non signé (`svhost32.exe`) par le compte `NT AUTHORITY\\SYSTEM`, la désactivation de Defender et le chiffrement de fichiers avec l'extension `.mirage`.
- La preuve **A-12** confirme le lancement depuis FIN-112 de l'outil de propagation, l'ouverture de quatorze partages SMB et l'exécution à distance sur six hôtes.
- La preuve **A-03** relie FIN-112 à une exfiltration nocturne vers une adresse externe inconnue.

## Pourquoi ce choix est défendable

FIN-112 est à la fois un poste compromis et un point de propagation. L'isoler coupe les communications de commande, l'accès aux partages et une nouvelle diffusion du chiffrement. Le laisser sous tension conserve la mémoire vive, les connexions, les processus et les clés éventuellement utiles à l'analyse. La mesure traite donc le risque immédiat sans détruire les traces volatiles.

Les deux alternatives étaient moins adaptées : le laisser connecté aurait prolongé la propagation ; l'éteindre immédiatement aurait réduit le risque réseau, mais aurait fait disparaître des preuves sensibles et ralenti l'identification du mode opératoire.

## Réponse courte au jury

> « Nous avons isolé la source de propagation dès que les preuves ont établi la compromission, mais nous ne l'avons pas éteinte : le confinement devait stopper l'attaque sans effacer la mémoire et les traces nécessaires pour comprendre, attribuer les actions et rétablir proprement. »

## Cadre de conformité et suites

- Appliquer un confinement ciblé, préserver l'intégrité et la provenance des traces, puis documenter l'action correspond à la logique d'analyse et d'atténuation du NIST CSF 2.0.
- La protection de la confidentialité, de l'intégrité et de la disponibilité du SI est cohérente avec la logique de classification des impacts du cadre marocain de sécurité des SI.
- Consigner l'heure d'isolement, le port ou VLAN coupé, l'état du poste, le responsable et l'image mémoire/disque acquise. Référence commune : [REFERENCES_NORMES_ET_CADRE.md](REFERENCES_NORMES_ET_CADRE.md).
