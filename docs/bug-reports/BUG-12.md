# BUG-12: Redirection ouverte via le paramètre `next` du login

- Contexte : Redirection ouverte via le paramètre `next` du login
- Préconditions : Compte alice.
- Étapes :
1. POST /login?next=https://evil.example avec les identifiants d'alice.
- Résultat attendu : Redirection limitée aux URL internes.
- Résultat obtenu : `302 Location: https://evil.example`.
- Preuve : Campagne : `open_redirect_Location = https://evil.example`. Détails dans `evidence/campaign-results.json` ; rejouable avec `tools/run_campaign.py`.
- Impact : Hameçonnage après connexion.
- Sévérité : Majeur
- Priorité : P2
