# BUG-06: Les produits en rupture restent visibles et ajoutables au panier (UI)

- Contexte : Les produits en rupture restent visibles et ajoutables au panier (UI)
- Préconditions : Veggie Burger stock 0.
- Étapes :
1. Ouvrir /restaurant/1.
2. Cliquer « Ajouter » sur Veggie Burger.
- Résultat attendu : Produit masqué ou grisé, ajout impossible.
- Résultat obtenu : Produit affiché et ajouté au panier (`/restaurant/1` contient « Veggie Burger »).
- Preuve : Campagne : `rupture_visible_UI_Veggie_Burger = true`. Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Frustration au checkout.
- Sévérité : Moyen
- Priorité : P2
