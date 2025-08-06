HC1T4 - Tâche 4 : Traitement de liste de joueurs

CODE 
```haskell
import Data.List (sortBy)
import Data.Ord (comparing)

-- 1. extractPlayers : liste de (nom, score) -> liste des noms
extractPlayers :: [(String, Int)] -> [String]
extractPlayers players = [name | (name, _) <- players]
-- Ou avec map : extractPlayers players = map fst players

-- 2. sortByScore : trie la liste par score décroissant
sortByScore :: [(String, Int)] -> [(String, Int)]
sortByScore = sortBy (flip (comparing snd))
-- 'snd' récupère le score, 'comparing snd' crée un comparateur sur le score
-- 'flip' inverse l'ordre pour décroissant

-- 3. topThree : retourne les trois premiers éléments
topThree :: [a] -> [a]
topThree = take 3

-- 4. getTopThreePlayers : compose les fonctions précédentes
getTopThreePlayers :: [(String, Int)] -> [String]
getTopThreePlayers = extractPlayers . topThree . sortByScore

-- Exemple de test
main :: IO ()
main = do
    let players = [("Alice", 50), ("Bob", 75), ("Charlie", 60), ("Diana", 80), ("Eve", 55)]
    print $ getTopThreePlayers players
```

EXPLICATIONS

## 1. `extractPlayers`

* **But :** récupérer la liste des noms uniquement.
* `(String, Int)` : chaque élément est un tuple `(nom, score)`.
* Utilisation de la **compréhension de liste** :

  ```haskell
  [name | (name, _) <- players]
  ```

  Parcourt chaque tuple et prend `name`, ignore `_` (score).
* On peut aussi utiliser `map fst players` car `fst` donne le premier élément du tuple.


### 2. `sortByScore`

*trier par score (2e élément du tuple) de façon décroissante.
* `sortBy` : fonction qui trie selon un comparateur.
* `comparing snd` : crée un comparateur qui regarde la deuxième valeur (`score`) des tuples.
* `flip` inverse l'ordre pour que ce soit décroissant (du plus grand au plus petit).
* Résultat : la liste triée du joueur au plus grand score au plus petit.


### 3. `topThree`

* `take 3` prend les 3 premiers éléments d’une liste.
* Simple et efficace.


### 4. `getTopThreePlayers`

* Compose les fonctions dans l’ordre logique :

  * Trier la liste par score décroissant → `sortByScore`
  * Prendre les 3 premiers → `topThree`
  * Extraire les noms → `extractPlayers`
* En Haskell, la composition de fonctions se fait avec `.` (point), de droite à gauche.
* Donc :

  ```haskell
  getTopThreePlayers = extractPlayers . topThree . sortByScore

LE TRI SE FAIT DE façon decroissante .
