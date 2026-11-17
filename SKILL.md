---
name: refonte-design-guide
description: Méthode pour analyser, concevoir et implémenter une refonte UX/UI de page, composant, widget ou modal sur web et mobile. Aide à clarifier la hiérarchie de l'information, les actions, les états, l'accessibilité et la cohérence visuelle sans perdre le sens métier ni l'identité du produit.
---

# Méthode de refonte UX/UI

Guide autonome pour toute refonte de page, composant, widget ou modal web et
mobile. Il fournit une méthode, des critères de décision et des exemples
génériques. Le code, les données et les consignes du projet concerné restent
nécessaires pour comprendre son métier.

## Contrat d'utilisation

- Lire le code et les consignes du projet avant de proposer une modification.
- Préserver les fonctions, destinations, droits, données et règles métier
  existants, sauf demande explicite contraire.
- Distinguer les observations faites dans le code ou l'interface, les
  recommandations de conception et les comportements réellement vérifiés.
- Ne pas inventer de métriques, de retours utilisateurs, de données ou de
  résultats de tests.
- Adapter l'effort au risque : une retouche locale demande des contrôles ciblés ;
  une refonte de parcours demande la vérification des états et de la récupération.
- Demander une clarification uniquement lorsqu'un choix change une règle métier,
  une destination, une donnée importante ou une intention utilisateur.

## Mode d'emploi

Avec ce guide et la surface à refondre :

1. Lire la page, ses composants, ses sources de données, ses actions et leurs
   destinations. Consulter les instructions du dépôt.
2. Établir l'intention de l'utilisateur à l'entrée et le résultat attendu à la
   sortie, à partir du parcours réellement implémenté.
3. Inventorier les informations et actions présentes, y compris dans les états
   de chargement, d'erreur, d'absence de données et d'indisponibilité.
4. Définir la hiérarchie et le traitement de chaque élément avec les critères
   ci-dessous. Examiner aussi la composition entière : répétitions entre
   composants, poids visuels, styles, espacements, textes et images.
5. Implémenter dans les composants réellement utilisés et vérifier le parcours
   complet affecté, pas seulement l'apparence d'un composant isolé.
6. Livrer une explication courte du problème corrigé, des vérifications réalisées
   et de leurs limites.

## Objectif

Rendre immédiatement compréhensibles l'information essentielle et la prochaine
action utile. Une refonte doit résoudre un problème de lecture, de décision ou
de parcours. Changer les couleurs ou arrondir les cartes ne suffit pas.

Épurer signifie réduire les répétitions et la concurrence visuelle tout en
préservant les informations utiles, les fonctions et leur accessibilité.
L'identité existante reste le point de départ.

## 1. Comprendre le vrai problème

Lire le composant, ses données et ses actions réelles, en plus de toute
référence visuelle. Formuler brièvement :

- Ce que l'utilisateur vient de faire et ce qu'il cherche maintenant.
- L'information qu'il doit comprendre en premier.
- L'action la plus utile à cet instant et les autres destinations nécessaires.
- Ce qui gêne aujourd'hui : répétition, priorité inversée, bouton concurrent,
  libellé ambigu, information dispersée, étape superflue ou débordement.

Exemple : après la validation d'une activité, le statut d'enregistrement et un
ornement très visible occupaient la première place, alors que le résultat
obtenu et la possibilité de continuer méritaient la priorité.

Ne pas demander au responsable produit de redéfinir chaque marge, titre ou
bouton : déduire les choix courants du parcours et du code. Une clarification
est utile si le choix change une règle métier ou si deux intentions
incompatibles restent possibles.

### Diagnostic attendu

> L'utilisateur arrive ici pour **[objectif]**. Il doit d'abord comprendre
> **[information]**, puis pouvoir **[action ou consultation attendue]**.
> Aujourd'hui, **[élément concret]** gêne cela parce que **[conséquence]**.
> La refonte va **[changement de hiérarchie ou de parcours]**, tout en
> conservant **[données, destinations et contraintes à préserver]**.

Appuyer le diagnostic sur des observations : deux boutons déclenchent la même
action, un grand titre répète le contenu, un montant est séparé de sa
condition, ou une action indispensable est hors de portée. Éviter les
justifications vagues comme « plus moderne » ou « plus propre ». Ne pas
présenter comme mesuré un gain qui n'a pas été mesuré.

## 2. Donner un rôle clair à chaque information

Organiser la lecture selon l'importance pour la tâche :

1. **Essentiel** : résultat, contenu ou décision qui justifie cet écran.
2. **Contexte utile** : détails nécessaires pour interpréter cet essentiel.
3. **Complément** : comparaison, historique ou destination secondaire.

Utiliser d'abord l'ordre, la taille, la graisse, la proximité et l'espace.
Regrouper les informations liées ; éviter une carte, une icône ou un titre pour
chaque valeur. Une même information ne doit pas être annoncée plusieurs fois
sans raison.

Pour chaque élément existant, décider : conserver, regrouper, reformuler,
déplacer vers un détail accessible ou supprimer parce qu'il est redondant. Une
information nécessaire à la décision reste visible au moment de décider. Ne
pas cacher une erreur, un coût, une condition importante ou une action
fréquente dans un menu pour alléger artificiellement l'écran.

