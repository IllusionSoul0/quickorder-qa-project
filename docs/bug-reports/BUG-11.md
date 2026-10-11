# BUG-11: ATLAS15 annoncé à -15 % mais appliqué à 10 %

- Contexte : ATLAS15 annoncé à -15 % mais appliqué à 10 %
- Préconditions : Restaurant Couscous Atlas.
- Étapes :
1. Lire le texte promo de Couscous Atlas.
2. POST /api/coupons/validate `ATLAS15`, subtotal 100.
- Résultat attendu : Réduction de 15 €.
- Résultat obtenu : 10,00 € (`discount_percent=10`).
- Preuve : `ATLAS15_100€ = {discount: 10.0, discount_percent: 10.0}`. Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Publicité mensongère.
- Sévérité : Moyen
- Priorité : P2
