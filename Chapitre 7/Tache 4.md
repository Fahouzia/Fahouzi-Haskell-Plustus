 **HC7T4 – Type personnalisé avec `Show` et `Read`**

---

##  Objectif

* Définir un **type `Shape`** avec :

  * `Circle Double` → cercle avec un rayon
  * `Rectangle Double Double` → rectangle avec largeur et hauteur
* Implémenter **`Show`** pour afficher le type sous forme lisible
* Implémenter **`Read`** pour pouvoir lire un `Shape` depuis une chaîne de caractères

---

##  Code complet (copiable)

```haskell
-- HC7T4 : Type personnalisé avec Show et Read

import Text.Read (readMaybe)

-- Définition du type Shape
data Shape = Circle Double | Rectangle Double Double

-- Implémentation de Show
instance Show Shape where
    show (Circle r) = "Circle " ++ show r
    show (Rectangle w h) = "Rectangle " ++ show w ++ " " ++ show h

-- Implémentation de Read
instance Read Shape where
    readsPrec _ input =
        case words input of
            ("Circle":r:[]) -> [(Circle (read r), "")]
            ("Rectangle":w:h:[]) -> [(Rectangle (read w) (read h), "")]
            _ -> []

-- Fonction principale main pour tester
main :: IO ()
main = do
    let s1 = Circle 5.0
    let s2 = Rectangle 3.0 4.0

    putStrLn ("Forme 1 : " ++ show s1)
    putStrLn ("Forme 2 : " ++ show s2)

    -- Lire un Shape depuis une chaîne
    let input1 = "Circle 7.5"
    let input2 = "Rectangle 2.0 6.0"

    case readMaybe input1 :: Maybe Shape of
        Just shape -> putStrLn ("Shape lu depuis chaîne : " ++ show shape)
        Nothing -> putStrLn "Erreur lecture Shape 1"

    case readMaybe input2 :: Maybe Shape of
        Just shape -> putStrLn ("Shape lu depuis chaîne : " ++ show shape)
        Nothing -> putStrLn "Erreur lecture Shape 2"
```

---

##  Explication pas à pas

### 1️⃣ Définition du type

```haskell
data Shape = Circle Double | Rectangle Double Double
```

* `Circle r` → cercle avec **rayon `r`**
* `Rectangle w h` → rectangle avec **largeur `w`** et **hauteur `h`**

---

### 2️⃣ Implémentation de Show

```haskell
instance Show Shape where
    show (Circle r) = "Circle " ++ show r
    show (Rectangle w h) = "Rectangle " ++ show w ++ " " ++ show h
```

* `show` transforme un `Shape` en **chaîne lisible**
* Exemple :

  * `show (Circle 5.0) → "Circle 5.0"`
  * `show (Rectangle 3.0 4.0) → "Rectangle 3.0 4.0"`

---

### 3️⃣ Implémentation de Read

```haskell
instance Read Shape where
    readsPrec _ input =
        case words input of
            ("Circle":r:[]) -> [(Circle (read r), "")]
            ("Rectangle":w:h:[]) -> [(Rectangle (read w) (read h), "")]
            _ -> []
```

* `readsPrec` lit une **chaîne de caractères** et retourne une **liste de paires `(valeur, reste)`**
* `words input` → sépare la chaîne en mots
* On teste le premier mot pour savoir si c’est `"Circle"` ou `"Rectangle"`
* `read r` / `read w` / `read h` → convertit la chaîne en `Double`
* `_ -> []` → toutes les autres chaînes → lecture échouée

---

### 4️⃣ Fonction `main` (tests)

* On crée deux `Shape` avec les constructeurs et on affiche avec `show`
* On lit des `Shape` depuis des chaînes avec `readMaybe` (de `Text.Read`)

Exemple :

```haskell
let input1 = "Circle 7.5"
readMaybe input1 :: Maybe Shape
-- Just (Circle 7.5)
```

---

###  Exemple de sortie

```
Forme 1 : Circle 5.0
Forme 2 : Rectangle 3.0 4.0
Shape lu depuis chaîne : Circle 7.5
Shape lu depuis chaîne : Rectangle 2.0 6.0
```

---

 **Remarque**

* Grâce à `Show`, on peut **afficher** le type de manière lisible
* Grâce à `Read`, on peut **reconstruire** le type depuis une chaîne
* `readMaybe` est plus sûr que `read`, car il retourne un `Maybe` au lieu de planter si la chaîne est incorrecte.

---

