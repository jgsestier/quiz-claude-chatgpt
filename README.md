# Plutôt Claude ou plutôt ChatGPT ?

Quiz fun (et un peu sérieux) pour aider les entreprises à choisir entre **Claude Team / Enterprise** et **ChatGPT Business / Enterprise**.

10 questions style sondage de magazine, scoring pondéré, verdict en pourcentage, recommandation par persona et un rappel essentiel : **le vrai enjeu n'est pas le choix de l'outil, c'est qui paie l'abonnement.**

## Stack

- HTML / CSS / JavaScript vanilla, 100% client-side
- Aucune dépendance npm, aucun build step
- Google Fonts (Playfair Display, Inter, Caveat) chargées via CDN
- Fichier unique : `index.html`

## Déploiement Vercel

### Option 1 — via GitHub (recommandée)

1. Crée un nouveau repo GitHub (public ou privé), par exemple `quiz-claude-chatgpt`
2. Pousse les deux fichiers à la racine :
   ```bash
   git init
   git add index.html README.md vercel.json
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<ton-user>/quiz-claude-chatgpt.git
   git push -u origin main
   ```
3. Va sur [vercel.com/new](https://vercel.com/new) → importe le repo
4. Framework Preset : **Other** (Vercel détecte un site statique)
5. Build Command : laisser vide
6. Output Directory : `.` (la racine)
7. Clique **Deploy** — c'est tout

L'URL Vercel sera disponible en ~30 secondes. Tu peux ensuite brancher un domaine custom (ex. `quiz.eqxia.com`) depuis Settings → Domains.

### Option 2 — via Vercel CLI

```bash
npm i -g vercel
cd quiz-claude-chatgpt
vercel
# puis pour la prod :
vercel --prod
```

## Customisation rapide

- **Modifier les questions** : tableau `QUESTIONS` dans `index.html`, ligne ~470
- **Modifier les profils de résultat** : tableau `PROFILES`, ligne ~570
- **Modifier les seuils** : champ `minClaude` dans chaque profil (de 0 à 100)
- **Modifier la pondération d'une question** : chaque option a `claude: X, gpt: Y`

## Mesurer l'engagement (optionnel)

Pour tracker le nombre de tests complétés, ajoute un appel à ton outil d'analytics (Plausible, Umami, GA4) dans la fonction `showResults()`. Exemple avec Plausible :

```js
if (window.plausible) {
  plausible('quiz-completed', { props: { claudePct, gptPct } });
}
```

## Crédits

Conçu par [Eqxia](https://eqxia.com) — Applied Intelligence.
Basé sur les capacités publiées en mai 2026 de Claude Team / Enterprise et ChatGPT Business / Enterprise.

## Licence

Quiz libre de réutilisation pour usage interne. Pour usage commercial ou redistribution, merci de citer Eqxia.
