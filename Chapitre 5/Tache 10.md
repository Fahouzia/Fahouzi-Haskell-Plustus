HC5T10 : Combiner les fonctions d’ordre supérieur
---

```haskell
-- Déclaration du type
checkSquare :: (Num a, Ord a) => [a] -> Bool

-- Définition de la fonction
checkSquare xs = any (>50) (filter (>0) (map (^2) xs))

-- Exemple d'utilisation
main :: IO ()
main = do
    print (checkSquare [5,6,7])   -- False
    print (checkSquare [5,8,3])   -- True
    print (checkSquare [1,2,3])   -- False
```

### Explication :

1. `map (^2) xs` → met chaque élément au carré.
2. `filter (>0)` → garde les éléments positifs (optionnel ici, juste pour montrer `filter`).
3. `any (>50)` → vérifie si **au moins un élément est supérieur à 50**.

---


## 1️ Objectif

* Entrée : une liste de nombres `[a]`.
* Étape 1 : **Mettre chaque élément au carré** → `map (^2)`.
* Étape 2 : **Garder uniquement ceux supérieurs à 50** → `filter (>50)`.
* Étape 3 : **Vérifier s’il y a au moins un élément** → `any` ou `not . null`.

---

##  la fonction

```haskell
checkSquare :: (Num a, Ord a) => [a] -> Bool
checkSquare xs = any (>50) (map (^2) xs)
```

### Explication :

1. `map (^2) xs`

   * Met au carré chaque élément de la liste.
   * Exemple : `[5,8,3]` → `[25,64,9]`.

2. `any (>50)`

   * Vérifie si **au moins un élément** de la liste est supérieur à 50.
   * Exemple : `[25,64,9]` → `True` (64 > 50).

3. Combinaison : `any (>50) (map (^2) xs)`

   * Applique d’abord `map (^2)` puis vérifie avec `any (>50)`.

---

## 3️ Exemple d’utilisation

```haskell
checkSquare [5,6,7]   -- 5^2=25, 6^2=36, 7^2=49 → aucun >50 → False
checkSquare [5,8,3]   -- 8^2=64 >50 → True
checkSquare [1,2,3]   -- aucun >50 → False
```

---

**Remarque :** On pourrait aussi utiliser `filter` mais ici `any` suffit pour vérifier l’existence.
