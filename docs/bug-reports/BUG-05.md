# BUG-05: Le stock n'est pas contrôlé : stock négatif

- Contexte : Le stock n'est pas contrôlé : stock négatif, Cas de test lié : LIM-06 / REG-05.
- Préconditions : Salmon Bowl stock 2 ; Veggie Burger stock 0.
- Étapes :
1. POST /api/orders produit 7, qté 3.
2. POST /api/orders produit 4, qté 1.
- Résultat attendu : Refus : stock insuffisant.
- Résultat obtenu : 201 dans les deux cas ; stock final = -1 pour les produits 7 et 4.
- Preuve : `POST /api/orders -> 201` ; stock en base : produit 4 = -1, produit 7 = -1. Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Surventes.
- Sévérité : Critique
- Priorité : P1