| Question | Décision à envisager | Condition à respecter |
| --- | --- | --- |
| Sans cet élément, peut-on comprendre le résultat ou décider ? | Le garder au premier niveau | Inclure unité, contexte et condition indispensables |
| Plusieurs éléments répondent-ils à la même question ? | Les regrouper | Ne pas confondre des concepts distincts |
| La même information est-elle répétée avec le même sens ? | Retirer une occurrence | Une valeur égale ne prouve pas à elle seule une redondance |
| Le détail est-il occasionnel ? | Le déplacer vers un accès secondaire explicite | Sa destination et son libellé doivent permettre de le retrouver |
| Le texte décrit-il longuement une action déjà claire ? | Le raccourcir | Conserver sens, destination et distinctions nécessaires |
| L'élément est-il décoratif et détourne-t-il l'attention ? | Réduire son poids ou le retirer | Préserver les repères utiles et l'identité du produit |

Pour chaque retrait ou déplacement, pouvoir expliquer où l'information ou la
fonction reste accessible, ou pourquoi elle faisait réellement doublon. En cas
de doute sur son rôle métier, la conserver jusqu'à clarification.

## 3. Hiérarchiser les actions

- Quand le parcours a une prochaine action évidente, lui réserver l'accent
  principal. Les actions secondaires restent visibles avec moins de poids.
- Nommer l'action avec des mots courts et précis : « Continuer », « Modifier »,
  « Détails », « Retour », lorsque le contexte suffit.
- Garder des zones tactiles confortables même pour les boutons discrets.
- Conserver les confirmations et protections nécessaires aux actions sensibles.
- Choisir une icône selon son sens perçu et fournir un libellé accessible aux
  commandes iconographiques.

Un seul bouton principal peut convenir à un écran de confirmation, mais ce
n'est pas une règle mécanique. Une page de consultation, un formulaire ou une
comparaison doivent suivre leur propre usage.

## 4. Préserver le sens, l'identité et le comportement

Conserver les couleurs, typographies et conventions pertinentes de la page ou
du produit. Une structure commune peut respecter plusieurs identités sans
uniformiser tous les écrans.

Vérifier la signification des données avant de les présenter. Un résultat
courant, un meilleur résultat et un classement sont des informations
différentes. Une unité ne doit pas être copiée d'un domaine à l'autre. Ne pas
inventer de valeur pour remplir la composition et ne pas annoncer un succès
avant confirmation.

Préserver les destinations, droits, règles métier et réglages indépendants.
Brancher réellement les boutons et vérifier les états concernés : chargement,
erreur, absence de données, succès, indisponibilité et nouvelle tentative.

## 5. Composer une page cohérente

Des composants lisibles séparément ne garantissent pas une bonne page. Évaluer
ce que leur réunion produit dans les différents états de contenu, pas
uniquement la qualité de chaque composant.

**Épuré ne signifie pas neutre.** Retirer le bruit et les répétitions ne
demande pas de supprimer les couleurs, illustrations, textures, dégradés ou
ornements qui donnent son identité à l'interface. Conserver ceux qui servent
le contexte et la hiérarchie, en ajustant leur intensité.

**Clarifier la hiérarchie ne doit pas effacer le caractère visuel.** Lorsqu'une
structure UX fonctionne, travailler son expression : surfaces, couleurs,
typographie, illustration et détails adaptés au contexte. Réduire les effets
excessifs sans supprimer toute décoration par défaut.

Distinguer deux questions complémentaires :

- **UX** : comprend-on les informations, les choix et leurs conséquences ?
- **UI** : la composition, les styles et les proportions rendent-ils cette
  hiérarchie perceptible et cohérente à l'échelle de l'écran ?

| Dimension | Question concrète | Ajustement possible |
| --- | --- | --- |
| Poids visuel | Quel élément attire le regard ? Son importance le justifie-t-elle ? | Réduire les accents concurrents avant d'agrandir l'action principale |
| Styles | Les surfaces, boutons et icônes semblent-ils appartenir à la même interface ? | Harmoniser bordures, ombres, arrondis et rôles, sans effacer les différences utiles |
| Typographie | Titres, valeurs et explications ont-ils des rôles distincts ? | Donner des rôles stables aux tailles et graisses |
| Espacements | Les éléments liés sont-ils plus proches que les groupes distincts ? | Ajuster les espacements internes et entre sections |
| Actions secondaires | Leur traitement leur donne-t-il trop de présence ? | Alléger l'apparence tout en conservant une zone interactive confortable |
| Images | Le sujet reste-t-il reconnaissable dans le cadre réel ? | Choisir ratio, position et recadrage selon l'image |

La cohérence n'impose pas un style uniforme ou minimaliste. Une illustration
ou une récompense peut être expressive ; vérifier si le cumul d'effets sert sa
place dans la page. Un composant réutilisé peut nécessiter une variante plus
sobre ici tout en gardant une présentation riche ailleurs.

### Auto-évaluation honnête

