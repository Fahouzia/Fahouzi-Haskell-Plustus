## HC6T8 : Filtrer les nombres pairs
---

##  Objectif

Créer une fonction `filterEven` qui prend une liste d’entiers et retourne **une nouvelle liste contenant uniquement les nombres pairs**.

---

##  Code 

```haskell
-- HC6T8 : Filtrer les nombres pairs

-- Définition de la fonction filterEven
filterEven :: [Int] -> [Int]
filterEven [] = []                             -- Cas de base : liste vide → renvoie []
filterEven (x:xs)
    | x `mod` 2 == 0 = x : filterEven xs      -- Si x est pair, on le garde et on continue
    | otherwise      = filterEven xs          -- Sinon, on ignore x et on continue

-- Fonction principale main pour tester
main :: IO ()
main = do
    let liste = [1,2,3,4,5,6,7,8,9,10]
    let result = filterEven liste
    putStrLn ("Liste originale : " ++ show liste)
    putStrLn ("Nombres pairs : " ++ show result)
```

---

##  Explication pas à pas



## 1️ Signature de la fonction

```haskell
filterEven :: [Int] -> [Int]
```

* `[Int]` → la fonction prend une **liste d’entiers** comme entrée.
* `[Int]` → elle retourne **une liste d’entiers**, contenant uniquement les nombres pairs.
* C’est une fonction **typée**, Haskell sait qu’elle ne fonctionne que sur des entiers.

---

## 2️ Cas de base

```haskell
filterEven [] = []
```

* Ici, on dit : **si la liste est vide**, il n’y a rien à filtrer.
* On renvoie simplement une **liste vide**.
* Le cas de base est **obligatoire** pour que la récursion s’arrête.

---

## 3️ Cas récursif avec gardes

```haskell
filterEven (x:xs)
    | x `mod` 2 == 0 = x : filterEven xs
    | otherwise      = filterEven xs
```

### Explication détaillée

* `(x:xs)` → décomposition de la liste :

  * `x` = **premier élément** (tête)
  * `xs` = **le reste de la liste** (queue)

* `| x \`mod` 2 == 0`→ vérifie si`x` est pair.

  * `mod` = reste de la division.
  * Exemple : `4 mod 2 = 0` → pair, `5 mod 2 = 1` → impair

* Si `x` est pair :

```haskell
x : filterEven xs
```

* On **garde x** (`:` ajoute à la tête de la liste résultat)

* On continue la récursion sur le reste `xs`

* Si `x` est impair :

```haskell
filterEven xs
```

* On **ignore x** et continue la récursion sur `xs`

---

## 4️ Exemple de déroulement

Liste d’entrée : `[1,2,3,4,5]`

1. `x = 1`, impair → on ignore → on fait `filterEven [2,3,4,5]`
2. `x = 2`, pair → on garde → `2 : filterEven [3,4,5]`
3. `x = 3`, impair → on ignore → `filterEven [4,5]`
4. `x = 4`, pair → on garde → `4 : filterEven [5]`
5. `x = 5`, impair → on ignore → `filterEven []`
6. Liste vide → renvoie `[]`
7. On remonte la récursion → `[2,4]`

 Résultat final : `[2,4]`

---

## 5️ Fonction `main`

```haskell
main :: IO ()
main = do
    let liste = [1,2,3,4,5,6,7,8,9,10]
    let result = filterEven liste
    putStrLn ("Liste originale : " ++ show liste)
    putStrLn ("Nombres pairs : " ++ show result)
```

* `let liste = [1..10]` → on définit une liste de 1 à 10
* `let result = filterEven liste` → on applique la fonction pour obtenir uniquement les pairs
* `putStrLn` → affiche les résultats sous forme lisible




