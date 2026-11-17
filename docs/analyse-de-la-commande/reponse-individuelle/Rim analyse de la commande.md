# Analyse de la commande - Rim Zougarh

## 1. Les questions

Sept questions dont la réponse aiderait la direction à trancher.

1. Dans quelles zones de la Gironde les départs de feu sont-ils les plus fréquents ?
2. À partir de quel niveau de la Météo des forêts le nombre de départs de feu augmente-t-il vraiment ?
3. L'indice est-il aussi fiable en Gironde que dans les autres départements et en France ?
4. Les feux partis avec un indice bas ont-ils des points communs (cause, lieu, période) ?
5. Les feux partent-ils plutôt le jour où l'indice passe en danger élevé, ou après plusieurs jours de suite à ce niveau ?
6. Combien de jours de dispositif renforcé par été chaque seuil possible déclencherait-il en Gironde ?
7. Les critères météo utilisés par l'indice (chaleur, sécheresse, vent, humidité) suffisent-ils à expliquer les départs de feu en Gironde, ou faut-il en ajouter d'autres ?

## 2. Les termes inconnus

Les mots de la commande que vous ne savez pas définir précisément, ou qui peuvent se comprendre de plusieurs façons.

| Terme | Ce que je crois qu'il veut dire | Ce qu'il faudrait vérifier |
|---|---|---|
| SDIS | Les pompiers du département (service départemental d'incendie et de secours) | Comment il est organisé (nombre de centres) |
| Météo des forêts | Un indicateur de Météo-France qui donne le niveau de danger de feu chaque jour | Combien de niveaux, à quelle échelle (département ou zone), depuis quand il existe |
| Dispositif renforcé | Les moyens en plus quand le risque est élevé (patrouilles, guet) | Ce qu'il y a dans le « etc. » et combien ça coûte par jour |
| Guet | Surveiller depuis des tours pour repérer les fumées | Où sont les tours en Gironde |
| Seuil actuel | Le niveau d'indice à partir duquel ils déclenchent le renfort aujourd'hui | Sa valeur exacte |
| Chef de centre | Le responsable d'une caserne | — |

## 3. Les besoins

La décision à éclairer, en une phrase :

Savoir où et à partir de quel niveau de la Météo des forêts déclencher le dispositif renforcé à l'été 2027, sans pouvoir le faire partout tout l'été.

Ce qui manque dans la commande pour y répondre (une information, une précision, une hypothèse à confirmer) :
- La valeur du seuil actuel
- Le budget, ou combien de jours de renfort ils peuvent payer
- Ce qui est le plus grave pour eux : les fausses alertes ou les feux ratés
- Si le renfort peut être déclenché zone par zone ou seulement sur tout le département
- Ce qu'ils appellent un « départ de feu » (tous les feux ou seulement les grands)
- Hypothèse : l'été 2027 ressemblera à l'été 2026

## 4. Les données

Pour chaque question, la donnée qu'il vous faudrait idéalement pour répondre.

| Question | Donnée idéale | Grain (une ligne = ?) | Période | Fraîcheur | Emprise géographique |
|---|---|---|---|---|---|
| 1 | Liste des feux avec date, commune et surface brûlée | Un feu | 10 dernières années | Annuelle | Gironde |
| 2 | Niveau de l'indice chaque jour + nombre de feux ce jour-là | Un jour × un département | Depuis 2023 (création de l'indice) | Quotidienne | Gironde |
| 3 | Pareil que la question 2 pour tous les départements | Un jour × un département | Depuis 2023 | Quotidienne | Nouvelle-Aquitaine + France |
| 4 | Liste des feux avec la cause et le niveau de l'indice du jour | Un feu | Depuis 2023 | Annuelle | Gironde |
| 5 | Niveau de l'indice chaque jour, dans l'ordre, + feux du jour | Un jour × un département | Depuis 2023 | Quotidienne | Gironde |
| 6 | Niveau de l'indice chaque jour pendant l'été | Un jour × un département | Étés depuis 2023 | Quotidienne | Gironde |
| 7 | Données météo du jour (température, vent, humidité, pluie) + feux du jour | Un jour × une commune ou une zone | 10 dernières années | Quotidienne | Gironde |