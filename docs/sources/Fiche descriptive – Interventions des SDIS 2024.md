# Fiche descriptive – Interventions des SDIS 2024

Nov 17, 2026 · @mec

Le fichier compte les interventions de chaque service d'incendie et de secours en 2024 (71 colonnes). Il donne le nombre de feux de végétations par département et par an, mais ni la date, ni le lieu, ni la cause d'un feu.

## 1. Fiche d'identité

| Champ | Ce qu'on sait |
| --- | --- |
| Nom | Interventions réalisées par les services d'incendie et de secours (fichier interventions2024.csv) |
| Propriétaire | Ministère de l'Intérieur, direction générale de la Sécurité civile et de la gestion des crises (DGSCGC) |
| Comment la donnée est collectée | Les services la déclarent eux-mêmes, via le site infosdis.interieur.gouv.fr (édition 2025, sur l'année 2024) |
| Accès | Téléchargement du fichier CSV sur data.gouv.fr. Lien exact à confirmer en ouvrant la page du jeu de données |
| Contenu | Le nombre d'interventions de 2024, par type : incendies, secours à personne, accidents de circulation, risques technologiques, opérations diverses |
| Grain (une ligne = ?) | Un service d'incendie et de secours pour l'année 2024 (un par département, plus la brigade de Paris et le bataillon de Marseille) |
| Historique | Ce fichier ne contient que 2024. Les années 2017 à 2024 existent dans d'autres fichiers |
| Fraîcheur | Année 2024, publiée en 2025. Mise à jour une fois par an. Date exacte de dernière mise à jour : à vérifier, la page ne l'indique pas |
| Clés | Numéro (code du département) et Département |
| Licence | Non vérifiée. À lire sur la page data.gouv.fr du jeu de données (la page du défi ne s'ouvre pas sans JavaScript) |
| Millésime | Données 2024. Référentiel géographique : départements, sans code commune ni code massif |
| Données personnelles | Non, ce sont uniquement des totaux par service |
| Format | CSV, séparateur « ; », encodage Windows-1252, 99 lignes × 71 colonnes, 30 Ko |

## 2. Colonnes retenues

On passe de 71 colonnes à 16 colonnes. Le fichier d'origine n'est pas modifié : on travaille sur une copie.

### Les lignes : le Sud-ouest

On garde les 12 services de la zone « Sud-ouest ». Dans ce fichier, elle correspond exactement aux 12 départements de la Nouvelle-Aquitaine : Charente, Charente-Maritime, Corrèze, Creuse, Dordogne, Gironde, Landes, Lot-et-Garonne, Pyrénées-Atlantiques, Deux-Sèvres, Vienne et Haute-Vienne. On y trouve la Gironde et ses voisins pour la comparer. Les 87 autres lignes (autres zones, Paris, Marseille) sont hors sujet.

### Les colonnes

On garde tous les feux, même ceux qui ne sont pas en forêt : on fera le tri plus fin plus tard. Les colonnes de feux sont des entiers (un nombre d'interventions en 2024). N° = place de la colonne dans le fichier d'origine.

| N° | Colonne | Type | Valeurs sur les 12 lignes | Gironde | Zéros sur 12 |
| --- | --- | --- | --- | --- | --- |
| 1 | Année | Entier | 2024 | 2024 |  |
| 4 | Numéro | Texte | 16 à 87 | 33 |  |
| 5 | Département | Texte | 12 noms | Gironde |  |
| 6 | Catégorie A | Texte | A (1 service), B (5), C (6) | A |  |
| 7 | Feux d'habitations-bureaux | Entier | 248 à 1 320 | 1 320 | 0 |
| 8 | dont feux de cheminées | Entier | 0 à 365 | 0 | 1 |
| 9 | Feux d'ERP avec local à sommeil | Entier | 0 à 181 | 181 | 1 |
| 10 | Feux d'ERP sans local à sommeil | Entier | 0 à 37 | 0 | 2 |
| 11 | Feux de locaux industriels | Entier | 2 à 308 | 308 | 0 |
| 12 | Feux de locaux artisanaux | Entier | 0 à 20 | 0 | 6 |
| 13 | Feux de locaux agricoles | Entier | 0 à 30 | 0 | 1 |
| 14 | Feux sur voie publique | Entier | 74 à 1 132 | 1 132 | 0 |
| 15 | Feux de véhicules | Entier | 106 à 1 159 | 1 159 | 0 |
| 16 | Feux de végétations | Entier | 79 à 180 | 175 | 0 |
| 17 | Autres feux | Entier | 98 à 1 178 | 1 178 | 0 |
| 18 | Incendies | Entier | 653 à 5 453 | 5 453 | 0 |

La colonne 8 est déjà comprise dans la colonne 7 : il ne faut pas l'ajouter. « Incendies » est le total des types de feux, sans la colonne 8 (vérifié sur les 99 lignes du fichier, zéro écart).

### Ce qu'on retire

55 colonnes : Zone et Région (une seule valeur dans les 12 lignes) et les 53 colonnes qui ne sont pas des feux (secours à personne, accidents de circulation, risques technologiques, protection des biens, divers, fausses alertes, total des interventions).

### Les corrections à faire

1. Lire le fichier en Windows-1252, pas en UTF-8.
2. Enlever le « ? » dans les nombres (par exemple « 1?320 ») et les convertir en entiers.
3. Mettre les codes département sur 2 caractères et en majuscules (« 1 » devient « 01 », « 2a » devient « 2A »). Sans effet sur nos 12 lignes, utile pour relier d'autres sources.

## 3. La ligne Gironde (numéro 33)

La Gironde est un service de catégorie A, avec 5 453 incendies et 175 feux de végétations en 2024. Elle a la valeur la plus haute du Sud-ouest sur 7 des 12 colonnes de feux. Quatre types de feux sont à zéro chez elle (cheminées, ERP sans local à sommeil, locaux artisanaux, locaux agricoles) alors que d'autres départements du Sud-ouest ont des valeurs : peut-être des cases non remplies, à vérifier auprès du SDIS.

## 4. Limites et pièges

- **Grain trop gros pour nos questions.** Un total par département et par an : pas de date, de commune, de cause, de surface ni de délai d'intervention.
- **« Feux de végétations » n'est pas « feux de forêt ».** La colonne peut contenir d'autres feux (herbe, friches). À vérifier dans la notice.
- **Le « ? » dans les nombres et l'encodage Windows-1252.** 1 563 valeurs à nettoyer, et un fichier qui s'affiche mal en UTF-8.
- **Données déclarées par les services.** Un zéro peut vouloir dire « non renseigné » (45 services à zéro en feux de locaux artisanaux, par exemple).

## 5. Ce que cette source couvre pour nos questions

| Question | Couverture | Pourquoi |
| --- | --- | --- |
| 3. Combien de feux de forêt par an ? | En partie | Feux de végétations par département, 2024 seulement |
| 8. Quelles communes ont le plus de feux ? | En partie | On a le département, pas la commune |
| 4, 5, 6, 7, 9, 12, 13, 14, 21 | Non | Ni surface, ni cause, ni date, ni délai, ni indice dans ce fichier |
| 15, 16 | Non | Pas de budget ni d'effectifs dans ce fichier |

Le fichier sert surtout de contexte : il donne le nombre de feux par type et par département, à croiser avec des sources plus détaillées.

## Sources

Pages vues dans les résultats de recherche, pas encore ouvertes en entier : à relire pour confirmer la licence et la date de mise à jour.

- [Page du jeu de données sur data.gouv.fr](https://www.data.gouv.fr/datasets/interventions-realisees-par-les-services-d-incendie-et-de-secours)
- [Statistiques 2024 – DGSCGC, ministère de l'Intérieur](https://www.interieur.gouv.fr/documentation/etudes-et-statistiques/statistiques-2024-dgscgc.html)
- [Document « Statistiques interventions SDIS, édition 2025 sur année 2024 »](https://www.faceaurisque.com/wp-content/uploads/2025/12/Statistiques-interventions-Sdis-edition-2025-sur-annee-2024_compressed.pdf)
