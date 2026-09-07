# Dossier `galerie/` — photos des évènements

Déposez ici les **photos** qui s'affichent dans la galerie du site
(section « Galerie », bouton « 📸 Voir la galerie photos »).

- Format conseillé : `.jpg`, en paysage de préférence (les vignettes sont
  recadrées automatiquement, la photo entière s'affiche à l'agrandissement).
- Pour un chargement rapide, évitez les fichiers trop lourds (viser < 500 Ko).

### Comment ajouter une photo à la galerie

1. Déposez le fichier ici (bouton **Add file → Upload files** sur GitHub).
2. Dans `index.html`, cherchez le repère
   « ▼▼▼ LA GALERIE PHOTOS — MODIFIEZ TOUT ICI ▼▼▼ ».
3. Ajoutez une ligne dans la liste `window.AGM_GALERIE`, par exemple :

   ```js
   { src:"galerie/rasso-juillet-01.jpg", legende:"AGM Motors — Domaine des Lys, Ancenis (juillet 2026)" },
   ```

   - `src` : le nom du fichier déposé ici (chemin `galerie/…`).
   - `legende` : facultatif, le texte affiché sous la photo agrandie.
4. **Commit changes** → la photo apparaît dans la galerie après ~1 minute.

Tant que la liste est vide, un message « Les photos arrivent bientôt »
s'affiche : le site n'est jamais cassé.

> Ce fichier `README.md` sert juste à faire exister le dossier. Il n'apparaît
> pas sur le site.
