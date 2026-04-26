# Security

Ne publiez jamais de tokens GLPI, tokens utilisateur, mots de passe SMTP ou fichiers `.env` réels dans GitHub.

Avant chaque commit, vérifiez que le workflow ne contient pas :

- `App-Token` avec une valeur réelle ;
- `Authorization` avec un `user_token` réel ;
- identifiants SMTP ;
- URLs ou emails internes que vous ne souhaitez pas rendre publics.

Rotation recommandée : si un token a déjà été exposé, régénérez-le dans GLPI avant de publier le dépôt.
