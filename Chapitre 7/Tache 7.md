 **HC7T7 – Utiliser `Bounded` et `Enum`**

## Objectif

* Créer une fonction `nextColor` qui prend une couleur et retourne **la couleur suivante** :

  ```
  Red -> Green -> Blue -> Red -> ...
  ```
* Utiliser **`Enum`** pour l’ordre et **`Bounded`** pour connaître la première et la dernière couleur.

---

## Code

```haskell
-- HC7T7 : Utiliser Bounded et Enum

-- Définition du type Color avec Enum et Bounded
data Color = Red | Green | Blue
    deriving (Show, Eq, Enum, Bounded)

-- Définition de la fonction nextColor
nextColor :: Color -> Color
nextColor c
    | c == maxBound = minBound  -- Si c est la dernière couleur, revenir à la première
    | otherwise     = succ c    -- Sinon, passer à la suivante

-- Fonction principale main pour tester
main :: IO ()
main = do
    let c1 = Red
    let c2 = Green
    let c3 = Blue

    putStrLn ("Next color after " ++ show c1 ++ " : " ++ show (nextColor c1))
    putStrLn ("Next color after " ++ show c2 ++ " : " ++ show (nextColor c2))
    putStrLn ("Next color after " ++ show c3 ++ " : " ++ show (nextColor c3))
```

---

##  Explication pas à pas

### 1️⃣ Définition du type

```haskell
data Color = Red | Green | Blue
    deriving (Show, Eq, Enum, Bounded)
```

* `Show` → pour pouvoir afficher la couleur
* `Eq` → pour comparer les couleurs (`==`)
* `Enum` → permet d’utiliser `succ` (successeur) et `pred` (prédécesseur)
* `Bounded` → permet de connaître la **première (`minBound`)** et la **dernière (`maxBound`)** valeur

---

### 2️⃣ Fonction `nextColor`

```haskell
nextColor :: Color -> Color
nextColor c
    | c == maxBound = minBound  -- Si c est la dernière couleur, revenir à la première
    | otherwise     = succ c    -- Sinon, passer à la suivante
```

* `succ c` → retourne la couleur **suivante dans l’ordre** défini par `Enum`

* `maxBound` → dernière couleur (`Blue`)

* `minBound` → première couleur (`Red`)

* Exemple :

  * `nextColor Red → Green`
  * `nextColor Green → Blue`
  * `nextColor Blue → Red`

---

### 3️⃣ Fonction `main` (tests)

```haskell
main :: IO ()
main = do
    let c1 = Red
    let c2 = Green
    let c3 = Blue

    putStrLn ("Next color after " ++ show c1 ++ " : " ++ show (nextColor c1))
    putStrLn ("Next color after " ++ show c2 ++ " : " ++ show (nextColor c2))
    putStrLn ("Next color after " ++ show c3 ++ " : " ++ show (nextColor c3))
```

* Teste chaque couleur et affiche la suivante
* Vérifie que `Blue` revient bien à `Red`

---

###  Exemple de sortie

```
Next color after Red : Green
Next color after Green : Blue
Next color after Blue : Red
```

---

 **Remarque**

* L’association **Enum + Bounded** est très pratique pour créer des cycles sur des types énumérés.
* On peut facilement l’étendre à plus de couleurs ou d’autres types avec le même principe.

---

