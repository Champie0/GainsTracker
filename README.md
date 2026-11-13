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

Connexion par **nom d'utilisateur + mot de passe**. Ces identifiants ne sont stockés nulle part : ils servent à dériver une clé (PBKDF2-SHA256, 310 000 itérations, sel aléatoire) qui chiffre toutes les données en **AES-256-GCM** dans le navigateur. Un mauvais identifiant rend le déchiffrement impossible. Déconnexion automatique après 5 minutes en arrière-plan.


Tout est enregistré dans le navigateur (localStorage) de l'appareil utilisé. Rien n'est envoyé sur un serveur.
Les données restent d'une visite à l'autre, mais ne se synchronisent pas entre appareils.
