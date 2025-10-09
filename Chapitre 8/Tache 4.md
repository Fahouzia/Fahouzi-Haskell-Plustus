 HC8T4 : Syntaxe d’enregistrement pour Employee
---

##  Code 

```haskell
--

-- Définition du type Employee avec la syntaxe d’enregistrement
data Employee = Employee
    { name :: String
    , experienceInYears :: Float
    } deriving (Show)

-- Fonction principale
main :: IO ()
main = do
    -- Création d’un employé nommé richard avec 7,5 ans d’expérience
    let richard = Employee { name = "Richard", experienceInYears = 7.5 }

    -- Affichage des informations
    putStrLn ("Nom : " ++ name richard)
    putStrLn ("Expérience : " ++ show (experienceInYears richard) ++ " ans")

    -- Affichage complet de l’objet (grâce à deriving Show)
    print richard
```

---

## Explication

### 1️⃣ Définition du type `Employee`

```haskell
data Employee = Employee
    { name :: String
    , experienceInYears :: Float
    } deriving (Show)
```

###  Détails :

* **`data Employee = Employee`**
  → On crée un **type de données** appelé `Employee`.
  Le mot juste après `=` (`Employee`) est aussi le **constructeur** (comme une “fonction” qui crée un employé).

* **Syntaxe d’enregistrement (`{ ... }`)**
  On définit les **champs nommés** :

  * `name :: String` → le nom de l’employé.
  * `experienceInYears :: Float` → ses années d’expérience.

* **`deriving (Show)`**
  Permet d’afficher un employé avec `print`, par exemple :

  ```
  Employee {name = "Richard", experienceInYears = 7.5}
  ```

---

### 2️⃣ Création d’un employé

```haskell
let richard = Employee { name = "Richard", experienceInYears = 7.5 }
```

Ici on utilise la **syntaxe d’enregistrement** pour initialiser les champs :

* `name = "Richard"`
* `experienceInYears = 7.5`

Tu peux créer plusieurs employés comme ceci :

```haskell
let alice = Employee { name = "Alice", experienceInYears = 3.0 }
```

---

### 3️⃣ Accès aux champs

Haskell génère automatiquement des **fonctions d’accès** :

* `name richard` → renvoie `"Richard"`
* `experienceInYears richard` → renvoie `7.5`

C’est pour ça qu’on peut écrire :

```haskell
putStrLn ("Nom : " ++ name richard)
```

---

### 4️⃣ Affichage formaté

* `putStrLn` affiche du texte.
* `show` convertit un nombre en chaîne (sinon la concaténation `++` ne marcherait pas).
* `print richard` affiche la structure complète, grâce à `deriving (Show)`.

---

---

| Élément                                                  | Rôle                                   |
| -------------------------------------------------------- | -------------------------------------- |
| `data Employee = ...`                                    | Définit un type avec deux champs       |
| `{ name :: String, experienceInYears :: Float }`         | Syntaxe d’enregistrement               |
| `Employee { name = "Richard", experienceInYears = 7.5 }` | Crée un employé                        |
| `name richard`                                           | Accède au nom                          |
| `experienceInYears richard`                              | Accède à l’expérience                  |
| `deriving (Show)`                                        | Permet d’afficher le type avec `print` |

---
