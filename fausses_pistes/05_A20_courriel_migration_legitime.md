# Fausse piste A-20 — Courriel de migration de messagerie légitime

![Capture A-20](05_A20_courriel_migration_legitime.png)

## Pourquoi elle paraissait crédible

Le message évoque une migration de messagerie, thème identique à celui utilisé par le phishing A-11. En période de crise, il était raisonnable de vérifier qu'il ne s'agissait pas d'une nouvelle tentative de collecte d'identifiants.

## Vérifications et conclusion

Les contrôles SPF, DKIM et DMARC sont valides ; le lien dirige vers l'intranet AtlasGrid et le message ne demande pas de mot de passe. Son expéditeur, son contenu et son contexte correspondent à une communication interne authentique.

## Pourquoi elle est écartée, sans être ignorée

La similitude de thème ne suffit pas à qualifier un phishing. Les contrôles d'authentification et la destination interne réfutent l'hypothèse. Cette analyse rappelle toutefois l'importance de distinguer les messages authentiques des domaines sosies.

## Réponse courte au jury

> « Nous avons vérifié ce message parce qu'il ressemblait au leurre A-11. Les preuves d'authentification et le lien intranet permettent de l'écarter : la prudence consiste justement à contrôler, pas à tout classer comme malveillant. »

## Conformité et suites

Archiver les en-têtes et la validation de l'équipe messagerie ; conserver le message selon les règles internes. Sensibiliser les utilisateurs sur les éléments différenciant le domaine officiel du domaine sosie. Référence : [REFERENCES_METHODE_ET_CONFORMITE.md](REFERENCES_METHODE_ET_CONFORMITE.md).