Pour chaque critique, identifier l'élément observable, expliquer son effet
possible et proposer un ajustement proportionné. Distinguer observation,
jugement visuel et comportement réellement vérifié. Nommer aussi ce qui
fonctionne et doit être préservé.

Un espace libre n'est pas forcément du gaspillage ; une image coupée n'est pas
forcément mal cadrée ; une différence de style peut être intentionnelle. Une
capture permet d'examiner la composition visible, pas de conclure sur tous les
états ou interactions.

## 6. Exemple générique : écran de résultat

Situation : une activité vient de se terminer. L'utilisateur veut connaître le
résultat de cette tentative, le situer par rapport à son meilleur résultat,
puis recommencer ou consulter un détail. Le classement général ne signifie pas
que la tentative actuelle est un nouveau record.

L'ancienne présentation mettait en avant un grand trophée, un message de statut
et une position, puis seulement le résultat. Les statistiques étaient
secondaires et plusieurs actions rivalisaient entre elles. Le problème était
la priorité visuelle donnée au statut et au rang au détriment du résultat
immédiat et de la suite du parcours.

Exemple de présentation, avec des valeurs illustratives :

```text
                 ACTIVITÉ TERMINÉE          ← repère discret
                       333                   ← information dominante
                      points                 ← unité proche du résultat

       158 unités · 7 étapes · 11,57 s      ← mesures de cette tentative

        Classement général · #1   Meilleur : 3379 points

                  [ Recommencer ]            ← seul bouton rempli
              Détails          Accueil       ← actions secondaires
```

Le résultat et son unité forment le premier groupe. Les mesures de cette
tentative forment le deuxième. Le rang et le meilleur résultat forment un
groupe de comparaison moins accentué. Les lignes peuvent se replier sur un
écran étroit ; aucun ordre de lecture ne dépend d'une largeur fixe.

Les chiffres sont un exemple de présentation, pas des données à coder en dur.
Les métriques et leurs unités doivent venir du domaine réel. Une répétition
numérique peut être omise dans un bilan compact, mais une distinction utile
doit rester visible si elle compte pour le parcours. Une égalité n'est pas un
nouveau record. Un statut de fin ne doit pas annoncer une sauvegarde réussie
si celle-ci est encore en cours ou a échoué.

Les actions doivent réellement déclencher leur destination : recommencer
l'activité, ouvrir les détails et revenir à la page d'accueil. Le travail
inclut ces branchements et leurs états.

### Transposer à d'autres pages

Ces situations sont hypothétiques et servent à appliquer le raisonnement :

| Situation | Problème à résoudre | Application |
| --- | --- | --- |
| Confirmation d'une commande | Montant, frais et conditions dispersés | Regrouper ce qui permet de décider et rendre le total visible avant confirmation |
| Formulaire de profil | Titres répétés et enregistrement difficile à trouver | Regrouper les champs liés, hiérarchiser l'enregistrement et garder les erreurs au bon endroit |
| Liste d'événements | Badges dominants, dates difficiles à comparer, tri ambigu | Prioriser les informations qui permettent de choisir et rendre tri et filtres compréhensibles |
| Paramètres audio | Un bouton global masque plusieurs réglages indépendants | Regrouper les commandes sans les fusionner et préciser ce que chacune active |

Une page de lecture peut n'avoir aucun bouton dominant. Une page de comparaison
peut donner la même importance à plusieurs options. Ne pas transformer tous les
écrans en un résultat central suivi d'un grand bouton.

## 7. Vérifier et livrer

Vérifier les actions réelles et les états modifiés, les petits écrans, le texte
agrandi, les libellés longs et les grandes valeurs. Préférer un retour à la
ligne ou un défilement maîtrisé à une réduction excessive des textes. Garder
les actions atteignables, les libellés accessibles et un contraste lisible.

Appliquer l'analyse statique et les contrôles fonctionnels ciblés utiles au
lot. Respecter les consignes et les outils de test du projet ; ne pas recréer
une ancienne suite supprimée sans demande explicite.

À la livraison, expliquer brièvement le problème corrigé, la nouvelle priorité
de lecture et d'action, les vérifications effectuées et leurs limites.

## Critères de fin

- Le premier niveau répond à l'intention de l'utilisateur et se distingue des
  compléments sans rendre ces derniers illisibles.
- Chaque information supprimée ou déplacée est justifiée et les données
  nécessaires à la décision restent disponibles au bon moment.
- Les actions ont des libellés compréhensibles et déclenchent les destinations
  ou opérations attendues, avec leurs protections et états réels.
- La solution reste utilisable avec les formats et tailles de texte concernés ;
  elle ne dépend ni de textes minuscules ni d'actions masquées.
- Le résultat respecte l'identité de l'écran et les contraintes métier.
- Les composants réunis conservent une hiérarchie visuelle cohérente et les
  répétitions entre composants ont été examinées selon les états de contenu.
- Le compte rendu distingue les vérifications réalisées des points non vérifiés.

Une refonte limitée à une nouvelle palette, à des coins arrondis ou à la
suppression d'informations sans justification ne satisfait pas cette méthode.
