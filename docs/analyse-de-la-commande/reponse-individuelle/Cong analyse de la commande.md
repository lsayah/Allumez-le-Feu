---
updated: 2026-11-13T12:32:19.918+01:00
edited_seconds: 6
---
# Analyse de la commande - Hoa CONG

## 1. Les questions

Quatre questions dont la réponse aiderait la direction à trancher.

> [!test] Test
> Le test : si la réponse est X, la direction fait A ; si elle est Y, elle fait B. Si A et B sont identiques, ce n'est pas une question analytique pertinente.

1. Quelle est le budget et effectif proposés (pompiers, pompiers volontaires, services médicaux, hopitaux) dans la région ?
2. Où sont situés toute les casernes, aéroports, lac et hopitaux de la région ?
3. Quelles sont les données météo (température, humidité) de la région passé ?
4. Les raisons, lieu, temps, progressions, etc des incendies précédentes ?

## 2. Les termes inconnus

Les mots de la commande que vous ne savez pas définir précisément, ou qui peuvent se comprendre de plusieurs façons.

| Terme | Ce que je crois qu'il veut dire | Ce qu'il faudrait vérifier |
|---|---|---|
|Feu fixé | Feu qui a été maitrisé| un incendie fixé n’est pas un incendie éteint mais un incendie qui ne progresse plus dans son axe de propagation principal.|
|Feu maîtrisé | Feu éteint | Toutes les flammes importantes sont éteintes. Il reste néanmoins des foyers chauds qu’il faut surveiller et des risques de reprise.|
|Pyrocumulus||Une manifestation naturelle due au mélange des fumées à la condensation de l’air chaud rejeté verticalement par les feux dans l’atmosphère.|
|Feu circonscrit||Les sapeurs-pompiers l’entourent complètement et que l’incendie ne peut plus progresser ailleurs que dans la zone cernée. Un incendie peut ainsi être et maîtrisé, et circonscrit. |

## 3. Les besoins

La décision à éclairer, en une phrase :

Ce qui manque dans la commande pour y répondre (une information, une précision, une hypothèse à confirmer) :
- Départ de feu due à une température sèche et une taux d'humidité basse due aux canicules prolongés dans tout(e) la région/le pays. 
- Point de feu à plusieurs endroit différente dans un très petit lap de temps dont dans des régions assez difficiles d'accès, un manque d'effectif et aussi de point d'eau dans des grosses zones boisées/inhabités.

## 4. Les données

Pour chaque question, la donnée qu'il vous faudrait idéalement pour répondre.

| Question | Donnée idéale | Grain (une ligne = ?) | Période | Fraîcheur | Emprise géographique |
|---|---|---|---|---|---|
| Q1 - Où démarrent le plus de feux ? | Commune et coordonnées de chaque feu (BDIFF) | Un feu | 10 dernières années | Dernier mois | Région, par commune |
| Q2 - À quel moment démarrent les feux ? | Date et heure de départ de chaque feu (BDIFF) | Un feu | 10 dernières années | Dernier mois | Région |
| Q3 - La surface brûlée augmente-t-elle ? | Surface brûlée de chaque feu (BDIFF) | Un feu | 10 dernières années | Annuelle | Région |
| Q4 - Combien de feux dépassent 1 hectare ? | Surface brûlée de chaque feu (BDIFF) | Un feu | 10 dernières années | Dernier mois | Région |
| Q5 - Quelles sont les causes des feux ? | Cause de chaque feu (BDIFF) | Un feu | 10 dernières années | Dernier mois | Région, par commune |
| Q6 - Les feux démarrent-ils près des routes et des maisons ? | Coordonnées des départs de feu, des routes, des voies ferrées et des bâtiments (BDIFF, BD TOPO) | Un feu | 10 dernières années | Annuelle | Région |
| Q7 - Combien de feux sont criminels, et où ? | Cause et commune de chaque feu (BDIFF) | Un feu | 10 dernières années | Dernier mois | Région, par commune |
| Q8 - À quel niveau de risque météo les feux se multiplient-ils ? | Indice Forêt Météo du jour et nombre de départs de feu (Météo-France, BDIFF) | Une station météo par jour | 10 dernières années | Quotidienne | Région, par station |
| Q9 - Y a-t-il plus de jours chauds et secs qu'avant ? | Température et humidité de chaque jour (Météo-France) | Une station météo par jour | 30 dernières années | Quotidienne | Région, par station |
| Q10 - Les grands feux ont-ils lieu par vent fort ? | Vitesse du vent le jour de chaque feu (Météo-France, BDIFF) | Un feu | 10 dernières années | Quotidienne | Région |
| Q11 - Combien de temps mettent les pompiers pour arriver ? | Heure d'alerte et heure d'arrivée des secours (SDIS) | Une intervention | 5 dernières années | Dernier mois | Région, par commune |
| Q12 - Arriver vite limite-t-il la taille du feu ? | Délai d'intervention et surface brûlée de chaque feu (SDIS, BDIFF) | Un feu | 10 dernières années | Dernier mois | Région |
| Q13 - Quelles forêts sont loin d'une caserne ? | Coordonnées des casernes et des forêts, temps de trajet par la route (BD TOPO) | Une zone boisée | Situation actuelle | Annuelle | Région |
| Q14 - Quelles forêts sont loin d'un point d'eau ? | Coordonnées des lacs utilisables par les bombardiers d'eau et des forêts (BD TOPO) | Une zone boisée | Situation actuelle | Annuelle | Région |
| Q15 - Les secours suivent-ils quand plusieurs feux démarrent en même temps ? | Heures d'alerte et d'arrivée des secours les jours à plusieurs feux (SDIS) | Un feu | 10 dernières années | Dernier mois | Région |
| Q16 - Combien de pompiers volontaires sont disponibles l'été ? | Nombre de volontaires disponibles par jour (SDIS) | Un centre de secours par jour | 5 derniers étés | Hebdomadaire | Région, par centre de secours |
| Q17 - Le budget est-il le même dans chaque département ? | Budget des secours et surface de forêt de chaque département (DGSCGC, IGN) | Un département par année | 10 dernières années | Annuelle | Région, par département |
| Q18 - Où placer les postes de guet ? | Coordonnées des départs de feu et relief (BDIFF, IGN) | Un feu | 10 dernières années | Annuelle | Région |
| Q19 - Combien de maisons sont proches d'une forêt à risque ? | Coordonnées des habitations et carte des forêts à risque (BD TOPO, préfecture) | Une habitation | Situation actuelle | Annuelle | Région, par commune |
| Q20 - Quels hôpitaux sont loin des zones à risque ? | Coordonnées des hôpitaux et carte des zones à risque (FINESS, préfecture) | Un hôpital | Situation actuelle | Annuelle | Région |
| Q21 - Le débroussaillement réduit-il les feux ? | Contrôles de débroussaillement et nombre de feux par commune (mairies, BDIFF) | Une commune par année | 10 dernières années | Annuelle | Région, par commune |