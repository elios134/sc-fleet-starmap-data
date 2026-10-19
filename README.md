# sc-fleet-starmap-data

Données de la carte stellaire 3D de **SC Fleet Manager** (V3), servies au runtime via
jsDelivr (`https://cdn.jsdelivr.net/gh/elios134/sc-fleet-starmap-data@main/...`).

## Contenu

- **`starmap-geo.json`** — géométrie des corps (orbites, rayon, rotation, couleur) + POI de
  surface (lon/lat), consommé par la commande Rust `starmap_geometry` (cache hors-ligne).
- **`planets/<clé>.webp`** — textures équirectangulaires par corps (clé = nom normalisé :
  minuscules, sans accents ni ponctuation, p. ex. `microtech.webp`). Chargées en direct par
  `THREE.TextureLoader` (jsDelivr sert avec CORS). Extraites de la carte du jeu
  (`Data/UI/starmap/textures/*` du `Data.p4k`, 2048×1024, WebP) : Stanton, Pyro, Nyx.
  Pyro V n'a pas de texture propre en jeu : l'app garde son rendu procédural.
- **`source-csv/`** — CSV sources VerseTime (provenance + régénération).

## Régénérer `starmap-geo.json`

```bash
node scripts/build-starmap-geo.mjs <dossier-csv-versetime> starmap-geo.json
```
(le script vit dans le dépôt applicatif `sc-fleet-manager-v2`).

## Attribution & licences

- **Géométrie + POI** dérivés des fichiers de données de **VerseTime** (© dydrmr,
  <https://github.com/dydrmr/VerseTime>, code sous GPL-3.0), eux-mêmes collationnés par le
  **Murphy Exploration Group**. Données factuelles de jeu réutilisées avec attribution.
- **Textures** : les textures équirectangulaires de planètes sont dérivées d'assets de
  **Star Citizen** (© Cloud Imperium Games). Projet **fan non affilié** à CIG ; usage toléré
  pour les outils communautaires, pas une licence formelle.
