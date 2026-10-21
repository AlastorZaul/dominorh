# Statistiques commerciales

Tableau de bord des actions commerciales **par agence et par commercial**, construit à partir des exports Excel (tableau croisé : *Type d'action → Agence → Commercial → Candidat/Client → Cible → année*).

👉 **Utiliser l'outil : https://alastorzaul.github.io/dominorh/**

## Comment ça marche

1. Ouvrir le lien ci-dessus avec **Microsoft Edge** ou **Google Chrome**.
2. Cliquer sur **« Choisir le dossier des exports »** et sélectionner le dossier où sont enregistrés les exports Excel, puis autoriser l'accès.
3. C'est tout : dès qu'un export est **ajouté, modifié ou supprimé** dans ce dossier (sous-dossiers compris), les statistiques se mettent à jour toutes seules en ~2 secondes.

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
- Données détaillées avec recherche, tri et pagination ; export CSV de la vue filtrée
- Filtres : agence, commercial, type de cible, type d'action, année
- Gestion des exports qui se recouvrent : une même ligne présente dans plusieurs fichiers est comptée une seule fois (fichier le plus récent), ou additionnée au choix
- Thème clair / sombre, affichage mobile

## Utilisation hors ligne

Télécharger le dépôt (**Code → Download ZIP**), le dézipper et ouvrir `index.html` avec Edge ou Chrome. Garder le dossier `vendor/` à côté.

## Structure

```
index.html                  l'application (HTML + CSS + JS, sans build)
vendor/xlsx.full.min.js     SheetJS Community Edition 0.18.5 (lecture des fichiers Excel, licence Apache-2.0)
```

## Publication (GitHub Pages)

*Settings → Pages → Build and deployment* : **Source = Deploy from a branch**, **Branch = `main` / `(root)`**.
