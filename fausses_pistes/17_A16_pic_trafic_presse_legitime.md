# Fausse piste A-16 — Pic de trafic lié à la presse

![Capture A-16](17_A16_pic_trafic_presse_legitime.png)

## Pourquoi elle paraissait crédible

Un pic de trafic pendant un incident peut évoquer un déni de service ou une reconnaissance hostile. Le service web public devait donc être contrôlé avant d'attribuer l'augmentation à une attaque.

## Vérifications et conclusion

Le pic suit la publication d'un article de **Maghreb Éco**. Les requêtes proviennent de visiteurs humains, le cache absorbe la charge et aucune dégradation d'origine n'est observée. Aucun indicateur de botnet, de saturation ou de compromission du site n'est relevé.

## Pourquoi elle est écartée, sans être ignorée

La cause externe légitime, la nature des requêtes et l'absence d'impact de disponibilité convergent. La piste est écartée pour MIRAGE, tandis que la surveillance du site reste justifiée en raison de la visibilité médiatique.

## Réponse courte au jury

> « Nous avons vérifié le trafic au lieu de l'interpréter. Les métriques montrent un effet médiatique normal, pas une attaque : requêtes humaines, cache efficace et service disponible. »

## Conformité et suites

Conserver les métriques web, l'heure de publication de l'article et le statut des services. Continuer la surveillance, mais ne mobiliser le plan DDoS qu'en présence d'indicateurs techniques concordants. Référence : [REFERENCES_METHODE_ET_CONFORMITE.md](REFERENCES_METHODE_ET_CONFORMITE.md).
