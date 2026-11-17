# Fiche d'identité - BD Forêt® V2 (IGN)

Rédigée par : Melissa Benbouabdellah, 2026-11-17
Données analysées : couche `LANDCOVER.FORESTINVENTORY.V2:formation_vegetale`, interrogée le 17/11/2026 sur le service WFS de l'IGN (Géoplateforme), puis filtrée sur le contour officiel de la Gironde (ADMIN EXPRESS COG CARTO, département 33)

## Identité

| Rubrique | Contenu |
|---|---|
| Propriétaire | IGN (Institut national de l'information géographique et forestière) |
| Accès | Fiche catalogue sur data.gouv.fr (`bd-foret-r`), qui renvoie vers geoservices.ign.fr/bdforet. Deux façons de récupérer les données : téléchargement d'archives par département (shapefile), ou service WFS `https://data.geopf.fr/wfs/ows` (couche `LANDCOVER.FORESTINVENTORY.V2:formation_vegetale`). Libre, sans compte |
| Format | Données géographiques (polygones). Shapefile en téléchargement, GeoJSON possible par le WFS |
| Contenu | La carte des forêts et des landes : chaque zone boisée de plus de 0,5 ha est un polygone, avec son type de formation végétale (forêt fermée ou ouverte, conifères, feuillus, mixte, lande…) et son essence dominante (pin maritime, chênes…) |
| Granularité | Une ligne = une zone de végétation homogène (un polygone), d'au moins 5 000 m² |
| Historique | Une seule photo de la forêt, pas de série dans le temps. La V2 a été produite entre 2007 et 2018 selon les départements. La V1, plus ancienne et moins précise, n'est plus comparable (nomenclature différente par département) |
| Fraîcheur | **Millésime de la Gironde non vérifié** : l'IGN publie une carte des millésimes par département, à consulter. Dans tous les cas, la carte est **antérieure aux grands feux de 2022 (Landiras, La Teste) et de 2026 (Saumos)** : les zones brûlées y apparaissent encore comme de la forêt. La date « mise à jour 16/11/2026 » de data.gouv.fr concerne la fiche catalogue, pas les données |
| Clés | `id` (identifiant unique du polygone). **Aucun code commune ni code département** : pour croiser avec la BDIFF (qui est à la commune), il faut une **jointure spatiale** avec les contours des communes (ADMIN EXPRESS) |
| Licence | Licence Ouverte / Open Licence 2.0 (indiquée sur data.gouv.fr) |
| Millésime | Version 2 de la BD Forêt. Année de prise de vue de la Gironde : non vérifiée (voir Fraîcheur) |
| Données personnelles | Aucune : pas de propriétaire, pas d'adresse, pas de parcelle cadastrale. Seulement de la végétation |

## Chiffres clés (Gironde)

- **53 151 polygones** en Gironde, 5 colonnes plus la géométrie
- **549 770 ha** de forêts et landes cartographiés, soit **environ 54 % de la surface du département** (1 008 819 ha)
- **Pin maritime : 222 202 ha, 40 % de la surface cartographiée.** C'est l'essence qui domine nettement, celle du massif des Landes de Gascogne
- **Forêt fermée sans couvert arboré : 122 816 ha (22 %)**. Ce sont des zones boisées sans arbres au moment de la photo (coupes rases, zones dévastées par une tempête ou un feu). Leur essence est notée « NR » (non renseignée)
- Feuillus (tous types) : environ 129 000 ha. Landes : 20 965 ha

| Type de formation (`tfv_g11`) | Surface (ha) | Part |
|---|---|---|
| Forêt fermée conifères | 223 353 | 40,6 % |
| Forêt fermée feuillus | 123 078 | 22,4 % |
| Forêt fermée sans couvert arboré | 122 816 | 22,3 % |
| Forêt fermée mixte | 41 456 | 7,5 % |
| Lande | 20 965 | 3,8 % |
| Forêts ouvertes, peupleraies, formations herbacées | 18 101 | 3,3 % |

## Schéma

| Colonne | Type | Description | Exemple | Remplissage |
|---|---|---|---|---|
| id | texte | Identifiant unique du polygone | FORESTIE0000000003301993 | 100 % (53 151 distincts) |
| code_tfv | texte | Code du type de formation végétale (nomenclature nationale) | FF2-51-51 | 100 % (28 valeurs) |
| tfv | texte | Libellé détaillé du type de formation végétale | Forêt fermée de pin maritime pur | 100 % (29 valeurs, voir limites) |
| tfv_g11 | texte | Regroupement en 11 grandes classes | Forêt fermée conifères | 100 % (11 valeurs) |
| essence | texte | Essence dominante | Pin maritime | 100 % (17 valeurs), mais « NR » ou « NC » sur 26 % de la surface |
| geom | polygone | Contour de la zone (Lambert 93 en téléchargement) | — | 100 % |

Remarque : il n'y a **pas de colonne surface**. Les surfaces de cette fiche ont été calculées à partir des contours (projection Lambert 93).

## Limites repérées

- **Carte figée et antérieure aux grands feux** : les forêts brûlées en 2022 et 2026 apparaissent encore boisées. Pour savoir « où concentrer les moyens », on risque de compter comme forêt à protéger des zones déjà brûlées.
- **Millésime de la Gironde à vérifier** avant toute utilisation.
- **Pas de lien direct avec les communes** : la jointure avec la BDIFF demande un calcul géographique (intersection des polygones avec les communes), donc un outil SIG dans le pipeline (PostGIS, GeoPandas…). C'est un vrai coût technique.
- **Essence inconnue sur 26 % de la surface** (« NR » 22 %, « NC » 4 %), surtout les zones sans arbres.
- **Problème d'encodage** : le libellé `FF1-49-49` existe en deux écritures (apostrophe mal codée `\x92` dans 533 lignes, correcte dans 6). Un regroupement sur `tfv` donnerait deux catégories au lieu d'une : il faut regrouper sur `code_tfv`.
- **143 polygones font moins de 5 000 m²**, alors que la documentation annonce ce minimum (morceaux coupés en bordure, à vérifier).
- **Ce n'est pas une carte du risque** : la BD Forêt dit quelle végétation il y a, pas si elle est sèche, entretenue ou proche des habitations.

## Questions servies

Numéros de la synthèse du groupe (`Synthese Analyse de la commande Groupe.md`).

| Question | Ce que la BD Forêt apporte |
|---|---|
| 4. Communes ou zones où les feux démarrent le plus | En partie : permet de rapporter le nombre de feux à la **surface de forêt** de chaque commune (un taux de feux par hectare boisé est plus juste qu'un simple nombre de feux) |
| 30. Types d'arbres dans chaque massif | Oui : essence dominante et type de formation, polygone par polygone |
| 31. Taille de chaque massif | Oui, après calcul des surfaces. Mais la notion de « massif » n'existe pas dans la base : il faut regrouper les polygones (définition à décider) |
| 21. Comparaison avec les autres départements | En partie : la même base existe pour toute la France métropolitaine, ce qui permet de comparer à surface de forêt égale |
| 18. Points communs des feux à indice bas | En partie : le type de végétation de la commune du feu peut être un de ces points communs |

## Verdict proposé

**À retenir comme source secondaire.** La BD Forêt ne répond pas seule à une décision, mais elle **corrige** les chiffres de la BDIFF : sans elle, une commune très boisée paraît plus dangereuse qu'une autre simplement parce qu'elle a plus de forêt. Elle reste à manier avec prudence à cause de son ancienneté et du coût de la jointure spatiale.
