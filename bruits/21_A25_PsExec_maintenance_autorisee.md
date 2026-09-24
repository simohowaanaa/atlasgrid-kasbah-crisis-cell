# Bruit A-25 — Utilisation légitime de PsExec

![Capture A-25](../assets/captures/bruits/21_A25_PsExec_maintenance_autorisee.png)

## Signal enregistré

PsExec est détecté dans l'environnement. Cet outil peut être utilisé pour une propagation malveillante, ce qui explique son contrôle pendant l'incident.

## Contexte et raison du classement

L'exécutable est officiel et signé ; l'opération est couverte par le ticket de maintenance **#4502**. Son périmètre et son horaire sont autorisés, et aucun indicateur ne le relie à FIN-112, au binaire MIRAGE ou aux flux de commande.

## Réponse courte au jury

> « PsExec est un outil à double usage. Nous ne le classons pas sur son nom : signature, ticket, périmètre et absence de corrélation démontrent ici une maintenance légitime. »

## Suite et conformité

Conserver le ticket, la signature de l'outil, les hôtes concernés et la fenêtre de maintenance. Conserver une liste de contrôle des outils d'administration à double usage. Référence : [REFERENCES_TRIAGE_ET_CONFORMITE.md](REFERENCES_TRIAGE_ET_CONFORMITE.md).
