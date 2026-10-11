# BUG-07: Le filtre « livraison max » est inversé

- Contexte : Le filtre « livraison max » est inversé
- Préconditions : Aucune.
- Étapes :
1. Ouvrir `/?max_delivery=2.00`.
- Résultat attendu : Seuls les restaurants à ≤ 2,00 € (Green Kitchen, 1,99 €).
- Résultat obtenu : Tous sauf Green Kitchen : Burger Factory, Tokyo Bowl, Pizza Roma, Couscous Atlas, Night Sushi (`>=` au lieu de `<=`).
- Preuve : Campagne : `filtre_livraison_max_2.00`. Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Filtre inutilisable.
- Sévérité : Majeur
- Priorité : P2
