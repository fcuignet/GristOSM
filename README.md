# gristopenstreetmap

Widget de cartographie Grist basé sur OpenStreetMap + Leaflet.

Ce projet reprend l'idée du widget/vue carte de Grist, mais utilise :
- **OpenStreetMap** pour le fond de carte,
- **Leaflet** pour le moteur cartographique,
- et permet d'afficher plusieurs points avec un libellé.

## Fichier principal

- `widgetpersoOSM.html` : widget autonome (HTML + CSS + JS).



## Utilisation dans Grist

1. Ajouter un widget personnalisé.
2. Pointer vers l'URL publique de `widgetpersoOSM.html`.
3. Mapper les colonnes :
   - `Latitude` (numérique)
   - `Longitude` (numérique)
   - `Label` (texte, optionnel)
   - `MarkerSize` (numérique, optionnel) : valeur pour agrandir/réduire le marqueur
   - `MarkerSizeCap` (numérique, optionnel) : plafond max pour la valeur de taille

Si `MarkerSize` est absent, le marqueur garde une taille standard.
Si `MarkerSize` est présent, la taille est mise à l'échelle jusqu'au plafond (`MarkerSizeCap`),
ou jusqu'au maximum observé si le plafond n'est pas fourni.

## Licence

Ce projet est distribué sous **GNU GPL v3** (voir `LICENSE`).
