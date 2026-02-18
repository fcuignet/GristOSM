# gristopenstreetmap

Widget de cartographie Grist basé sur OpenStreetMap + Leaflet.

Ce projet reprend l'idée du widget/vue carte de Grist, mais utilise :
- **OpenStreetMap** pour le fond de carte,
- **Leaflet** pour le moteur cartographique,
- et permet d'afficher plusieurs points avec un libellé.

## Fichier principal

- `widgetpersoOSM.html` : widget autonome (HTML + CSS + JS).

## Publier le fichier HTML via GitHub (sans stockage local)

Si tu n'utilises pas de stockage local, tu peux tout faire directement depuis l'interface web GitHub.

### Étapes (100% navigateur)
1. Créer un dépôt GitHub public (ex: `gristopenstreetmap`).
2. Dans le dépôt, cliquer **Add file** → **Upload files**.
3. Déposer `widgetpersoOSM.html` (et éventuellement `README.md`, `LICENSE`).
4. Valider avec **Commit changes**.
5. Ouvrir **Settings** → **Pages**.
6. Dans **Build and deployment** :
   - **Source** = *Deploy from a branch*
   - **Branch** = `main` (root)
   - **Save**
7. Attendre l'URL GitHub Pages (format `https://<user>.github.io/<repo>/`).
8. Utiliser dans Grist l'URL directe du fichier :
   - `https://<user>.github.io/<repo>/widgetpersoOSM.html`

> Important : l'URL du widget doit être publique en HTTPS, servir directement le HTML, et ne pas demander d'authentification.

## Utilisation dans Grist

1. Ajouter un widget personnalisé.
2. Pointer vers l'URL publique de `widgetpersoOSM.html`.
3. Mapper les colonnes :
   - `Latitude` (numérique)
   - `Longitude` (numérique)
   - `Label` (texte, obligatoire) : nom principal
   - `Label2`, `Label3`, `Label4` (optionnel, tout type : texte / entier / choix / numérique / booléen)
   - `Layer` (optionnel) : nom du calque de points (ex: "Clients", "Prospects", "Fournisseurs")
   - `BoundaryUrl` (optionnel) : URL d'un contour en `.json`, `.geojson`, `.shp` ou `.zip`
   - `BoundaryLayerName` (optionnel) : nom du calque de contours
   - `MarkerSize` (numérique, optionnel) : valeur pour agrandir/réduire le marqueur
   - `MarkerSizeCap` (numérique, optionnel) : plafond max pour la valeur de taille
   - `ColorBy` (optionnel, tout type) : texte / entier / choix simple / choix multiple / numérique / booléen pour la couleur
   - `ColorPalette` (optionnel) : `default`, `pastel`, `vivid`, `earth`, `grayscale` ou une liste hex (`#2a7fff,#ff7f2a,#14a085`)

Si `MarkerSize` est absent, le marqueur garde une taille standard.
Si `MarkerSize` est présent, la taille est mise à l'échelle jusqu'au plafond (`MarkerSizeCap`),
ou jusqu'au maximum observé si le plafond n'est pas fourni.

Si `ColorBy` est renseigné, la couleur du marqueur change selon la valeur :
- booléen `true`/`false` : couleurs dédiées,
- choix simple ou multiple : couleur déterministe par valeur.

Une légende de colorisation apparaît automatiquement sous la carte avec les catégories présentes.

Une palette personnalisée peut être choisie globalement via `ColorPalette`.

Le contrôle Leaflet permet aussi de basculer entre plusieurs fonds de carte et d'afficher/masquer les calques de points par valeur de `Layer`.

Si `BoundaryUrl` est renseigné, un calque de contours est chargé et superposé (ex: communes/départements).

## Licence

Ce projet est distribué sous **GNU GPL v3** (voir `LICENSE`).

## Fork pour gérer plusieurs calques

Oui, tu peux forker ce dépôt puis continuer à l'adapter.
Ce fork inclut maintenant un mode multi-calques via la colonne `Layer` pour grouper les points dans des calques séparés, et un calque de contours via `BoundaryUrl`.
