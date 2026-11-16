# GainsTracker

Carnet de prise de masse, en un seul fichier HTML, qui fonctionne hors ligne.

**Ouvrir l'app : https://champie0.github.io/GainsTracker/**

## Ce que fait l'app

- **Profil** : calcul des besoins (Mifflin-St Jeor + surplus de 300 à 500 kcal) et objectif protéines (1,8 à 2,2 g/kg).
- **Journal** : repas du jour depuis une recette, une photo ou une saisie rapide ; historique des 7 derniers jours.
- **Ma journée** : génère le plan le moins cher qui atteint tes calories et tes protéines, avec une liste de courses regroupée par rayon.
- **Recettes** : 42 recettes simples avec des produits de base, prix en CHF (moyennes Migros / Coop).
- **Estimer un repas** : décris ton repas (et/ou ajoute une photo), Gemini estime calories et protéines aliment par aliment.
- **Coach IA** : propose quoi manger pour finir ta journée (selon ce qu'il te reste, l'heure et ce que tu as sous la main) et de nouvelles idées de repas ; il apprend tes goûts (j'aime / pas pour moi, recettes gardées, aliments fréquents du journal).

## Mode actuel : local

L'app fonctionne **sans compte** : profil, journal, plans et goûts sont enregistrés dans le navigateur de l'appareil (localStorage). Pas de synchronisation entre appareils, et les fonctions IA (estimation, Coach, étapes détaillées) passent par leur repli sans IA.

## Réactiver la connexion, la synchro et l'IA

Le code (connexion GitHub via Firebase Authentication, synchronisation Cloud Firestore, Gemini via Firebase AI Logic avec App Check) est déjà dans `index.html`. Il faut un projet Firebase **créé par un parent, avec son propre compte Google, qui accepte lui-même les conditions** de Firebase et de l'API Gemini. Ensuite :

1. Ajouter une application Web au projet et copier son `firebaseConfig` dans `const FIREBASE_CONFIG`.
2. Créer Firestore (mode production, `europe-west6`) avec ces règles :
   ```
   match /users/{userId} { allow read, write: if request.auth != null && request.auth.uid == userId; }
   ```
3. Authentication → GitHub (app OAuth sur le compte Champie0, URL de rappel `https://PROJET.firebaseapp.com/__/auth/handler` ; le client secret est copié par un humain, jamais dans le dépôt) et domaine autorisé `champie0.github.io`.
4. Pour l'IA : activer Firebase AI Logic (Gemini Developer API), créer une clé reCAPTCHA Enterprise pour `champie0.github.io`, l'enregistrer dans App Check et la copier dans `const RECAPTCHA_SITE_KEY`.

L'ancien projet `gainstracker-85440` n'est plus utilisé par l'app.
