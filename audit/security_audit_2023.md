# Rapport d'audit sécurité interne — EduConnect Corp
**Date :** 14 novembre 2023  
**Auditeur :** Cabinet ExternalSec (contrat ref. ES-2023-114)  
**Périmètre :** Infrastructure DMZ + LAN + accès distants

---

## Résumé exécutif

L'audit a identifié **7 vulnérabilités**, dont 2 critiques. Les actions correctives ont été planifiées
avec l'équipe IT (contact : j.dupont@educonnect-corp.xyz).

---

## Vulnérabilités identifiées

### [CRITIQUE] VC-01 — Authentification MongoDB désactivée
**Service :** db01 (MongoDB 5.0.x)  
**Détail :** L'instance MongoDB est accessible sans authentification depuis le réseau LAN.  
**Risque :** Accès complet à toutes les bases de données sans credentials.  
**Statut :** ✅ CORRIGÉ — Authentification activée en décembre 2023 (ticket #89)  
**Note de suivi (mars 2024) :** Vérification post-migration à planifier par t.leblanc.

### [CRITIQUE] VC-02 — Credentials hardcodés dans le code source
**Service :** web01 (portail étudiant)  
**Détail :** Identifiants de base de données présents en clair dans `includes/db.php`.  
**Risque :** Exposition des credentials DB si accès au code source.  
**Statut :** ⚠️ PARTIELLEMENT CORRIGÉ — Migration vers variables d'environnement en cours (ticket #198, Q2 2024)

### [HAUTE] VH-01 — Version PHP outdated avec CVEs connues
**Service :** web01  
**Détail :** PHP 7.4.33 — EOL depuis novembre 2022, CVE-2022-31628, CVE-2022-31629 applicables.  
**Statut :** 🔄 EN COURS — Blocage sur compatibilité CMS legacy (ticket #203)

### [HAUTE] VH-02 — Exposition Jenkins sans authentification réseau forte
**Service :** dev01 (Jenkins 2.387.x)  
**Détail :** Interface Jenkins accessible sur LAN sans restriction IP additionnelle.  
**Statut :** ✅ CORRIGÉ — ACL réseau ajoutée, accès restreint à 10.21.0.0/24

### [MOYENNE] VM-01 — Répertoire /backup/ exposé
**Service :** web01  
**Détail :** Le répertoire /backup/ liste les archives disponibles (directory listing activé).  
**Statut :** ✅ CORRIGÉ — Ajout restriction d'accès (décembre 2023)

### [MOYENNE] VM-02 — Absence de politique DMARC/SPF stricte
**Service :** mail01  
**Statut :** ✅ CORRIGÉ — SPF/DMARC configurés (janvier 2024)

### [FAIBLE] VF-01 — Headers HTTP révèlent la stack technique
**Service :** web01  
**Détail :** Headers `X-Powered-By`, `X-Framework`, `Server` exposent les versions.  
**Statut :** 🔄 DIFFÉRÉ — Impact jugé faible, traitement Q3 2024 (ticket #211)

---

## Recommandations prioritaires

1. Finaliser migration credentials DB (ticket #198) — **avant Q2 2024**
2. Mettre à jour PHP 8.x — **avant Q3 2024**  
3. Audit des accès Samba sur files01 — partage `it-backups` accessible à tous les comptes IT

---

*Rapport confidentiel — diffusion restreinte à la direction et à l'équipe IT*
