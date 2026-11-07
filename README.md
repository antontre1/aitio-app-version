# aitio-app-version

Sert `https://api.aitio.fr/` : la dernière version publiée de l'app mobile Aitio actuelle (Expo / React Native).

```json
{"iosVersion":"1.4.1","androidVersion":"1.4.1"}
```

## Fonctionnement

Au démarrage, l'app lit ce JSON (`fetch('https://api.aitio.fr/')`, puis `response.json()`). Si la version du serveur est
**supérieure** à la version installée, elle affiche « Mise à jour disponible ». Toute erreur est ignorée : sans ce service,
l'app fonctionne, simplement sans invite.

**La comparaison se fait sur des chaînes de caractères** (`"1.4.10" < "1.4.9"`). Garder des numéros comparables,
par exemple `2.0.0` pour pousser la future app native.

## Mettre à jour

Modifier `index.html` (c'est du JSON, le nom de fichier sert seulement à GitHub Pages), puis fusionner sur `main`.
GitHub Pages republie en une à deux minutes. Vérifier ensuite :

```bash
curl -s https://api.aitio.fr/
```

## Hébergement

- GitHub Pages, branche `main`, racine du dépôt ; domaine personnalisé `api.aitio.fr` (fichier `CNAME`), HTTPS forcé.
- DNS (zone `aitio.fr` chez OVH) : `api` en CNAME vers `antontre1.github.io.` ; domaine vérifié dans GitHub
  (enregistrement TXT `_github-pages-challenge-antontre1`) pour empêcher qu'un autre compte le réclame.
- Remplace l'ancien `index.php` sur l'hébergement mutualisé OVH `cluster024` (novembre 2026).

Ce dépôt est **public** : n'y mettre aucun secret, aucun jeton, aucune donnée utilisateur.
