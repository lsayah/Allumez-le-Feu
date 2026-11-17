---
updated: 2026-11-13T12:58:07.517+01:00
edited_seconds: 37
---
# Le glossaire du projet

**Modalité :** en groupe. Chaque membre ajoute des termes ; le ou la chef·fe de projet tient le fichier et valide les entrées.

**Quand :** 
- une première version en fin de S1, à partir de vos termes inconnus de l'exercice 1. 
- Le glossaire est ensuite tenu à jour jusqu'au rendu final du 11/12.

## Pourquoi un glossaire

Un même mot ne veut pas dire la même chose pour la direction, pour chaque source et pour chaque membre du groupe. Quelques exemples tirés de votre sujet :

- **« Feu de forêt »** : la direction parle de départs de feu, une source recense des feux de forêt, une autre des interventions pour incendie. S'agit-il des mêmes événements ? Comment-les définissez-vous ?
- **« Danger élevé »** : la Météo des forêts a plusieurs niveaux. Quand un chef de centre dit que l'indice « annonce un danger élevé », de quel niveau parle-t-il ?
- **« Département »** : un code INSEE, ou le territoire couvert par un service d'incendie ? Les deux ne coïncident pas toujours.

Si vous ne fixez pas ces définitions, vos chiffres changeront selon la personne qui écrit la requête et la source sur laquelle vous vous basez; vos indicateurs (UE01.B) ne seront pas comparables, et la direction lira autre chose que ce que vous avez réellement mesuré.

## Ce que contient une entrée

Les champs ci dessous sont des exemples courants, ils ne seront pas tous pertinent selon le contexte, à vous d'adapter votre fichier.

| Champ                    | Ce que vous y écrivez                                                      |
| ------------------------ | -------------------------------------------------------------------------- |
| Terme                    | Le mot tel que la direction ou une source l'emploie                        |
| Définition               | Une ou deux phrases compréhensibles par la direction, sans nom de colonne  |
| Sources et colonnes      | Où ce terme apparaît : source, fichier, colonne                            |
| Divergences              | Ce que chaque source entend par ce terme, quand ce n'est pas la même chose |
| Règle retenue            | Ce que le groupe a décidé, et le lien vers la décision dans le journal     |
| Unité ou granularité     | Hectare, jour, département, commune…                                       |
| Exemple                  | Une valeur réelle tirée d'une source                                       |
| Statut                   | Proposé, validé ou à vérifier                                              |
| Origine de la définition | Documentation du producteur, texte réglementaire, décision du groupe       |

## Exemple d'entrée

_une communauté de communes issue d'une fusion hérite de trois réseaux de médiathèques._

**Lecteur actif (réseau de médiathèques)**
- **Définition :** personne inscrite dans un réseau de médiathèques qui a emprunté au moins un document au cours des douze derniers mois.
- **Sources et colonnes :** exports des logiciels des trois réseaux (date d'inscription, date du dernier prêt).
- **Divergences :** le réseau A compte comme actif tout inscrit dont l'abonnement est en cours ; le réseau B, toute personne ayant emprunté pendant l'année civile ; les compteurs de passage comptent des entrées, pas des personnes. Une personne inscrite dans deux réseaux apparaît deux fois.
- **Règle retenue :** au moins un prêt dans les douze derniers mois, tous réseaux confondus, chaque personne comptée une seule fois (décision 004 du journal).
- **Unité ou granularité :** une personne ; période glissante de douze mois.
- **Exemple :** lecteur n° 10482 du réseau A, dernier prêt le 3 mars 2026 : actif. Inscrit aussi au réseau B sous le n° 2291 : même personne, comptée une fois.
- **Statut :** validé.
- **Origine :** règlements des trois réseaux, puis décision du groupe.

## Comment le construire
1. **Partez de vos termes inconnus.** Chaque membre apporte ceux de son analyse de la commande. Fusionnez les doublons et gardez trace de qui les a proposés.
2. **Ajoutez les termes rencontrés en ouvrant les sources.** Chaque fois qu'une fiche d'identité emploie un mot métier, il a sa place dans le glossaire.
3. **Écrivez la définition dans les mots de la direction.** « Le champ `surf_ha` » n'est pas une définition.
4. **Ne gommez pas les divergences.** Si deux sources ne définissent pas un terme de la même façon, écrivez-le, décidez, et consignez la décision dans le journal.
5. **Citez l'origine de chaque définition.** Tant qu'une définition n'est pas confirmée par la documentation, son statut reste « à vérifier ».

## Comment l'entretenir
- **Toute modification passe par un ticket et une pull request**, relue par le ou la chef·fe de projet.
- **Mettez-le à jour à chaque étape** : nouvelle source, règle de qualité, choix de minimisation, grain d'un fait, dimension historisée. Chaque décision qui touche le sens d'un terme modifie son entrée.
- **Ne supprimez jamais un terme.** Marquez-le « obsolète », avec la raison et la date.
- **Avant le rendu final**, vérifiez que chaque terme employé dans vos questions, vos indicateurs et vos tableaux est dans le glossaire, et que chaque colonne de l'entrepôt qui porte une notion métier renvoie à son terme.
- Vous devez être en capacité d'expliquer chaque terme et ses caractéristiques pendant la présentation

## Modèle

Créez `docs/glossaire.md` avec la structure suivante, une section par terme, dans l'ordre alphabétique :

```markdown
# Glossaire — [Région]

Dernière mise à jour : AAAA-MM-JJ

## [Terme]

- **Définition :**
- **Sources et colonnes :**
- **Divergences :**
- **Règle retenue :** (lien vers la décision)
- **Unité ou granularité :**
- **Exemple :**
- **Statut :** proposé / validé / à vérifier / obsolète
- **Origine de la définition :**
- **Ajouté par :** Prénom Nom, AAAA-MM-JJ
```

## Rendu de fin de S1

La version 0 de `docs/glossaire.md`, avec au moins huit termes, entre dans `main` par une pull request.

**Avant de la fusionner, vérifiez que :**
- chaque terme inconnu de vos analyses individuelles a une entrée, ou une raison d'avoir été écarté ;
- aucune définition ne se réduit à un nom de colonne ;
- chaque divergence repérée est écrite, même si la règle n'est pas encore décidée ;
- chaque définition a son origine, ou le statut « à vérifier ».