# GLPI - Rapport journalier automatisé

Workflow n8n pour générer et envoyer un rapport quotidien GLPI par email.

## Fonctionnalités

- Initialisation de session GLPI via API REST.
- Comptage des tickets par statut : en cours, en attente, affectés, résolus.
- Suivi des tickets critiques, SLA dépassés et backlog de plus de 7 jours.
- Analyse de charge par technicien.
- Génération d’un rapport HTML compact et lisible.
- Envoi automatique par SMTP.
- Fermeture de session GLPI en fin de traitement.

## Sécurité

Les tokens et identifiants sensibles ont été retirés du workflow exporté. Avant import dans n8n, configurez les variables d’environnement suivantes :

```env
GLPI_BASE_URL=https://votre-domaine-glpi.tld
GLPI_APP_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxx
GLPI_USER_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxx
REPORT_FROM_EMAIL=example@example.com
REPORT_TO_EMAIL=support@example.com
```

Le workflow utilise ces variables dans les requêtes HTTP au lieu de stocker les tokens en clair dans le JSON.

## Import dans n8n

1. Importer `GLPI-Rapport-journalier.sanitized.json` dans n8n.
2. Configurer les variables d’environnement ci-dessus.
3. Sélectionner à nouveau le credential SMTP dans le node `Envoyer Rapport Email`.
4. Tester le workflow manuellement.
5. Ajouter un déclencheur planifié si nécessaire.

## Points à adapter

- Domaine GLPI via `GLPI_BASE_URL`.
- Destinataires email via `REPORT_TO_EMAIL`.
- Mapping des statuts GLPI dans les nodes JavaScript si votre instance utilise une configuration différente.
- Critères de priorité, urgence et SLA selon les règles internes.

## Fichiers

- `GLPI-Rapport-journalier.sanitized.json` : workflow n8n prêt à partager.
- `.env.example` : exemple de variables à configurer.
- `SECURITY.md` : consignes pour éviter de publier des secrets.
