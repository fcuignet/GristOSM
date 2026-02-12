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
   - `Label`, `Label2`, `Label3`, `Label4` (texte, optionnel) : jusqu'à 4 étiquettes affichables
   - `MarkerSize` (numérique, optionnel) : valeur pour agrandir/réduire le marqueur
   - `MarkerSizeCap` (numérique, optionnel) : plafond max pour la valeur de taille
   - `ColorBy` (optionnel) : colonne de type choix simple, choix multiple ou booléen pour la couleur

Si `MarkerSize` est absent, le marqueur garde une taille standard.
Si `MarkerSize` est présent, la taille est mise à l'échelle jusqu'au plafond (`MarkerSizeCap`),
ou jusqu'au maximum observé si le plafond n'est pas fourni.

Si `ColorBy` est renseigné, la couleur du marqueur change selon la valeur :
- booléen `true`/`false` : couleurs dédiées,
- choix simple ou multiple : couleur déterministe par valeur.

Une légende de colorisation apparaît automatiquement sous la carte avec les catégories présentes.

## Licence

Ce projet est distribué sous **GNU GPL v3** (voir `LICENSE`).
