# BUG-09: Le coupon est validé sur un montant fourni par le client

- Contexte : Le coupon est validé sur un montant fourni par le client, Cas de test lié : REG-04.
- Préconditions : Clé API valide.
- Étapes :
1. POST /api/coupons/validate `{"code":"WELCOME10","subtotal":100000}`.
- Résultat attendu : Montant calculé côté serveur à partir d'un panier réel.
- Résultat obtenu : `valid=true, discount=8.0` sans aucun panier.
- Preuve : `POST /api/coupons/validate -> 200 valid:true`. Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Contournement du minimum de coupon.
- Sévérité : Moyen
- Priorité : P3
