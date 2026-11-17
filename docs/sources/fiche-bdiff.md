# Fiche d'identité - BDIFF (Base de Données sur les Incendies de Forêt en France)

Rédigée par : Rim Zougarh, 2026-11-17
Fichier analysé : `Incendies.csv`, export du portail BDIFF du 17/11/2026 (Nouvelle-Aquitaine, feux de forêt, 01/01/2016 → 31/12/2025)

## Identité

| Rubrique | Contenu |
|---|---|
| Propriétaire | IGN (Institut national de l'information géographique et forestière), pour le ministère de l'Agriculture et de la Souveraineté alimentaire |
| Accès | Portail https://bdiff.agriculture.gouv.fr → Consultation des incendies → filtres → « Télécharger CSV ». Fiche catalogue sur data.gouv.fr (le « fichier » y est seulement un lien vers le portail). Téléchargement libre, sans compte |
| Format | ZIP contenant un CSV (séparateur `;`, encodage UTF-8) + 2 PDF (Définitions, Mentions légales). Attention : 3 lignes d'informations avant la ligne des titres de colonnes |
| Contenu | Un enregistrement par incendie de forêt : date d'alerte, commune, surfaces brûlées par type de végétation, cause, dégâts |
| Granularité | Une ligne = un incendie, localisé à la commune (pas de coordonnées GPS) |
| Historique | Depuis 2006 pour toute la France (export fait ici sur 2016-2025) |
| Fraîcheur | Dernier feu du fichier : 28/12/2025. Le portail diffuse les données jusqu'à l'année précédant l'année en cours : **la saison 2026 n'est pas disponible** (dont le feu de Saumos de juillet 2026) |
| Clés | `Code INSEE` (commune) et `Département` pour croiser avec d'autres sources ; `Date de première alerte` pour croiser avec la Météo des forêts. Identifiant d'un feu : `Année` + `Numéro` + `Département` (le `Numéro` seul n'est pas unique) |
| Licence | Licence Ouverte / Open Licence 2.0 (indiquée sur data.gouv.fr). Les mentions légales demandent de citer bdiff.agriculture.gouv.fr comme source |
| Millésime | Export du 17/11/2026. Les fiches ont changé de format en 2023 (nouvelles catégories de surfaces) |
| Données personnelles | Pas de nom ni d'adresse. Mais les colonnes décès et bâtiments détruits, croisées avec la commune et la date, peuvent permettre de retrouver une personne ou un bien dans une petite commune : à vérifier avec le responsable conformité |

## Chiffres clés de l'export

- 4 003 incendies, 24 colonnes
- 12 départements de Nouvelle-Aquitaine, dont la Gironde (33) : 1 380 feux, le département le plus touché
- Plus grand feu : Landiras (33), 12/07/2022, 12 552 ha
- 2024 : seulement 98 feux, contre 250 à 650 les autres années (à vérifier : année humide ou données incomplètes ?)

## Schéma

| Colonne | Type | Description | Exemple | Remplissage |
|---|---|---|---|---|
| Année | entier | Année de l'incendie | 2016 | 100 % |
| Numéro | entier | Numéro de la fiche (unique seulement avec Année + Département) | 362 | 100 % |
| Département | texte | Code du département | 33 | 100 % |
| Code INSEE | texte | Code INSEE de la commune (texte pour garder le 0 du début) | 23144 | 100 % |
| Nom de la commune | texte | Commune où le feu est déclaré | La Nouaille | 100 % |
| Date de première alerte | date et heure | Moment où l'alerte arrive au CODIS | 2016-01-26 14:42:00 | 100 % |
| Surface parcourue (m2) | entier | Surface totale brûlée, en **m²** (pas en hectares) | 20000 | 100 % |
| Surface forêt (m2) | entier | Partie brûlée en forêt | 0 | 100 % |
| Surface maquis garrigues (m2) | entier | Uniquement pour la zone méditerranéenne | — | 0 % |
| Autres surfaces naturelles hors forêt (m2) | entier | Landes, prairies naturelles, zones humides | 20000 | 96 % |
| Surfaces agricoles (m2) | entier | Format depuis 2023 | 0 | 26 % |
| Autres surfaces (m2) | entier | Format depuis 2023 (friches, jardins…) | 0 | 26 % |
| Surface autres terres boisées (m2) | entier | Format avant 2023 | 20000 | 71 % |
| Surfaces non boisées naturelles (m2) | entier | Format avant 2023 | 0 | 19 % |
| Surfaces non boisées artificialisées (m2) | entier | Format avant 2023 | 0 | 19 % |
| Surfaces non boisées (m2) | entier | Format avant 2023 | 0 | 69 % |
| Précision des surfaces | texte | Estimées ou Mesurées | Estimées | 59 % |
| Type de peuplement | texte | Uniquement pour la zone méditerranéenne | — | 0 % |
| Nature | texte | Cause : Naturelle, Accidentelle, Involontaire (particulier), Involontaire (travaux), Malveillance | Malveillance | 38 % |
| Décès ou bâtiments touchés | texte | Oui / Non | Non | 44 % |
| Nombre de décès | entier | Nombre de morts | 0 | 17 % |
| Nombre de bâtiments totalement détruits | entier | Bâtiments détruits | 0 | 17 % |
| Nombre de bâtiments partiellement détruits | entier | Bâtiments abîmés | 0 | 17 % |
| Précision de la donnée | texte | Avertissement sur la fiche | Données partielles ou non valides | 0,3 % |

## Limites repérées

- **La cause est vide pour 62 % des feux** : la question 4 (points communs des feux avec indice bas) ne pourra s'appuyer que sur un tiers des feux.
- **Changement de format en 2023** : les colonnes de surface par type de végétation ne sont pas les mêmes avant et après 2023. Seules `Surface parcourue` et `Surface forêt` sont comparables sur toute la période.
- **Surfaces en m²** dans le CSV, alors que le site les affiche en hectares : il faudra convertir (÷ 10 000).
- **Pas de 2026** : la saison la plus récente, celle que la direction a en tête, manque.
- **Localisation à la commune seulement** : impossible de savoir où exactement dans la commune le feu est parti.
- **2024 très bas** : à vérifier avant de l'utiliser.

## Questions servies

| Question | Ce que la BDIFF apporte |
|---|---|
| 1. Zones les plus touchées | Oui : feux par commune et par département |
| 2, 5, 6. Seuil de l'indice | En partie : donne les feux par jour, à croiser avec la Météo des forêts (2023-2025 seulement) |
| 3. Comparaison avec les autres départements | En partie : export à refaire pour la France entière |
| 4. Feux avec indice bas | En partie : la cause n'est remplie que pour 38 % des feux |
| 7. Critères météo suffisants | En partie : donne les feux, la météo doit venir d'une autre source |