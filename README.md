# GainsTracker

Carnet de prise de masse, en un seul fichier HTML, qui fonctionne hors ligne.

**Ouvrir l'app : https://champie0.github.io/GainsTracker/**

## Ce que fait l'app

- **Profil** : calcul des besoins (Mifflin-St Jeor + surplus de 300 à 500 kcal) et objectif protéines (1,8 à 2,2 g/kg).
- **Journal** : repas du jour depuis une recette, une photo ou une saisie rapide ; historique des 7 derniers jours.
- **Ma journée** : génère le plan le moins cher qui atteint tes calories et tes protéines, avec une liste de courses regroupée par rayon.
- **Recettes** : 42 recettes simples avec des produits de base, prix en CHF (moyennes Migros / Coop).
- **Photo** : estimation approximative à partir de la description du plat.

## Données et accès

L'app est protégée par un code à 4 chiffres, créé au premier lancement sur chaque appareil (seul un hachage SHA-256 salé est stocké). Elle se reverrouille après 5 minutes en arrière-plan.


Tout est enregistré dans le navigateur (localStorage) de l'appareil utilisé. Rien n'est envoyé sur un serveur.
Les données restent d'une visite à l'autre, mais ne se synchronisent pas entre appareils.
