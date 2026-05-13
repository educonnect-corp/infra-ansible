# EduConnect Infra — Ansible

  Playbooks de déploiement infrastructure EduConnect Corp.

  ## Architecture
  - DMZ (172.20.0.0/24) : web01, mail01
  - LAN (172.21.0.0/24) : dev01 (Jenkins), files01 (Samba)
  - CORE (172.23.0.0/24) : db01 (MongoDB/Redis), root01

  ## Documentation

  Voir `docs/` pour les notes opérationnelles et logs de déploiement.
