HC8T6 : Syntaxe d’enregistrement pour variantes Shape
##  Code 

```haskell
-- 

-- Définition du type Shape avec la syntaxe d’enregistrement
data Shape
    = Circle { center :: (Float, Float), color :: String, radius :: Float }
    | Rectangle { width :: Float, height :: Float, color :: String }
    deriving (Show)

-- Fonction principale
main :: IO ()
main = do
    -- Création d’un cercle et d’un rectangle
    let circle1 = Circle { center = (0.0, 0.0), color = "Red", radius = 5.5 }
    let rectangle1 = Rectangle { width = 10.0, height = 6.0, color = "Blue" }

    -- Affichage des informations du cercle
    putStrLn "=== Cercle ==="
    putStrLn ("Centre : " ++ show (center circle1))
    putStrLn ("Couleur : " ++ color circle1)
    putStrLn ("Rayon : " ++ show (radius circle1))

    -- Affichage des informations du rectangle
    putStrLn "\n=== Rectangle ==="
    putStrLn ("Largeur : " ++ show (width rectangle1))
    putStrLn ("Hauteur : " ++ show (height rectangle1))
    putStrLn ("Couleur : " ++ color rectangle1)

    -- Affichage complet grâce à deriving (Show)
    putStrLn "\n=== Affichage brut ==="
    print circle1
    print rectangle1
```

---

##  Explication pas à pas

### 1️⃣ Définition du type `Shape`

```haskell
data Shape
    = Circle { center :: (Float, Float), color :: String, radius :: Float }
    | Rectangle { width :: Float, height :: Float, color :: String }
    deriving (Show)
```

#### 🔍 Détails :

* **`data Shape`** → création d’un **type de données algébrique** nommé `Shape`.
* **`=`** → indique les différentes **formes possibles** d’un `Shape`.
* Il y a **deux constructeurs** :

  1. **`Circle`** : représente un cercle.
  2. **`Rectangle`** : représente un rectangle.

---

### 2️⃣ Syntaxe d’enregistrement (Record Syntax)

La **syntaxe d’enregistrement** (`{ champ :: type, ... }`) permet :

* de nommer chaque champ,
* d’accéder aux champs facilement,
* et d’éviter de confondre les arguments.

---

####  Pour le cercle :

```haskell
Circle
    { center :: (Float, Float)
    , color :: String
    , radius :: Float
    }
```

→ Champs :

| Champ    | Type             | Signification         |
| -------- | ---------------- | --------------------- |
| `center` | `(Float, Float)` | coordonnées du centre |
| `color`  | `String`         | couleur du cercle     |
| `radius` | `Float`          | rayon du cercle       |

---

####  Pour le rectangle :

```haskell
Rectangle
    { width :: Float
    , height :: Float
    , color :: String
    }
```

→ Champs :

| Champ    | Type     | Signification        |
| -------- | -------- | -------------------- |
| `width`  | `Float`  | largeur              |
| `height` | `Float`  | hauteur              |
| `color`  | `String` | couleur du rectangle |

---

### 3️⃣ Création d’instances

#### Cercle :

```haskell
let circle1 = Circle { center = (0.0, 0.0), color = "Red", radius = 5.5 }
```

* Centre : `(0, 0)`
* Couleur : `"Red"`
* Rayon : `5.5`

#### Rectangle :

```haskell
let rectangle1 = Rectangle { width = 10.0, height = 6.0, color = "Blue" }
```

* Largeur : `10`
* Hauteur : `6`
* Couleur : `"Blue"`

---

### 4️⃣ Accès aux champs

Haskell crée automatiquement **des fonctions d’accès** :

| Champ    | Type de fonction          | Exemple            |
| -------- | ------------------------- | ------------------ |
| `center` | `Shape -> (Float, Float)` | `center circle1`   |
| `color`  | `Shape -> String`         | `color rectangle1` |
| `radius` | `Shape -> Float`          | `radius circle1`   |
| `width`  | `Shape -> Float`          | `width rectangle1` |

---

### 5️⃣ Affichage

* `putStrLn` → affiche du texte.
* `show` → convertit une valeur (nombre, tuple) en texte.
* `print` → affiche directement la valeur grâce à `deriving (Show)`.

---

##  Résultat attendu dans le terminal

```
=== Cercle ===
Centre : (0.0,0.0)
Couleur : Red
Rayon : 5.5

=== Rectangle ===
Largeur : 10.0
Hauteur : 6.0
Couleur : Blue

=== Affichage brut ===
Circle {center = (0.0,0.0), color = "Red", radius = 5.5}
Rectangle {width = 10.0, height = 6.0, color = "Blue"}
```

---

| Élément                             | Description                                         |                          |
| ----------------------------------- | --------------------------------------------------- | ------------------------ |
| `data Shape = Circle {...}          | Rectangle {...}`                                    | Type avec deux variantes |
| `Record syntax { champ :: type }`   | Permet de nommer et d’accéder facilement aux champs |                          |
| `Circle {...}`                      | Crée un cercle avec ses champs                      |                          |
| `Rectangle {...}`                   | Crée un rectangle avec ses champs                   |                          |
| `deriving (Show)`                   | Permet d’afficher les objets avec `print`           |                          |
| `color circle1`, `width rectangle1` | Accès direct aux champs                             |                          |

---

