# README - Analyse approfondie du projet `Grp1_RO`

## Périmètre de l'analyse

Cette analyse porte principalement sur le notebook [`Livrable_Modelisation.ipynb`](./Livrable_Modelisation.ipynb), qui constitue aujourd'hui le livrable central du projet.

Le document a été évalué par rapport :

- au sujet ADEME fourni dans le projet ;
- aux attendus du livrable final ;
- à la macro-grille d'évaluation `A / B / C / D`.

Cette analyse ne juge pas la qualité de la soutenance orale elle-même, mais l'état actuel du contenu technique et rédactionnel.

## Verdict rapide

- État global du projet : **très avancé**
- Niveau actuel du livrable : **cohérent, complet et déjà exploitable**
- Note estimée selon la macro-grille : **A**
- Réserve principale : **quelques incohérences de narration et de reproductibilité sont encore à nettoyer pour sécuriser l'évaluation**

Pourquoi une note `A` ?

- le programme est fonctionnel ;
- une étude théorique de complexité est présente ;
- une étude statistique expérimentale est présente.

Sur la macro-grille fournie, cela correspond bien à :

> **A : Programme fonctionnel avec étude théorique de complexité et étude statistique**

## 1. Ce qui est déjà fait correctement

### 1.1 Compréhension du besoin et reformulation du problème

Le notebook reformule correctement le besoin métier ADEME en un problème de **CVRP** (*Capacitated Vehicle Routing Problem*).

Ce choix est pertinent car il permet de traduire le contexte logistique en un modèle mathématique classique de recherche opérationnelle :

- un dépôt ;
- plusieurs clients ;
- plusieurs tournées ;
- une minimisation du coût total ;
- une contrainte de capacité des véhicules.

Le projet ne reste donc pas au niveau descriptif : il transforme bien le sujet métier en problème algorithmique formel.

### 1.2 Contraintes supplémentaires bien choisies

Le sujet impose d'ajouter au moins deux contraintes. Le notebook en prend bien en compte deux :

- **l'utilisation de plusieurs véhicules** ;
- **la capacité maximale des véhicules**.

Ces contraintes sont cohérentes avec le problème visé et suffisantes pour faire du sujet une vraie variante du VRP, pas seulement un TSP simplifié.

### 1.3 Modélisation formelle satisfaisante

La partie modélisation est sérieuse et bien structurée :

- définition du graphe ;
- distinction dépôt / clients ;
- définition des coûts ;
- définition des demandes ;
- fonction objectif clairement écrite ;
- contraintes explicites : visite unique, capacité, départ/retour dépôt, multi-tournées.

Sur ce point, le notebook répond bien à l'attendu du livrable de modélisation.

### 1.4 Analyse de complexité présente et globalement juste

La partie complexité est bien amorcée :

- le lien avec le **TSP** est explicité ;
- la **NP-difficulté** du CVRP est argumentée par réduction ;
- la complexité des méthodes implémentées est discutée ;
- le choix d'heuristiques est justifié par l'impraticabilité d'une résolution exacte sur des tailles réalistes.

C'est un très bon point, car cette partie est précisément ce qui distingue une note `A` d'une note `B` dans la macro-grille.

### 1.5 Implémentation Python riche et au-delà du minimum demandé

Le cahier des charges demandait au moins deux méthodes de résolution. Le notebook en propose en réalité plusieurs :

- `Sweep + NN`
- `Sweep + NN + 2-opt`
- `Clarke-Wright`
- `Clarke-Wright + 2-opt`
- `Recuit simulé`
- `Recherche tabou`

Autrement dit, le projet dépasse nettement l'exigence minimale.

Le code couvre aussi les briques essentielles :

- génération d'instances aléatoires ;
- calcul des distances ;
- validation des solutions ;
- calcul du coût ;
- comparaison de solveurs ;
- visualisation des tournées.

### 1.6 Génération d'instances aléatoires pertinente

Les instances sont générées de manière paramétrable avec :

- nombre de clients ;
- distribution spatiale `uniform` ou `clustered` ;
- demandes aléatoires ;
- capacité pilotée par un paramètre de tension ;
- graines pour la reproductibilité.

Ce point est bien traité, car les paramètres ne sont pas seulement codés : ils sont aussi expliqués dans le notebook.

### 1.7 Étude expérimentale réelle, pas juste illustrative

Le notebook contient une vraie étude expérimentale et pas seulement deux captures d'écran.

Le plan d'expérience principal repose sur :

- `4` tailles d'instances ;
- `2` distributions spatiales ;
- `2` niveaux de tension de capacité ;
- `3` répétitions par configuration ;
- `6` solveurs comparés.

Cela conduit à **288 exécutions de solveurs**, ce qui constitue déjà une base expérimentale sérieuse.

