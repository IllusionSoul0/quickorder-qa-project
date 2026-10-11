Tests utilisateurs:

- Testeur A : Guillaume 20 ans habitué de uber eat
- Testeur B : Mathis 19 ans

# Scénario 1 : trouver un plat végétarien et le commander

Consigne : Choisis un restaurant, trouve un plat végétarien et passe commande.

Déroulement
Le testeur A est arrivé sur la page d'accueil et a parcouru la liste. Il a choisi Green Kitchen. Il a ensuite trouvé facilement un plat végétarien.

Verbatim A : C'était simple de trouver ce que je voulais

Le testeur B a fait exactement le meme parcours (meme restaurant), il a voulu rajouter le plat Quinoa Bowl le bouton ajouter était toujours disponible malgré le stock à 0

Verbatim B : C'est le nom de restaurant qui faisait le plus végétatarien, mais mon plat que je pouvais ajouter a ma commande n'étais pas disponible

Pistes selon ce qui s'est passé :

- Si un plat en rupture était affiché et ajoutable (Quinoa Bowl) : BUG-06.

# Scénario 2 : appliquer un coupon puis payer en espèces

Consigne : Compose un panier, applique un code promo et paie en espèces.

Déroulement
Le testeur A a trouvé où saisir le code. Il a essayé SAVE20 avec une commande de 15€. Le résultat a été refusé avec message : Montant minimum de 35.00 € requis. Il a ensuite payé 15€ en espèce sans réduction.

Verbatim A : Je n'ai meme pas eu le droit a mon coupon pour ma commande

Le testeur B a passé sa commande rentré le code WELCOME10 ca a marché, cependant il a choisi de ne payer que 3€ en espèce et ca commande est passée.

Verbatim B : Pratique je n'ai payé que 3€ pour une commande de plus de 30€

Pistes selon ce qui s'est passé :

- Montant espèces trop bas a été accepté : BUG-02.

# Scénario 3 : annuler une commande puis la recommander

Consigne : Annule ta dernière commande, puis passe-la à nouveau.

Déroulement
Le testeur A a ouvert Commandes , puis le détail de sa dernière commande et a cliqué sur Annuler la commande . L'annulation a été immédiate, sans demande de confirmation. Le message Commande annulée.  s'est affiché et le statut est passé à cancelled . Il a ensuite cliqué sur Commander à nouveau  et retrouvé son panier identique.

Verbatim A : Ça annule direct, sans me demander si je suis sûr. Sur Uber Eats j'ai toujours une confirmation. 

Le testeur B a suivi le même parcours. Sa commande contenait un produit devenu indisponible entre-temps. Le message 1 produit(s) ajouté(s) au panier.  ne précisait pas lequel manquait.

Verbatim B : Il m'a mis un produit sur deux dans le panier et je n'ai su qu'en vérifiant moi-même. 


# Tableau de synthèse

| Testeur | Scénario | Contexte | Problème | Fréquence | Impact | Verbatim | Hypothèse d'amélioration | Priorité | Bug lié |
|---|---|---|---|---|---|---|---|---|---|
| A | 1 | Accueil | Aucun problème bloquant | A | Aucun | « C'était simple de trouver ce que je voulais » | Aucune | n/a | aucun |
| B | 1 | Accueil | A choisi d'après le nom du restaurant, pas avec le filtre « Végétarien » | B | Mineur | « C'est le nom de restaurant qui faisait le plus végétarien » | Rendre le filtre plus visible | P3 | aucun |
| B | 1 | `/restaurant/3` | Quinoa Bowl en rupture, bouton « Ajouter » actif malgré « HORS STOCK » | B (et auditeur) | Gênant | « Mon plat… n'était pas disponible alors que je pouvais l'ajouter » | Désactiver le bouton si stock = 0 | P2 | BUG-06 |
| A | 2 | Checkout | SAVE20 refusé (minimum 35 €), message en haut de page loin du champ, commande confirmable au prix plein | A | Gênant | « Je n'ai même pas eu le droit à mon coupon pour ma commande » | Afficher le message près du champ avec le montant manquant | P2 | aucun (anomalie UX) |
| B | 2 | Checkout, espèces | 3 € acceptés pour une commande de plus de 30 € | B (et A selon son total) | Bloquant | « Pratique, je n'ai payé que 3 € pour une commande de plus de 30 € » | Refuser un montant inférieur au total | P1 | BUG-02 |
| A | 3 | Détail commande | Annulation sans confirmation | A | Mineur | « Ça annule direct, sans me demander si je suis sûr. » | Ajouter une confirmation | P3 | aucun |
| B | 3 | Recommande | Produit indisponible ignoré sans le signaler | B | Gênant | « Il m'a mis un produit sur deux dans le panier et je n'ai su qu'en vérifiant moi-même. » | Lister les produits non ajoutés | P3 | aucun |

# Conclusion

Les testeurs ont principalement rencontré 3 problèmes, étant presque déjà tous documentés (BUG-02, BUG-06). Le plus pénalisant pour eux a été le dernier car la recommande ne marchait pas bien. 
Priorité recommandée : Regler les changements de stocks a chaque actions étant censé le changer
