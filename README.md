# Statistiques commerciales

Tableau de bord des actions commerciales **par agence et par commercial**, construit à partir des exports Excel (tableau croisé : *Type d'action → Agence → Commercial → Candidat/Client → Cible → année*).

👉 **Utiliser l'outil : https://alastorzaul.github.io/dominorh/**

## Comment ça marche

1. Ouvrir le lien ci-dessus avec **Microsoft Edge** ou **Google Chrome**.
2. Cliquer sur **« Choisir le dossier des exports »** et sélectionner le dossier où sont enregistrés les exports Excel, puis autoriser l'accès.
3. C'est tout : dès qu'un export est **ajouté, modifié ou supprimé** dans ce dossier (sous-dossiers compris), les statistiques se mettent à jour toutes seules en ~2 secondes.

### Semaines

Chaque export correspond à **une semaine**. La semaine est lue dans le **nom du fichier** :

| Nom du fichier | Semaine |
|---|---|
| `Export PAU S42.xlsx`, `Export 2026-S42.xlsx`, `pau_semaine_42.xlsx`, `Export W42.xlsx` | S42 |
| `Export DAX 2026-10-12.xlsx`, `export_20261012.xlsx`, `Export 12-10-2026.xlsx` | semaine contenant cette date (S42) |

Si le nom ne contient ni semaine ni date, la semaine est déduite de la **date d'enregistrement du fichier** (affichée avec un « ? » dans la liste des fichiers) : renommer le fichier pour la fixer.

Un filtre **Semaine** et un graphique **Évolution par semaine** (cliquable) permettent de suivre l'activité semaine par semaine. Si deux fichiers de la **même semaine** contiennent la même ligne (export refait), elle n'est comptée qu'une fois.

À la réouverture, le dossier est mémorisé ; selon le navigateur, un clic sur **« Reprendre la surveillance »** peut être demandé.

> Firefox ne permet pas la surveillance d'un dossier : il peut lire les exports, mais il faut cliquer sur « Actualiser » après chaque nouvel export.

## Confidentialité

- **Les exports ne quittent jamais le poste.** Ils sont lus directement par le navigateur ; GitHub ne sert que la page, vide de toute donnée.
- La page interdit au navigateur toute connexion réseau (`Content-Security-Policy: connect-src 'none'`) : même par erreur, aucune donnée ne peut être envoyée.
- Le dépôt **ne doit contenir aucun export** : le `.gitignore` bloque les fichiers `.xlsx`, `.xls`, `.xlsm` et `.csv`.

## Fonctionnalités

- Chiffres clés : actions totales, candidats / clients, cibles distinctes, commerciaux actifs
- Fiche par agence (cliquer pour filtrer)
- Actions par commercial et par type d'action, avec détail par commercial (cibles suivies et actions menées)
- Tableau triable par commercial, matrice commercial × type d'action, cibles les plus travaillées
- **Export en présentation PowerPoint (.pptx)** de la vue filtrée : page de titre, chiffres clés, agences, évolution par semaine, commerciaux, types d'action, puis une fiche par commercial — graphiques PowerPoint natifs, modifiables. Généré dans le navigateur, rien n'est envoyé.
- Données détaillées avec recherche, tri et pagination ; export CSV de la vue filtrée
- Filtres : agence, commercial, type de cible, type d'action, semaine, année
- Évolution par semaine (graphique cliquable)
- Gestion des exports refaits : une même ligne présente dans plusieurs fichiers de la même semaine est comptée une seule fois (fichier le plus récent), ou additionnée au choix
- Thème clair / sombre, affichage mobile

## Utilisation hors ligne

Télécharger le dépôt (**Code → Download ZIP**), le dézipper et ouvrir `index.html` avec Edge ou Chrome. Garder le dossier `vendor/` à côté.

## Structure

```
index.html                  l'application (HTML + CSS + JS, sans build)
export-pptx.js              génération de la présentation PowerPoint
vendor/xlsx.full.min.js     SheetJS Community Edition 0.18.5 (lecture des fichiers Excel, licence Apache-2.0)
vendor/pptxgen.bundle.js    PptxGenJS 3.12.0 (création du .pptx, licence MIT)
```

## Publication (GitHub Pages)

*Settings → Pages → Build and deployment* : **Source = Deploy from a branch**, **Branch = `main` / `(root)`**.
