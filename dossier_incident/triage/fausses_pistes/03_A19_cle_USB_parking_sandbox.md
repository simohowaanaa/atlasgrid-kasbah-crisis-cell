# Fausse piste A-19 — Clé USB trouvée sur le parking

![Capture A-19](../../../assets/captures/fausses_pistes/03_A19_cle_USB_parking_sandbox.png)

## Pourquoi elle paraissait crédible

Une clé USB abandonnée peut être un vecteur d'infection volontaire. Dans le contexte d'un ransomware, elle devait être isolée et analysée, jamais connectée directement à un poste AtlasGrid.

## Vérifications et conclusion

La clé a été analysée en environnement de sandbox. Aucun branchement sur un équipement AtlasGrid n'est constaté et aucun artefact de son contenu n'apparaît dans les journaux EDR ou les événements de FIN-112. Elle ne peut donc pas expliquer la compromission MIRAGE connue.

## Pourquoi elle est écartée, sans être ignorée

L'absence de contact avec le SI rend impossible une chaîne de propagation depuis cette clé vers AtlasGrid. La piste est clôturée pour MIRAGE, mais le support est conservé comme élément de sûreté et ses indicateurs peuvent être recherchés par précaution.

## Réponse courte au jury

> « Le risque était crédible, mais nous avons appliqué une règle simple : pas de lien technique, pas d'attribution. La clé n'a jamais touché le SI ; elle ne peut pas être présentée comme l'origine de MIRAGE. »

## Conformité et suites

Conserver le support, la copie sandbox et les empreintes ; ne pas le reconnecter. Diffuser les indicateurs techniques, pas les éventuelles données personnelles inutiles. Référence : [REFERENCES_METHODE_ET_CONFORMITE.md](REFERENCES_METHODE_ET_CONFORMITE.md).
