Plan d'amélioration:

| # | Amélioration | Justification | Priorité |
|---|---|---|---|
| 1 | Vérifier stock, restaurant ouvert et minimum côté serveur (API + UI) dans une fonction unique | Corrige BUG-03/04/05 | P1 |
| 2 | Supprimer la création du doublon PayPal | Corrige BUG-01, double facturation | P1 |
| 3 | Rejeter les espèces < total | Corrige BUG-02 | P1 |
| 4 | Calculer coupons sur le panier serveur ; aligner ATLAS15 (15 %) | BUG-09, BUG-11 | P2 |
| 5 | Filtrer `next` sur les URL internes ; passer `/logout` en POST | BUG-12 + CSRF | P2 |
| 6 | Machine d'états des commandes | BUG-10 | P2 |
| 7 | Corriger filtre livraison (`<=`) et recherche sur description | BUG-07, BUG-08 | P3 |
| 8 | Masquer/griser les produits en rupture, exiger une adresse complète au checkout | BUG-06, adresse vide | P3 |
