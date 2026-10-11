Périmètre :
Parcours web (inscription, connexion, catalogue, filtres, panier, checkout, commandes, favoris, avis, profil, admin), API REST (`/api/*`, clé `X-API-Key`), paiement simulé.

Hors périmètre :
Performance, charge, accessibilité complète, vrai paiement

Parcours critiques :
- Connexion → panier → checkout → commande confirmée
- Paiement (carte, PayPal, espèces) et montants
- Application des coupons
- Règles restaurant : ouvert, minimum, stock
- Suivi de statut et annulation

Types de tests:
Fonctionnels UI (navigateur + DevTools), API (Swagger / requests), limites, erreurs