Les métriques sont pertinentes :

- coût total ;
- nombre de véhicules ;
- temps d'exécution ;
- écart relatif au meilleur solveur du panel ;
- gain par rapport à un baseline.

### 1.8 Résultats interprétés

Le notebook ne s'arrête pas aux tableaux :

- il commente les figures ;
- il compare qualité et temps ;
- il explique l'effet de la structure spatiale ;
- il discute le passage à l'échelle ;
- il distingue les usages "temps réel" et "planification hors-ligne".

Cette capacité d'interprétation est importante pour un jury, car elle montre que le projet ne se limite pas à "faire tourner du code".

### 1.9 Références bibliographiques présentes

La présence d'une bibliographie finale est un vrai plus.

Les références choisies sont pertinentes :

- Dantzig & Ramser ;
- Clarke & Wright ;
- Croes ;
- Gendreau, Hertz & Laporte ;
- Toth & Vigo.

Cela renforce la crédibilité du livrable.

## 2. Ce qui ressort comme particulièrement réussi

Voici les points les plus solides du notebook actuel.

- **Le cadrage est clair** : on comprend rapidement le problème, les contraintes retenues et le lien avec l'ADEME.
- **La structure est bonne** : modélisation, méthodes, démonstration, expérimentation, limites, conclusion.
- **Le projet dépasse le minimum attendu** : plusieurs solveurs, amélioration locale, métaheuristiques, stress tests.
- **Le code est lisible** : usage de `dataclass`, noms de fonctions explicites, séparation correcte des responsabilités.
- **La validation des solutions est intégrée** : c'est un excellent signal de robustesse.
- **L'étude statistique est déjà crédible** : le projet ne repose pas sur un unique cas favorable.
- **Les conclusions sont opérationnelles** : on comprend quel solveur recommander selon le contexte.

## 3. Ce qui reste à améliorer

Le projet est déjà solide, mais plusieurs points doivent être améliorés pour rendre la copie plus propre, plus défendable et plus cohérente.

### 3.1 Clarifier le positionnement exact du notebook

Le notebook est nommé `Livrable_Modelisation.ipynb`, mais son contenu correspond en réalité à un **livrable final complet** :

- modélisation ;
- implémentation ;
- exploitation ;
- expérimentation.

Ce n'est pas un problème de fond, mais cela peut créer une ambiguïté :

- soit assumer clairement que ce notebook est le livrable final ;
- soit renommer / séparer si vous souhaitez conserver une logique par étape.

### 3.2 Rendre la démonstration de complexité plus rigoureuse

La partie complexité est bonne, mais elle peut encore être renforcée.

À améliorer :

- distinguer explicitement **problème d'optimisation** et **problème de décision** ;
- préciser que la réduction montre au minimum la **NP-difficulté** ;
- si vous voulez être très propre théoriquement, expliciter les conditions pour parler de **NP-complétude** de la version décisionnelle.

Aujourd'hui, cette partie est suffisante pour la macro-grille, mais elle peut être rendue plus académique.

### 3.3 Mieux justifier certains paramètres expérimentaux

Les paramètres sont donnés, mais leur justification peut être encore plus défendue.

À expliciter davantage :

- pourquoi `100 x 100` pour la zone ;
- pourquoi des demandes entre `1` et `10` ;
- pourquoi ces valeurs de `capacity_tightness` ;
- pourquoi `15 / 25 / 35 / 45` pour la première campagne ;
- pourquoi `20 / 50 / 100` puis `400 / 1000` pour les stress tests.

Le notebook est déjà correct sur ce point, mais une justification plus explicite améliorera la crédibilité du protocole.

### 3.4 Bien distinguer "meilleur solveur du panel" et "optimum réel"

Le notebook utilise des métriques du type `gap_to_best_pct`.

C'est utile, mais il faut toujours rappeler clairement que :

- le "meilleur" est ici **le meilleur solveur testé** ;
- ce n'est **pas** la distance à l'optimum mathématique global ;
- sans solveur exact ou borne inférieure, on ne connaît pas l'écart réel à l'optimum.

Cette nuance apparaît partiellement dans le notebook, mais elle mérite d'être encore davantage mise en avant.

### 3.5 Nettoyer la section des stress tests

C'est la zone la plus perfectible du notebook.

Les stress tests sont intéressants, mais la narration comporte plusieurs incohérences :

- une section parle de **1000 clients** alors qu'une cellule précédente montre un test à **400 clients** ;
- le texte indique à un moment que "la taille des clients a été remise à 10", alors que le code et les sorties affichent **1000** ;
- le texte affirme que certaines métaheuristiques ont été interrompues, mais le code final présenté ne les exécute plus dans ce test extrême.

