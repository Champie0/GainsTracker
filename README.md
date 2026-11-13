# GainsTracker

Carnet de prise de masse, en un seul fichier HTML, qui fonctionne hors ligne.

**Ouvrir l'app : https://champie0.github.io/GainsTracker/**

## Ce que fait l'app

- **Profil** : calcul des besoins (Mifflin-St Jeor + surplus de 300 à 500 kcal) et objectif protéines (1,8 à 2,2 g/kg).
- **Journal** : repas du jour depuis une recette, une photo ou une saisie rapide ; historique des 7 derniers jours.
- **Ma journée** : génère le plan le moins cher qui atteint tes calories et tes protéines, avec une liste de courses regroupée par rayon.
- **Recettes** : 42 recettes simples avec des produits de base, prix en CHF (moyennes Migros / Coop).
- **Photo** : estimation approximative à partir de la description du plat.

## Connexion et données

- Connexion avec **« Continuer avec GitHub »** (Firebase Authentication, projet `gainstracker-85440`).
- Données stockées dans **Cloud Firestore** (région `europe-west6`, Zurich), un document par compte (`users/{uid}`), synchronisées en temps réel entre appareils et disponibles hors ligne.
- Règles Firestore : un compte ne peut lire et écrire que son propre document ; tout le reste est refusé. L'accès est limité à l'UID du propriétaire.
- La configuration web Firebase présente dans `index.html` n'est pas un secret : elle identifie le projet, la sécurité repose sur l'authentification et les règles serveur.
