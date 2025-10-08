**HC7T9 – Définir une classe de type avec plusieurs instances**

## Objectif

Créer une **classe de type** `Describable` avec une méthode `describe`,
et l’implémenter pour deux types :

* `Bool`
* `Shape` (le type défini précédemment)

---

##  Code
```haskell
-- HC7T9 : Définir une classe de type avec plusieurs instances

-- Définition du type Shape
data Shape = Circle Double | Rectangle Double Double
    deriving (Show, Read)

-- Définition de la classe de type Describable
class Describable a where
    describe :: a -> String

-- Instance pour Bool
instance Describable Bool where
    describe True  = "C'est vrai "
    describe False = "C'est faux "

-- Instance pour Shape
instance Describable Shape where
    describe (Circle r) =
        "Cercle de rayon " ++ show r
    describe (Rectangle l w) =
        "Rectangle de longueur " ++ show l ++ " et de largeur " ++ show w

-- Fonction main pour tester
main :: IO ()
main = do
    -- Test avec Bool
    putStrLn (describe True)
    putStrLn (describe False)

    -- Test avec Shape
    let s1 = Circle 3.5
    let s2 = Rectangle 4.0 6.0

    putStrLn (describe s1)
    putStrLn (describe s2)
```

---

##  Explication pas à pas

### 1️⃣ Définir un type `Shape`

```haskell
data Shape = Circle Double | Rectangle Double Double
    deriving (Show, Read)
```

* `Shape` peut être :

  * un **cercle** (avec un rayon)
  * un **rectangle** (avec longueur et largeur)
* `Show` permet d’afficher la valeur
* `Read` permet de lire à partir d’une chaîne (`"Circle 3.5"` → `Circle 3.5`)

---

### 2️⃣ Créer la classe de type `Describable`

```haskell
class Describable a where
    describe :: a -> String
```

➡️ Une **classe de type** en Haskell est comme une interface (ou un contrat).
Elle déclare **ce que les types doivent implémenter**.

Ici, tout type `a` qui appartient à `Describable` doit fournir une fonction :

```haskell
describe :: a -> String
```

qui **retourne une description textuelle** de la valeur.

---

### 3️⃣ Créer l’instance pour `Bool`

```haskell
instance Describable Bool where
    describe True  = "C'est vrai "
    describe False = "C'est faux "
```

* On indique comment décrire les valeurs `True` et `False`.
* Chaque type peut avoir sa propre logique de description.

---

### 4️⃣ Créer l’instance pour `Shape`

```haskell
instance Describable Shape where
    describe (Circle r) =
        "Cercle de rayon " ++ show r
    describe (Rectangle l w) =
        "Rectangle de longueur " ++ show l ++ " et de largeur " ++ show w
```

* On fait du **pattern matching** :

  * Si la forme est un `Circle`, on affiche le rayon.
  * Si c’est un `Rectangle`, on affiche longueur et largeur.

---

### 5️⃣ Fonction `main`

```haskell
main :: IO ()
main = do
    putStrLn (describe True)
    putStrLn (describe False)

    let s1 = Circle 3.5
    let s2 = Rectangle 4.0 6.0

    putStrLn (describe s1)
    putStrLn (describe s2)
```

* Teste la fonction `describe` sur :

  * des valeurs `Bool`
  * des objets `Shape`

---

##  Exemple de sortie

```
C'est vrai 
C'est faux 
Cercle de rayon 3.5
Rectangle de longueur 4.0 et de largeur 6.0
```

---



| Type    | Valeur          | Résultat de `describe`                        |
| ------- | --------------- | --------------------------------------------- |
| `Bool`  | `True`          | "C'est vrai ✅"                                |
| `Bool`  | `False`         | "C'est faux ❌"                                |
| `Shape` | `Circle 3.5`    | "Cercle de rayon 3.5"                         |
| `Shape` | `Rectangle 4 6` | "Rectangle de longueur 4.0 et de largeur 6.0" |

---