En l'état, le lecteur comprend l'idée générale, mais peut douter de la rigueur exacte du récit expérimental.

Cette partie doit être harmonisée avant rendu final.

### 3.6 Rejouer le notebook intégralement avant rendu

Le notebook a manifestement été exécuté en plusieurs temps, ce qui est normal en phase de travail.

En revanche, avant rendu final, il faut absolument :

- faire un **Run All** ;
- vérifier que tout s'exécute dans l'ordre ;
- s'assurer que les sorties correspondent bien au code affiché ;
- éviter toute cellule contradictoire ou obsolète.

C'est un point essentiel pour la crédibilité du livrable.

### 3.7 Renforcer l'analyse critique du 2-opt

Le 2-opt est bien ajouté, mais dans les résultats il améliore parfois peu, voire pas du tout, certaines solutions Clarke-Wright.

Ce n'est pas un défaut, au contraire : c'est une observation intéressante.

Il faudrait simplement mieux l'expliquer :

- pourquoi le gain est faible sur certaines instances ;
- dans quels cas il devient utile ;
- pourquoi il semble plus profitable après certaines heuristiques qu'après d'autres.

### 3.8 Lisser quelques formulations et petites fautes

Le niveau rédactionnel est globalement bon, mais une dernière passe est recommandée :

- accords ;
- répétitions ;
- ponctuation ;
- homogénéité des termes (`Recherche tabou` / `Recherche Tabou`, `Clarke & Wright` / `Clarke-Wright`, etc.).

Ce sont des détails, mais ils comptent à l'impression générale.

## 4. Évaluation détaillée par exigence

| Exigence du sujet | État actuel | Évaluation |
|---|---|---|
| Modélisation formelle du problème | Présente | Bien traitée |
| Analyse de complexité | Présente | Bonne, à rendre encore plus rigoureuse |
| Génération d'instances aléatoires | Présente | Bien traitée |
| Au moins deux méthodes de résolution | Présente | Très bien, largement au-dessus du minimum |
| Étude statistique expérimentale | Présente | Bien traitée |
| Ajout d'au moins deux contraintes | Présente | Conforme |
| Références bibliographiques | Présentes | Bon point |
| Lisibilité / storytelling | Présent | Bon niveau |
| Robustesse / validation des solutions | Présente | Très bon point |
| Cohérence finale du document | Partiellement stabilisée | À nettoyer avant rendu |

## 5. Ce qui est encore à faire avant de considérer le projet comme "sécurisé"

Si l'objectif est d'arriver à un rendu final très propre, voici l'ordre de priorité recommandé.

### Priorité 1

- harmoniser les sections de stress test ;
- supprimer les contradictions texte / code / résultats ;
- relancer le notebook de haut en bas.

### Priorité 2

- renforcer la partie complexité avec la version décisionnelle ;
- préciser davantage la justification des paramètres expérimentaux ;
- mieux rappeler que les écarts sont relatifs au meilleur solveur testé et non à l'optimum exact.

### Priorité 3

- faire une passe de relecture rédactionnelle ;
- homogénéiser les noms de méthodes ;
- éventuellement condenser certaines répétitions.

## 6. Note estimée selon la macro-grille

### Note proposée : **A**

### Justification

- **Programme fonctionnel** : oui
- **Étude théorique de complexité** : oui
- **Étude statistique** : oui

Le notebook coche donc bien les trois éléments de la ligne `A`.

### Nuance importante

Cette note `A` est une **estimation macro**.

Elle signifie que le projet est aujourd'hui classable dans la meilleure catégorie de la grille simplifiée.

En revanche, à l'intérieur de cette catégorie, la perception du jury dépendra encore :

- de la propreté finale du notebook ;
- de la cohérence du récit expérimental ;
- de votre capacité à défendre vos choix à l'oral ;
- de la démonstration en soutenance.

Autrement dit :

- **sur la macro-grille, vous êtes déjà au niveau A** ;
- **sur la finesse d'évaluation, il reste des points à polir pour rendre ce A plus solide**.

## 7. Conclusion générale

Le projet est **déjà bien plus qu'un simple livrable de modélisation**. En l'état, il ressemble déjà à un **livrable final crédible** :

- le problème est formalisé ;
- plusieurs algorithmes sont implémentés ;
- l'expérimentation est réelle ;
- les résultats sont interprétés ;
- une conclusion métier est proposée.

Le plus important à ce stade n'est donc plus d'ajouter beaucoup de contenu, mais de **fiabiliser et nettoyer ce qui existe déjà**.

En résumé :

- le fond est bon ;
- la structure est bonne ;
- le niveau est compatible avec une note `A` ;
- les améliorations restantes portent surtout sur la rigueur finale, la cohérence du récit et la qualité du rendu.
