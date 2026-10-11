# BUG-08: La recherche ignore la description des restaurants

- Contexte : La recherche ignore la description des restaurants
- Préconditions : Aucune.
- Étapes :
1. Ouvrir `/?q=japonaise` (UI) puis GET /api/restaurants?q=japonaise.
- Résultat attendu : Tokyo Bowl (description « Cuisine japonaise… »).
- Résultat obtenu : 0 résultat (UI et API).
- Preuve : `recherche_description_UI = []`, API `count = 0`. Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Recherche pauvre.
- Sévérité : Mineur
- Priorité : P3
