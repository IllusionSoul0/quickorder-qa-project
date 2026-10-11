# BUG-01: Le paiement PayPal crée deux commandes identiques

-Contexte : Le paiement PayPal crée deux commandes identiques, Cas de test lié : REG-03.
-Préconditions : Client connecté (UI) ou clé API valide.
-Étapes :
1. GET /api/orders : noter `count`.
2. POST /api/orders avec `{"items":[{"product_id":9,"quantity":1},{"product_id":10,"quantity":1}],"payment_method":"paypal"}`.
3. GET /api/orders : comparer `count`.
(UI : même effet au checkout en choisissant PayPal.)
-Résultat attendu : Une seule commande créée (+1), débitée une seule fois.
-Résultat obtenu : Deux commandes créées (+2) et le stock est décrémenté deux fois.
-Preuve : `GET /api/orders` count 6 → 8 (voir REG-03). Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
-Impact : Client facturé deux fois, stock faux.
-Sévérité : Critique
-Priorité : P1
