HC8T5 : Syntaxe d’enregistrement pour Person
---

##  Code

```haskell
-- 

-- Définition du type Person avec syntaxe d’enregistrement
data Person = Person
    { name :: String
    , age :: Int
    , isEmployed :: Bool
    } deriving (Show)

-- Fonction principale
main :: IO ()
main = do
    -- Création de deux personnes
    let person1 = Person { name = "Alice", age = 28, isEmployed = True }
    let person2 = Person { name = "Bob", age = 35, isEmployed = False }

    -- Affichage des informations pour person1
    putStrLn "=== Personne 1 ==="
    putStrLn ("Nom : " ++ name person1)
    putStrLn ("Âge : " ++ show (age person1))
    putStrLn ("Employé ? " ++ show (isEmployed person1))

    -- Affichage des informations pour person2
    putStrLn "\n=== Personne 2 ==="
    putStrLn ("Nom : " ++ name person2)
    putStrLn ("Âge : " ++ show (age person2))
    putStrLn ("Employé ? " ++ show (isEmployed person2))

    -- Affichage complet avec deriving Show
    putStrLn "\n=== Affichage brut ==="
    print person1
    print person2
```

---

##  Explication

### 1️⃣ Définition du type `Person`

```haskell
data Person = Person
    { name :: String
    , age :: Int
    , isEmployed :: Bool
    } deriving (Show)
```



* `data Person = Person` → définit un **nouveau type de données** appelé `Person`.
  Le mot `Person` après `=` est le **constructeur** (il crée une valeur du type `Person`).

* `{ name :: String, age :: Int, isEmployed :: Bool }`
  → ce sont les **champs nommés** :

  * `name` : le nom de la personne, de type `String`.
  * `age` : l’âge de la personne, de type `Int`.
  * `isEmployed` : indique si la personne est employée (`True` ou `False`).

* `deriving (Show)` → permet d’afficher directement la structure avec `print`.

---

### 2️⃣ Création de deux personnes

```haskell
let person1 = Person { name = "Alice", age = 28, isEmployed = True }
let person2 = Person { name = "Bob", age = 35, isEmployed = False }
```

* `Person { ... }` utilise la **syntaxe d’enregistrement** pour nommer explicitement les champs.
* `person1` → est employée (`True`)
* `person2` → est sans emploi (`False`)

---

### 3️⃣ Accès aux champs


#### Texte personnalisé :

```haskell
putStrLn ("Nom : " ++ name person1)
```

Affiche :

```
Nom : Alice
```

#### Conversion avec `show` :

```haskell
show (age person1)
```

→ convertit `28` en `"28"` (chaîne).

#### Affichage direct de l’objet :

```haskell
print person1
```

→ grâce à `deriving (Show)`, on obtient :

```
Person {name = "Alice", age = 28, isEmployed = True}
```

---

## 🧾 Sortie attendue dans le terminal

```
=== Personne 1 ===
Nom : Alice
Âge : 28
Employé ? True

=== Personne 2 ===
Nom : Bob
Âge : 35
Employé ? False

=== Affichage brut ===
Person {name = "Alice", age = 28, isEmployed = True}
Person {name = "Bob", age = 35, isEmployed = False}
```

---


| Élément                                              | Description                                    |
| ---------------------------------------------------- | ---------------------------------------------- |
| `data Person = Person { ... }`                       | Déclare un type avec des champs nommés         |
| `name`, `age`, `isEmployed`                          | Fonctions automatiques pour accéder aux champs |
| `deriving (Show)`                                    | Permet d’afficher directement une valeur       |
| `Person { name = ..., age = ..., isEmployed = ... }` | Crée une personne                              |
| `True` / `False`                                     | Booléens indiquant si la personne est employée |

---
