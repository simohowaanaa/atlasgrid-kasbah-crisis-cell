# Preuve A-11 — Courriel d'hameçonnage AtlasGrid-IT

![Capture A-11](01_A11_entetes_phishing_atlasgrid-it.png)

## Fait objectivé

Le jour J1 à 06:41:22 (+0100), le serveur de messagerie reçoit un message de `support-messagerie@atlasgrid-it.info`. SPF et DMARC échouent, aucun DKIM n'est présent et le lien pointe vers une page de saisie d'identifiants externe : `atlasgrid-it.info/owa/login`.

## Pourquoi cette pièce est une preuve

Les en-têtes de messagerie permettent de vérifier l'expéditeur technique, l'IP source (`193.42.55.108`), les contrôles d'authentification et l'URL. Ces éléments sont directement observables, exportables et reproductibles : le message est bien une tentative de phishing.

## Portée et limite

Cette pièce **ne prouve pas** que le phishing a été ouvert, qu'un identifiant a été saisi, ni qu'il est la porte d'entrée de MIRAGE. L'incident principal repose sur une chaîne technique distincte autour de `svc_oasisnet`.

## Réponse courte au jury

> « A-11 prouve une tentative d'hameçonnage réelle, pas l'origine prouvée de MIRAGE. Nous l'avons signalée et recherchée dans les journaux, sans inventer de lien causal. »

## Conservation et conformité

Conserver le message original au format source, ses en-têtes complets, l'URL et son horodatage ; ne pas cliquer sur le lien depuis un poste de production. Les données des destinataires sont limitées aux enquêteurs habilités. Référence : [REFERENCES_CONSERVATION_ET_CONFORMITE.md](REFERENCES_CONSERVATION_ET_CONFORMITE.md).
