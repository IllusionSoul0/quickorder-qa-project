# BUG-10: Transitions de statut impossibles acceptées par l'admin

- Contexte : Transitions de statut impossibles acceptées par l'admin, Cas de test lié : REG-06.
- Préconditions : Admin connecté ; commande créée.
- Étapes :
1. POST /admin/orders/<id>/status `delivered`.
2. POST /admin/orders/<id>/status `confirmed`.
- Résultat attendu : Refus de delivered → confirmed.
- Résultat obtenu : Statut revient à `confirmed`.
- Preuve : GET /api/orders/<id> → `status: confirmed`. Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Historique incohérent.
- Sévérité : Moyen
- Priorité : P2
