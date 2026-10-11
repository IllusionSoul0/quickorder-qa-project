# BUG-02: Un paiement en espèces insuffisant est accepté

- Contexte : Un paiement en espèces insuffisant est accepté, Cas de test lié : ERR-06.
- Préconditions : Clé API valide.
- Étapes :
1. POST /api/orders avec produit 1, `payment_method=cash`, `cash_received=1`.
- Résultat attendu : 400 : montant insuffisant.
- Résultat obtenu : 201, commande `paid`, `change_due=-13.89`.
- Preuve : `POST /api/orders -> 201`, `change_due: -13.89`.
- Impact : Commande gratuite possible.
- Sévérité : Majeur
- Priorité : P1
