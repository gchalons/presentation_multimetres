# C4_R1 — Animation Flash sur le web

Ce dossier permet de lire `C4_R1.swf` directement dans un navigateur, via
[Ruffle](https://ruffle.rs), un émulateur Flash Player open-source
(WebAssembly). Aucune installation de Flash Player n'est nécessaire — Flash
étant définitivement mort depuis fin 2020.

## Structure

```
.
├── index.html          # Page qui charge et affiche l'animation
├── media/
│   └── C4_R1.swf        # Ton animation Flash d'origine
└── ruffle/               # Émulateur Ruffle (JS + WebAssembly), inclus localement
```

## Utiliser en local

Comme les navigateurs bloquent le chargement de fichiers locaux (WASM/`fetch`)
via `file://`, lance un petit serveur local :

```bash
python3 -m http.server 8000
```

puis ouvre http://localhost:8000 dans ton navigateur.

## Déployer sur GitHub Pages

1. Crée un nouveau dépôt GitHub (ou utilise un dépôt existant).
2. Copie tout le contenu de ce dossier à la racine du dépôt (ou dans un
   sous-dossier `/docs` si tu préfères).
3. Pousse sur GitHub :
   ```bash
   git init
   git add .
   git commit -m "Ajout animation C4_R1 avec lecteur Ruffle"
   git branch -M main
   git remote add origin https://github.com/<ton-utilisateur>/<ton-repo>.git
   git push -u origin main
   ```
4. Dans les paramètres du dépôt → **Pages**, choisis la branche `main`
   (dossier `/` ou `/docs` selon ton choix) comme source.
5. Ton animation sera accessible à
   `https://<ton-utilisateur>.github.io/<ton-repo>/`.

## Remarques

- Le dossier `ruffle/` contient l'émulateur en local (pas de CDN externe),
  donc tout fonctionne même hors-ligne une fois servi par un serveur web.
- Si l'animation utilise ActionScript avancé, des interactions complexes ou
  des composants Flash très spécifiques, un rendu partiel est possible :
  Ruffle couvre la grande majorité de l'ActionScript 2/3 mais n'est pas
  garanti 100% compatible.
- Licence de Ruffle : MIT / Apache-2.0 (fichiers inclus dans `ruffle/`).
