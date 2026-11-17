---
updated: 2026-11-17
---
# Analyse de la commande - Melissa Benbouabdellah

## 1. Les questions

Quatre questions dont la réponse aiderait la direction à trancher.

> [!test] Test
> Le test : si la réponse est X, la direction fait A ; si elle est Y, elle fait B. Si A et B sont identiques, ce n'est pas une question analytique pertinente.

1. **Dans quelles zones de Gironde (communes, massifs) se concentrent les départs de feu en été, et cette concentration est-elle stable d'une année à l'autre ?**
   *Si quelques zones regroupent la majorité des départs chaque année, la direction y concentre ses moyens humains et financiers. Si les départs sont dispersés ou changent de zone chaque année, elle garde une répartition large et mise sur des moyens mobiles.*

2. **Pour chaque niveau de la Météo des forêts, quelle part des jours a connu au moins un départ de feu en Gironde (et inversement, quelle part des départs de feu a eu lieu à chaque niveau) ?**
   *Cette question mesure les deux défauts cités dans la commande : les fausses alertes (indice élevé, aucun feu) et les feux « surprises » (feu à indice bas). Si les départs deviennent fréquents dès un niveau modéré, la direction abaisse le seuil de déclenchement. S'ils restent rares jusqu'aux niveaux les plus hauts, elle le relève et économise des journées de dispositif renforcé.*

3. **La relation entre le niveau de l'indice et les départs de feu est-elle la même dans toutes les zones de Gironde ?**
   *Si l'indice « prévoit » bien les feux dans certaines zones et mal dans d'autres, la direction fixe un seuil différent selon les zones (renforcement ciblé, compatible avec le budget). Si la relation est la même partout, elle garde un seuil unique pour tout le département.*

4. **À niveau d'indice égal, la Gironde connaît-elle plus ou moins de départs de feu que les autres départements de Nouvelle-Aquitaine et que la moyenne nationale ?**
   *Si la Gironde a nettement plus de départs que les autres à indice égal, l'indice sous-estime le danger chez elle : la direction se cale sur un seuil plus bas que le seuil national et peut s'inspirer des départements qui s'en sortent mieux. Si la Gironde est dans la moyenne, le seuil national est une base fiable et le problème vient d'ailleurs (causes, zones, moyens).*

## 2. Les termes inconnus

Les mots de la commande que vous ne savez pas définir précisément, ou qui peuvent se comprendre de plusieurs façons.

| Terme | Ce que je crois qu'il veut dire | Ce qu'il faudrait vérifier |
|---|---|---|
| Météo des forêts | L'indice quotidien de danger de feu de forêt publié par Météo-France, calculé à partir de la météo (vent, humidité, température, sécheresse) | Combien de niveaux il compte, à quelle échelle il est calculé (département, zone, maille), depuis quand il existe et si l'historique est téléchargeable |
| Niveau / seuil de l'indice | Une classe de danger (faible, modéré, élevé…) correspondant à une plage de valeurs | Les valeurs numériques derrière chaque niveau, et si elles sont identiques partout en France |
| Seuil actuel | Le niveau à partir duquel le SDIS 33 déclenche aujourd'hui le dispositif renforcé | Sa valeur exacte, qui le décide, et s'il est le même sur tout le département |
| Dispositif renforcé | Les moyens ajoutés quand le danger monte : patrouilles, guet, pré-positionnement | Ce qu'il contient précisément, son coût par jour, sa durée minimale, et s'il peut être déclenché sur une partie du département seulement |
| Départ de feu | Le début d'un incendie de forêt, quelle que soit sa taille | À partir de quelle surface un départ est enregistré, et si les feux éteints très vite sont comptés |
| Moyens (humains et financiers) | Les pompiers (professionnels et volontaires), les véhicules, le budget de la saison | Le budget disponible pour l'été 2027 et ce qui est réellement déplaçable d'une zone à l'autre |
| « Concentrer » les moyens | Mettre plus de moyens dans les zones les plus à risque | À quelle échelle : commune, massif, secteur d'un centre de secours ? |
| « Comment l'indice se comporte » | Si l'indice annonce correctement les jours où des feux partent | Le critère de réussite attendu par la direction : moins de fausses alertes, moins de feux non prévus, ou un équilibre entre les deux ? |
| « Autres départements de la région » | Les départements de Nouvelle-Aquitaine | Si tous sont comparables à la Gironde (certains ont peu de forêt) |
| L'été | La saison des feux | Les dates exactes : juin à septembre, ou toute la période à risque (printemps compris) ? |

## 3. Les besoins

La décision à éclairer, en une phrase : où et à partir de quel niveau de la Météo des forêts le SDIS 33 doit-il déclencher son dispositif renforcé pour l'été 2027, sachant que son budget ne lui permet pas de le faire partout ni tout le temps ?

Ce qui manque dans la commande pour y répondre (une information, une précision, une hypothèse à confirmer) :
- La valeur du seuil actuel de déclenchement et la façon dont il est appliqué (tout le département ou par zone).
- Le budget disponible pour la saison 2027 et le coût d'une journée de dispositif renforcé, pour savoir combien de « journées × zones » la direction peut se payer.
- L'échelle à laquelle la direction peut réellement déplacer ses moyens (commune, massif, secteur de centre de secours).
- Ce que la direction juge le plus grave : déclencher pour rien (gaspillage) ou rater un feu (risque) ? Cet arbitrage fixe le seuil.
- L'historique des jours où le dispositif renforcé a été déclenché, pour comparer avec les feux réellement survenus.
- Hypothèse à confirmer : l'été 2027 ressemblera à l'été 2026. Sur quoi repose-t-elle, et 2026 est-il représentatif ?
- Hypothèse à confirmer : l'historique de la Météo des forêts est assez long pour tirer des conclusions (l'indice est récent ; à vérifier s'il existe un historique recalculé sur les années précédentes).

## 4. Les données

Pour chaque question, la donnée qu'il vous faudrait idéalement pour répondre.

| Question | Donnée idéale | Grain (une ligne = ?) | Période | Fraîcheur | Emprise géographique |
|---|---|---|---|---|---|
| 1 | Chaque départ de feu avec sa date, sa commune, ses coordonnées et sa surface brûlée, plus la carte des massifs forestiers | Un départ de feu | Les 10 à 20 derniers étés | Saison 2026 incluse | Gironde, à la commune ou plus fin (coordonnées) |
| 2 | Le niveau de la Météo des forêts de chaque jour, croisé avec le nombre de départs de feu ce jour-là | Un jour × une zone de l'indice | Toutes les saisons où l'indice (ou un historique recalculé) existe | Quotidienne, saison 2026 incluse | Gironde, par zone de calcul de l'indice |
| 3 | Les mêmes données qu'en question 2, découpées par zone, avec la correspondance entre zones de l'indice et communes | Un jour × une zone de l'indice | Idem question 2 | Quotidienne, saison 2026 incluse | Gironde, par zone de l'indice et par commune |
| 4 | Niveau de l'indice et nombre de départs de feu par jour pour chaque département, avec la surface de forêt pour comparer à taille égale | Un jour × un département | Idem question 2 | Quotidienne, saison 2026 incluse | Nouvelle-Aquitaine par département, et France entière |
