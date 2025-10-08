HC6T3 – Somme des éléments avec `foldr`
---

Objectif

Créer une fonction `sumList` qui utilise **`foldr`** pour calculer la **somme de tous les éléments d’une liste**.

---

Code 

```haskell
-- HC6T3 : Somme des éléments avec foldr

-- Définition de la fonction sumList
sumList :: [Int] -> Int
sumList xs = foldr (+) 0 xs

-- Fonction principale main pour tester
main :: IO ()
main = do
    let liste = [1, 2, 3, 4, 5]
    let resultat = sumList liste
    putStrLn ("La somme des éléments de la liste " ++ show liste ++ " est : " ++ show resultat)
```

---

### Explication pas à pas

#### 1. Comprendre `foldr`

`foldr` signifie **fold right** (réduction vers la droite).
Sa forme générale est :

```haskell
foldr fonction valeur_initiale liste
```
 Il **applique récursivement** la fonction donnée à chaque élément **de droite à gauche**, en accumulant un résultat.

---

#### 2. Notre cas : additionner les éléments

Ici, on veut additionner tous les éléments d’une liste.
La fonction qu’on applique est donc `(+)`, et la valeur initiale (accumulateur de départ) est `0`.

```haskell
foldr (+) 0 [1,2,3,4,5]
```

Le calcul se déroule ainsi :

```
1 + (2 + (3 + (4 + (5 + 0))))
```

Résultat final → `15`.

---

#### 3. Définition de la fonction

```haskell
sumList :: [Int] -> Int
sumList xs = foldr (+) 0 xs
```

* `sumList` prend une **liste d’entiers** (`[Int]`)
* Elle retourne un **entier** (`Int`)
* On utilise `foldr` pour accumuler la somme.

---

#### 4. La fonction `main`

```haskell
main :: IO ()
main = do
    let liste = [1, 2, 3, 4, 5]
    let resultat = sumList liste
    putStrLn ("La somme des éléments de la liste " ++ show liste ++ " est : " ++ show resultat)
```

* On définit une liste `[1,2,3,4,5]`
* On appelle `sumList` sur cette liste.
* On affiche le résultat avec `putStrLn`.

---

###  Exemple de sortie

```
La somme des éléments de la liste [1,2,3,4,5] est : 15
```

---
