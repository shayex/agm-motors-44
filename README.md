# AGM Motors 44 — site de l'association

Site vitrine en un seul fichier (`index.html`). Aucune installation, aucun
serveur : tout tient dans cette page.

---

## Ajouter les photos (visibles par TOUS les visiteurs)

Les photos et logos se chargent automatiquement depuis deux dossiers du dépôt :

- `photos/` → les photos du bureau
- `partenaires/` → les logos des partenaires

**Il suffit de déposer un fichier au bon nom.** Si le fichier est absent, les
initiales s'affichent à la place — le site n'est jamais cassé.

### Comment déposer une image directement sur GitHub (sans logiciel)

1. Sur la page du dépôt GitHub, ouvrez le dossier `photos` (ou `partenaires`).
   - Si le dossier n'existe pas encore : bouton **Add file → Create new file**,
     tapez `photos/thomas.jpg` dans le nom — GitHub crée le dossier tout seul —
     ou plus simple, **Add file → Upload files** puis glissez vos images.
2. Bouton **Add file → Upload files**.
3. Glissez-déposez votre image, en la renommant **exactement** comme dans les
   tableaux ci-dessous (le nom compte, majuscules/minuscules comprises).
4. Bouton vert **Commit changes**.
5. Attendez ~1 minute : la photo apparaît sur le site en ligne.

> Astuce : des images **carrées** (ex. 800×800 px) rendent le mieux pour le
> bureau. Pour les logos partenaires, un **PNG à fond transparent** est idéal.

### Noms de fichiers attendus — Le bureau (`photos/`)

| Personne     | Fichier à déposer      |
|--------------|------------------------|
| Thomas L.    | `photos/thomas.jpg`    |
| Marion B.    | `photos/marion.jpg`    |
| Kévin D.     | `photos/kevin.jpg`     |
| Sarah A.     | `photos/sarah.jpg`     |
| Julien M.    | `photos/julien.jpg`    |
| Noé R.       | `photos/noe.jpg`       |

### Noms de fichiers attendus — Partenaires (`partenaires/`)

| Partenaire            | Fichier à déposer                    |
|-----------------------|--------------------------------------|
| Garage de l'Erdre     | `partenaires/garage-erdre.png`       |
| Atlantic Performance  | `partenaires/atlantic-performance.png` |
| Carrosserie Sèvre     | `partenaires/carrosserie-sevre.png`  |
| Detailing Nantes      | `partenaires/detailing-nantes.png`   |
| Pneus Loire Ouest     | `partenaires/pneus-loire-ouest.png`  |
| Café du Circuit       | `partenaires/cafe-circuit.png`       |

> Vous ajoutez un nouveau membre ou partenaire ? Le nom de fichier attendu est
> la valeur `data-photo-id` de la carte dans `index.html`. Dites-le-moi et je
> mets la liste à jour.

---

## Changer le nom d'un membre / ajouter / retirer un membre

Tous les membres du bureau sont regroupés dans **une seule liste** au même
endroit du fichier `index.html`. Cherchez le repère :

```
▼▼▼  LES MEMBRES DU BUREAU — MODIFIEZ TOUT ICI  ▼▼▼
```

Chaque membre tient sur une ligne, entre accolades `{ }` :

```js
{ id:"thomas", nom:"Thomas L.", role:"Président", bio:"…", photo:"photos/thomas.jpg" },
```

- **Changer un nom** → modifiez le texte après `nom:`. Les initiales
  affichées à défaut de photo se recalculent toutes seules.
- **Changer le rôle / la description** → texte après `role:` ou `bio:`.
- **Associer une photo** → mettez le nom du fichier après `photo:` (le fichier
  doit être déposé dans le dossier `photos/`). Laissez `photo:""` s'il n'y a
  pas encore de photo : les initiales s'affichent.
- **Ajouter un membre** → copiez une ligne, collez-la en dessous, changez les
  valeurs. Donnez-lui un `id` unique (sans espace ni accent) et gardez la
  virgule en fin de ligne.
- **Retirer un membre** → supprimez sa ligne entière.

> Le `id` est un identifiant technique interne (il n'apparaît pas à l'écran).
> Le nom affiché, lui, est le champ `nom` — les deux sont indépendants, donc
> renommer un membre ne casse jamais sa photo.

Après modification : **Commit changes** → le site se met à jour tout seul.
(Ou envoyez-moi le changement souhaité, je m'en occupe et je fais la PR.)

---

## Changer un partenaire / ajouter / retirer un partenaire

Même principe que pour le bureau : tous les partenaires sont dans **une seule
liste**. Cherchez dans `index.html` le repère :

```
▼▼▼  LES PARTENAIRES — MODIFIEZ TOUT ICI  ▼▼▼
```

Chaque partenaire tient sur une ligne :

```js
{ id:"garage-erdre", nom:"Garage de l'Erdre", type:"Mécanique", texte:"…", logo:"partenaires/garage-erdre.png" },
```

- **Changer le nom** → champ `nom`. Il met aussi à jour **le bandeau défilant**
  des partenaires en haut de la section, et recalcule les initiales de repli.
- **Changer la catégorie / la description** → champs `type` et `texte`.
- **Associer un logo** → champ `logo` (fichier déposé dans `partenaires/`).
  Laissez `logo:""` s'il n'y en a pas encore : les initiales s'affichent.
- **Ajouter / retirer** un partenaire → ajoutez / supprimez une ligne (gardez la
  virgule en fin de ligne, et un `id` unique sans espace ni accent).

---

## Carte AGM (abonnement annuel) et ses offres

L'onglet **Carte AGM** présente l'abonnement à l'année et la liste des remises
partenaires. Tout se modifie au même endroit dans `index.html`, repère :

```
▼▼▼  LES OFFRES DE LA CARTE — MODIFIEZ TOUT ICI  ▼▼▼
```

- **Changer le prix** → la ligne juste au-dessus de la liste :
  `window.AGM_CARTE_PRIX = "20€";`
- **Un partenaire = un bloc** `{ … }` :

  ```js
  { nom:"Lustr'O Detailing", logo:"", lignes:[
    "-15% nettoyage auto intérieur et extérieur, pose de céramique",
    "À domicile"
  ]},
  ```

  - `nom` : le nom affiché.
  - `lignes` : un avantage par ligne (entre guillemets, séparés par des
    virgules). Un début de ligne en `-15%`, `-12€`… est mis en avant en couleur
    automatiquement.
  - `logo` : facultatif. Mettez `""` pour afficher les initiales, ou un chemin
    d'image (par ex. `offres/lustro.png`) après avoir déposé le fichier.
- **Ajouter / retirer** une offre → ajoutez / supprimez un bloc `{ … }` (gardez
  les virgules entre les blocs).

---

## Le site est-il bien publié ? (GitHub Pages)

Pour que le lien public affiche le site (et pas le code source), **GitHub Pages**
doit être activé :

1. Dépôt GitHub → onglet **Settings** → menu **Pages**.
2. Section *Build and deployment* → **Source : Deploy from a branch**.
3. **Branch : `main`**, dossier **`/ (root)`** → **Save**.
4. Après une minute, l'adresse publique s'affiche en haut de cette même page
   (de la forme `https://shayex.github.io/agm-motors-44/`).

Une fois Pages activé, chaque photo déposée dans `photos/` ou `partenaires/`
devient visible par tous les visiteurs, automatiquement.
