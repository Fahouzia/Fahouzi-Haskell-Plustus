**HC7T10 – Fonction avec plusieurs contraintes de classes de types**.

##  Objectif

Créer une fonction :

```haskell
describeAndCompare :: (Describable a, Ord a) => a -> a -> String
```

 Elle prend **deux valeurs** qui :

* peuvent être **comparées** (`Ord`)
* peuvent être **décrites** (`Describable`)

et retourne **la description de la plus grande** valeur.

---

##  Code 

```haskell

-- Définition du type Shape
data Shape = Circle Double | Rectangle Double Double
    deriving (Show, Read, Eq, Ord)

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

-- Fonction avec plusieurs contraintes
describeAndCompare :: (Describable a, Ord a) => a -> a -> String
describeAndCompare x y =
    if x >= y
        then "La plus grande valeur est : " ++ describe x
        else "La plus grande valeur est : " ++ describe y

-- Fonction main pour tester
main :: IO ()
main = do
    -- Test avec Bool
    putStrLn (describeAndCompare True False)
    putStrLn (describeAndCompare False True)

    -- Test avec Shape
    let s1 = Circle 3.0
    let s2 = Rectangle 2.0 5.0

    putStrLn (describeAndCompare s1 s2)
```

---

##  Explication pas à pas

### 1️⃣ Type `Shape`

```haskell
data Shape = Circle Double | Rectangle Double Double
    deriving (Show, Read, Eq, Ord)
```

* `Eq` : pour pouvoir tester l’égalité
* `Ord` : pour pouvoir comparer les formes (`>`, `<`, `>=`, etc.)
* La dérivation automatique d’`Ord` compare les constructeurs dans l’ordre de leur définition (`Circle` < `Rectangle`).

---

### 2️⃣ Classe `Describable`

```haskell
class Describable a where
    describe :: a -> String
```

➡️ Tout type appartenant à cette classe doit définir une fonction `describe`.

---

### 3️⃣ Instances `Describable` pour `Bool` et `Shape`

```haskell
instance Describable Bool where
    describe True  = "C'est vrai "
    describe False = "C'est faux "

instance Describable Shape where
    describe (Circle r) = "Cercle de rayon " ++ show r
    describe (Rectangle l w) = "Rectangle de longueur " ++ show l ++ " et de largeur " ++ show w
```

---

### 4️⃣ Fonction `describeAndCompare`

```haskell
describeAndCompare :: (Describable a, Ord a) => a -> a -> String
```

* `(Describable a, Ord a)` → le type `a` doit être **à la fois** :

  * comparable (`Ord`)
  * descriptible (`Describable`)

```haskell
describeAndCompare x y =
    if x >= y
        then "La plus grande valeur est : " ++ describe x
        else "La plus grande valeur est : " ++ describe y
```

➡️ On compare les deux valeurs `x` et `y`, puis on affiche la description de la plus grande.

---

### 5️⃣ Fonction `main`

```haskell
main :: IO ()
main = do
    putStrLn (describeAndCompare True False)
    putStrLn (describeAndCompare False True)

    let s1 = Circle 3.0
    let s2 = Rectangle 2.0 5.0

    putStrLn (describeAndCompare s1 s2)
```

* On teste la fonction sur :

  * des `Bool`
  * des `Shape`

---

##  Exemple de sortie

```
La plus grande valeur est : C'est vrai 
La plus grande valeur est : C'est vrai 
La plus grande valeur est : Rectangle de longueur 2.0 et de largeur 5.0
```

---

## 

| Type  | x          | y                 | Résultat                                        |
| ----- | ---------- | ----------------- | ----------------------------------------------- |
| Bool  | True       | False             | `"C'est vrai "`                                |
| Shape | Circle 3.0 | Rectangle 2.0 5.0 | `"Rectangle de longueur 2.0 et de largeur 5.0"` |

---

