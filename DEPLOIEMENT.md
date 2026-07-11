# Mettre le site en ligne — GitHub + Cloudflare Pages

Guide pas à pas, sans ligne de commande, tout se fait dans le navigateur.

Tu as reçu 3 fichiers/dossiers à mettre en ligne :
```
site-hypnose/
├── index.html
└── assets/
    ├── style.css
    ├── logo-hybou.png
    └── logo-hybou-square.png
```

---

## Étape 1 — Créer un dépôt GitHub

1. Va sur [github.com](https://github.com) et connecte-toi (ou crée un compte gratuit avec "Sign up").
2. En haut à droite, clique sur le **+** puis **New repository**.
3. Renseigne :
   - **Repository name** : `site-hypnose` (ou le nom que tu veux)
   - Laisse-le en **Public** (ça n'affecte pas la sécurité du site, ce sont juste les fichiers du code)
   - Ne coche aucune case ("Add a README", etc.)
4. Clique sur **Create repository**.

---

## Étape 2 — Envoyer les fichiers sur GitHub (sans ligne de commande)

1. Sur la page de ton nouveau dépôt (vide), clique sur le lien **uploading an existing file**.
2. Sur ton ordinateur, ouvre le dossier `site-hypnose` que je t'ai fourni.
3. **Glisse-dépose** dans la fenêtre GitHub :
   - le fichier `index.html`
   - le dossier `assets` en entier (avec `style.css` et `logo-hybou.svg` dedans)

   ⚠️ Important : il faut que la structure reste identique une fois en ligne, c'est-à-dire que `index.html` soit à la racine du dépôt, et que `assets/style.css` + `assets/logo-hybou.svg` soient bien dans un sous-dossier `assets`. Si tu glisses le dossier `assets` complet, GitHub conserve automatiquement cette structure.
4. En bas de page, clique sur **Commit changes** (le bouton vert).

Tes fichiers sont maintenant sur GitHub.

---

## Étape 3 — Connecter le dépôt à Cloudflare Pages

1. Va sur [dash.cloudflare.com](https://dash.cloudflare.com) et connecte-toi à ton compte Cloudflare.
2. Dans le menu de gauche, clique sur **Workers & Pages**.
3. Clique sur **Create** (ou **Create application**), puis choisis l'onglet **Pages**.
4. Clique sur **Connect to Git**.
5. Autorise Cloudflare à accéder à ton compte GitHub si demandé, puis sélectionne le dépôt **site-hypnose**.
6. Clique sur **Begin setup**.

### Paramètres de build (build settings)

Renseigne exactement ceci :

| Champ                     | Valeur                  |
|---------------------------|-------------------------|
| Framework preset           | `None`                  |
| Build command              | *(laisser vide)*        |
| Build output directory     | `/`                     |

7. Clique sur **Save and Deploy**.

Cloudflare va publier le site. Après 1 à 2 minutes, tu obtiens une adresse du type :
`https://site-hypnose-xxx.pages.dev`

C'est ton site, déjà en ligne et accessible à tous.

---

## Étape 4 — Brancher ton domaine hybou.com

Tu possèdes déjà **hybou.com** (utilisé comme filigrane sur tes visuels). Voici comment le brancher sur ce nouveau site :

1. Dans ton projet Cloudflare Pages, va dans l'onglet **Custom domains**.
2. Clique sur **Set up a custom domain**.
3. Renseigne `hybou.com` (et refais l'opération pour `www.hybou.com` si tu veux que les deux fonctionnent).
4. Deux cas possibles :
   - **Le domaine hybou.com est déjà géré par Cloudflare** (zone DNS Cloudflare) : la connexion se fait en un clic, automatiquement.
   - **Le domaine est enregistré/géré ailleurs** (autre registrar, DNS externe) : Cloudflare Pages t'indiquera l'enregistrement à ajouter (en général un `CNAME` pour `www` et un enregistrement pour la racine) — copie-le chez ton fournisseur de domaine actuel.
5. Attends la propagation (quelques minutes à quelques heures). Le cadenas HTTPS se met en place automatiquement.

⚠️ Si `hybou.com` sert déjà à autre chose ailleurs (email, autre site), dis-le-moi avant de brancher le domaine dessus — on pourra par exemple mettre ce site sur un sous-domaine comme `spectacle.hybou.com` sans rien casser de ton usage actuel.

---

## Étape 5 — Mettre à jour le site plus tard

Pour toute future modification (texte, coordonnées, couleurs...) :

1. Je te fournirai les fichiers modifiés (`index.html` et/ou `assets/style.css`).
2. Va sur ton dépôt GitHub (`site-hypnose`).
3. Clique sur le fichier à remplacer (ex. `index.html`), puis sur l'icône crayon (**Edit this file**) ou supprime-le et réenvoie la nouvelle version via **Add file > Upload files**.
4. Clique sur **Commit changes**.
5. Cloudflare Pages republie automatiquement le site en 1 à 2 minutes — tu n'as rien d'autre à faire.

---

## Récapitulatif

- **Code source** : GitHub (dépôt `site-hypnose`)
- **Hébergement / publication** : Cloudflare Pages, connecté automatiquement au dépôt GitHub
- **Mise à jour** : modifier les fichiers sur GitHub → republication automatique par Cloudflare

Si un écran ne correspond pas exactement à ce qui est décrit (Cloudflare fait parfois évoluer son interface), dis-le-moi et je t'aiderai à retrouver le bon bouton.
