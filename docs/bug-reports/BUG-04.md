# BUG-04: Le minimum de commande du restaurant n'est jamais appliqué

- Contexte : Le minimum de commande du restaurant n'est jamais appliqué, Cas de test lié : REG-02.
- Préconditions : Burger Factory : minimum 20 €.
- Étapes :
1. POST /api/orders avec `product_id=3` (3,50 €), qté 1.
- Résultat attendu : Refus : minimum 20 € non atteint.
- Résultat obtenu : 201, commande à 3,50 €.
- Preuve : `POST /api/orders -> 201`, `subtotal=3.5`. Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Commandes non rentables.
- Sévérité : Majeur
- Priorité : P2
