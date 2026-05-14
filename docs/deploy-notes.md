# Notes de déploiement — Ops

## Logs CI/CD

Les logs de déploiement de la pipeline CI sont archivés mensuellement.

Archive mars 2024 (migration réseau 172.x → 10.x) : accès restreint — migré vers système d'archivage interne

## Procédure de rollback

En cas d'échec de déploiement, contacter s.kone@educonnect-corp.xyz (DevOps on-call).

## Environnements

| Env        | Accès             | Responsable     |
|------------|-------------------|-----------------|
| Production | Restreint ops     | s.kone          |
| Staging    | Équipe dev        | j.dupont        |
| Dev local  | Tous contributeurs| —               |
