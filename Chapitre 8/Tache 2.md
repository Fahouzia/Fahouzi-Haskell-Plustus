**HC8T2 – Types personnalisés et constructeurs de données**
---

##  Objectif

1. Créer un **type `PaymentMethod`** avec trois options :

   * `Cash`
   * `Card`
   * `Cryptocurrency`

2. Créer un **type `Person`** comprenant :

   * `name` : `String`
   * `address` : `(String, Int)` → exemple : (rue, numéro)
   * `payment` : `PaymentMethod`

3. Créer un objet `bob` qui paie en **espèces (`Cash`)**.

---

##  Code complet (copiable)

```haskell
-- HC8T2 : Types personnalisés et constructeurs de données

-- Définition du type PaymentMethod
data PaymentMethod = Cash | Card | Cryptocurrency
    deriving (Show)

-- Définition du type Person
data Person = Person
    { name    :: String
    , address :: (String, Int)
    , payment :: PaymentMethod
    } deriving (Show)

-- Création d'une personne : Bob paie en espèces
bob :: Person
bob = Person
    { name = "Bob"
    , address = ("Rue Principale", 42)
    , payment = Cash
    }

-- Fonction principale main pour tester
main :: IO ()
main = do
    putStrLn ("Nom : " ++ name bob)
    putStrLn ("Adresse : " ++ show (address bob))
    putStrLn ("Méthode de paiement : " ++ show (payment bob))
```

---

##  Explication pas à pas

### 1️⃣ Type `PaymentMethod`

```haskell
data PaymentMethod = Cash | Card | Cryptocurrency
    deriving (Show)
```

* `Cash`, `Card` et `Cryptocurrency` sont **les constructeurs du type**.
* `Show` permet d’afficher la méthode de paiement facilement.

---

### 2️⃣ Type `Person`

```haskell
data Person = Person
    { name    :: String
    , address :: (String, Int)
    , payment :: PaymentMethod
    } deriving (Show)
```

* `Person` est défini avec **des champs nommés** :

  * `name` : nom de la personne
  * `address` : un tuple `(rue, numéro)`
  * `payment` : méthode de paiement (`PaymentMethod`)
* `Show` permet d’afficher directement un `Person`.

---

### 3️⃣ Création d’un objet `bob`

```haskell
bob :: Person
bob = Person
    { name = "Bob"
    , address = ("Rue Principale", 42)
    , payment = Cash
    }
```

* Bob a pour nom `"Bob"`, habite `"Rue Principale" 42` et paie en **espèces**.

---

### 4️⃣ Fonction `main` pour tester

```haskell
main :: IO ()
main = do
    putStrLn ("Nom : " ++ name bob)
    putStrLn ("Adresse : " ++ show (address bob))
    putStrLn ("Méthode de paiement : " ++ show (payment bob))
```

* On affiche chaque champ de `bob`.
* `show` convertit `address` (tuple) et `payment` en chaîne.

---

###  Exemple de sortie

```
Nom : Bob
Adresse : ("Rue Principale",42)
Méthode de paiement : Cash
```

---

