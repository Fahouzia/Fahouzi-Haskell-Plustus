HC6T4 : Produit des éléments avec foldl
## Objectif

Créer une fonction `productList` qui calcule le **produit de tous les éléments d’une liste** à l’aide de **`foldl`**.


##Code 

```haskell


-- Définition de la fonction productList
productList :: [Int] -> Int
productList xs = foldl (*) 1 xs

-- Fonction principale main pour tester
main :: IO ()
main = do
    let liste = [1, 2, 3, 4, 5]
    let resultat = productList liste
    putStrLn ("Le produit des éléments de la liste " ++ show liste ++ " est : " ++ show resultat)
```

---

##  Explication pas à pas

### 1. Comprendre `foldl`

`foldl` signifie **fold left** → réduction vers la gauche.
Forme générale :

```haskell
foldl fonction valeur_initiale liste
```

Il applique la fonction **de gauche à droite**, en transportant une valeur accumulée.

---

### 2. Notre cas : multiplier tous les éléments

On veut le produit de tous les éléments d’une liste.
La fonction qu’on applique est donc `( *)` (multiplication),
et la **valeur initiale** (accumulateur de départ) est `1` (neutre de la multiplication).

---

## 3. Exemple de déroulement

```haskell
foldl (*) 1 [1, 2, 3, 4, 5]
```

Se déroule comme ceci :

```
((((1 * 1) * 2) * 3) * 4) * 5
```

→ résultat final = `120`

---

### 4. Définition de la fonction

```haskell
productList :: [Int] -> Int
productList xs = foldl (*) 1 xs
```

* `productList` prend une liste d’entiers `[Int]`
* Elle retourne un entier `Int`
* `foldl` applique `(*)` sur chaque élément en partant de `1`

---

### 5. Fonction `main`

```haskell
main :: IO ()
main = do
    let liste = [1, 2, 3, 4, 5]
    let resultat = productList liste
    putStrLn ("Le produit des éléments de la liste " ++ show liste ++ " est : " ++ show resultat)
```

* On définit une liste `[1, 2, 3, 4, 5]`
* On appelle `productList`
* On affiche le résultat.

---

## 🧾 Exemple de sortie

```
Le produit des éléments de la liste [1,2,3,4,5] est : 120
```

---

###  Différence entre `foldr` et `foldl`

| Fonction | Direction de parcours | Exemple                         |
| -------- | --------------------- | ------------------------------- |
| `foldr`  | Droite → Gauche       | `1 + (2 + (3 + (4 + (5 + 0))))` |
| `foldl`  | Gauche → Droite       | `((((0 + 1) + 2) + 3) + 4) + 5` |

NB:Pour la somme et le produit, le résultat est identique,
mais pour certaines opérations non symétriques, l’ordre change le résultat.

---
