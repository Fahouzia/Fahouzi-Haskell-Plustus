 **HC8T3 – Types algébriques et fonctions**
---

##  Objectif

1. Définir un **type algébrique `Shape`** :

   * `Circle Float` → rayon
   * `Rectangle Float Float` → longueur et largeur

2. Créer une fonction :

```haskell
area :: Shape -> Float
```

qui calcule l’**aire** de la forme.

3. Tester avec :

* `Circle 5` → aire du cercle
* `Rectangle 10 5` → aire du rectangle

---

## Code 

```haskell
-- HC8T3 : Types algébriques et fonction area

-- Définition du type Shape
data Shape = Circle Float | Rectangle Float Float
    deriving (Show)

-- Fonction pour calculer l'aire
area :: Shape -> Float
area (Circle r)       = pi * r * r
area (Rectangle l w)  = l * w

-- Fonction principale main pour tester
main :: IO ()
main = do
    let c = Circle 5
    let r = Rectangle 10 5

    putStrLn ("Aire du cercle (rayon 5) : " ++ show (area c))
    putStrLn ("Aire du rectangle (10 x 5) : " ++ show (area r))
```

---

##  Explication pas à pas

### 1️ Définition du type `Shape`

```haskell
data Shape = Circle Float | Rectangle Float Float
```

* `Circle Float` → cercle avec **rayon** `Float`

* `Rectangle Float Float` → rectangle avec **longueur** et **largeur** `Float`

* `deriving (Show)` → permet d’afficher facilement la valeur.

---

### 2️ Définition de la fonction `area`

```haskell
area :: Shape -> Float
area (Circle r)       = pi * r * r
area (Rectangle l w)  = l * w
```

* On utilise **pattern matching** pour déterminer le constructeur :

  * `Circle r` → aire = π × r²
  * `Rectangle l w` → aire = l × w

* `pi` est la constante π intégrée dans Haskell.

---

### 3️ Fonction `main` pour tester

```haskell
main :: IO ()
main = do
    let c = Circle 5
    let r = Rectangle 10 5

    putStrLn ("Aire du cercle (rayon 5) : " ++ show (area c))
    putStrLn ("Aire du rectangle (10 x 5) : " ++ show (area r))
```

* On crée un **cercle de rayon 5**
* On crée un **rectangle de 10 x 5**
* On affiche les **aires calculées**

---


###  Exemple de sortie

```
Aire du cercle (rayon 5) : 78.53982
Aire du rectangle (10 x 5) : 50.0
```

---

---

##  1. Définir le type algébrique `Shape`

```haskell
data Shape = Circle Float | Rectangle Float Float
    deriving (Show)
```


* **`data`** : sert à définir un **nouveau type de données** en Haskell.
* **`Shape`** : c’est le **nom du type** (comme un "modèle" de forme géométrique).
* **`Circle Float`** : un **constructeur** de type `Shape` qui représente un cercle, et qui prend **un argument** `Float` (le rayon).
* **`Rectangle Float Float`** : un **constructeur** de type `Shape` qui représente un rectangle, et qui prend **deux arguments** `Float` (la longueur et la largeur).
* **`deriving (Show)`** : permet d’utiliser `show` sur les valeurs de ce type, c’est-à-dire de les afficher sous forme de texte.

### Exemple :

```haskell
Circle 5        -- représente un cercle de rayon 5
Rectangle 10 5  -- représente un rectangle 10x5
```

Sans `deriving (Show)`, tu ne pourrais pas afficher ces valeurs avec `print` ou `show`.

---

##  2. Définir la fonction `area`

```haskell
area :: Shape -> Float
area (Circle r)       = pi * r * r
area (Rectangle l w)  = l * w
```

###  Décomposition :

* **`area :: Shape -> Float`**
  Cette ligne indique le **type** de la fonction :

  * Elle prend un **argument de type `Shape`**
  * Elle retourne un **`Float`** (le résultat de l’aire).

---

### Pattern Matching (appariement de formes)

Haskell va regarder **quel constructeur** de `Shape` est utilisé, et exécuter la ligne correspondante.

#### Cas 1 : un cercle

```haskell
area (Circle r) = pi * r * r
```

* Si la valeur est un `Circle`, Haskell récupère le rayon `r`.
* Calcule :
  ( \text{Aire} = \pi \times r^2 )

#### Cas 2 : un rectangle

```haskell
area (Rectangle l w) = l * w
```

* Si la valeur est un `Rectangle`, Haskell récupère la **longueur `l`** et la **largeur `w`**.
* Calcule :
  ( \text{Aire} = l \times w )

---

##  3. Fonction `main` (programme principal)

```haskell
main :: IO ()
main = do
    let c = Circle 5
    let r = Rectangle 10 5

    putStrLn ("Aire du cercle (rayon 5) : " ++ show (area c))
    putStrLn ("Aire du rectangle (10 x 5) : " ++ show (area r))
```

###  Explication ligne par ligne :

1. **`main :: IO ()`**

   * Signifie que `main` est une action d’entrée/sortie (IO).
   * En Haskell, toute fonction qui affiche du texte sur l’écran appartient au type `IO`.

2. **`let c = Circle 5`**

   * On crée une variable `c` qui représente un cercle de rayon 5.

3. **`let r = Rectangle 10 5`**

   * On crée une variable `r` qui représente un rectangle de 10 x 5.

4. **`putStrLn`**

   * Affiche une chaîne de caractères suivie d’un saut de ligne.

5. **`show (area c)`**

   * `area c` calcule l’aire du cercle.
   * `show` convertit le résultat (un nombre `Float`) en texte pour pouvoir le concaténer avec la chaîne.

6. **`"Aire du cercle (rayon 5) : " ++ show (area c)`**

   * Concatène du texte et la valeur calculée, par exemple :

     ```
     Aire du cercle (rayon 5) : 78.53982
     ```

---

## 🧾 Résultat final dans le terminal

```
Aire du cercle (rayon 5) : 78.53982
Aire du rectangle (10 x 5) : 50.0
```

---


| Élément      | Description                                    |
| ------------ | ---------------------------------------------- |
| `data Shape` | Définit un type de formes (cercle, rectangle)  |
| `area`       | Calcule l’aire selon le type de forme          |
| `main`       | Crée deux formes et affiche leurs aires        |
| `pi`         | Constante intégrée de Haskell (3.141592653...) |
| `show`       | Convertit un nombre en texte                   |
| `++`         | Concaténation de chaînes                       |

---

