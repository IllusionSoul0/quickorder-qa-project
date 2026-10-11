# BUG-03: Un restaurant fermé accepte des commandes

- Contexte :  Un restaurant fermé accepte des commandes, Cas de test lié : REG-01.
- Préconditions : Night Sushi `is_open=false`.
- Étapes :
1. POST /api/orders avec `product_id=24`, qté 1, card.
- Résultat attendu : Refus 409 (restaurant fermé).
- Résultat obtenu : 201, commande confirmée. Le code UI (`shop.add`, `checkout`) ne vérifie pas non plus `is_open`.
- Preuve : `POST /api/orders -> 201` (REG-01). Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Commande impossible à livrer.
- Sévérité : Majeur
- Priorité : P1
