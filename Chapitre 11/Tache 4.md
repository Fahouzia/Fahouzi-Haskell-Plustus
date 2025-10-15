 **HC11T4 : Instance `Container` pour le type `Present`** 

Cet exercice réutilise la **classe de type `Container`** qu’on a créée précédemment,
mais cette fois on l’applique à un **autre type de données** appelé `Present`.

---

## Code

```haskell
-- Définition du type Present
data Present a = NoPresent | Wrap a deriving (Show, Eq)

-- Définition de la classe de type Container
class Container c where
    isEmpty  :: c a -> Bool
    contains :: (Eq a) => c a -> a -> Bool
    replace  :: c a -> a -> c a

-- Instance de Container pour Present
instance Container Present where
    -- Vérifie si le cadeau est vide
    isEmpty NoPresent   = True
    isEmpty (Wrap _)    = False

    -- Vérifie si le cadeau contient une certaine valeur
    contains NoPresent _ = False
    contains (Wrap x) y  = x == y

    -- Remplace le contenu du cadeau (ou l’enveloppe s’il était vide)
    replace NoPresent newVal = Wrap newVal
    replace (Wrap _) newVal  = Wrap newVal

-- Programme principal pour tester
main :: IO ()
main = do
    let p1 = NoPresent
    let p2 = Wrap "Livre"
    putStrLn "=== Test de Container pour Present ==="
    print p1
    print p2

    putStrLn "\n1️⃣ Test de isEmpty :"
    print (isEmpty p1)  -- True
    print (isEmpty p2)  -- False

    putStrLn "\n2️⃣ Test de contains :"
    print (contains p2 "Livre")  -- True
    print (contains p2 "Chaussures")  -- False

    putStrLn "\n3️⃣ Test de replace :"
    print (replace p1 "Peluche")   -- Wrap "Peluche"
    print (replace p2 "Montre")    -- Wrap "Montre"
```

---

##  Explication pas à pas

### 1️⃣ Type `Present`

```haskell
data Present a = NoPresent | Wrap a deriving (Show, Eq)
```

➡️ `Present` est un **type paramétrique**, comme `Box`.
Il peut contenir une valeur (un “cadeau”) ou être vide.

| Constructeur | Signification                              |
| ------------ | ------------------------------------------ |
| `NoPresent`  | aucun cadeau                               |
| `Wrap a`     | un cadeau contenant une valeur de type `a` |

---

### 2️⃣ Classe `Container`

```haskell
class Container c where
    isEmpty  :: c a -> Bool
    contains :: (Eq a) => c a -> a -> Bool
    replace  :: c a -> a -> c a
```

* **isEmpty** : vérifie si le conteneur est vide.
* **contains** : vérifie si le conteneur contient une valeur spécifique (requiert `(Eq a)` pour la comparaison).
* **replace** : remplace la valeur contenue par une nouvelle.

---

### 3️⃣ Instance de `Container` pour `Present`

```haskell
instance Container Present where
    isEmpty NoPresent   = True
    isEmpty (Wrap _)    = False

    contains NoPresent _ = False
    contains (Wrap x) y  = x == y

    replace NoPresent newVal = Wrap newVal
    replace (Wrap _) newVal  = Wrap newVal
```

➡️ **Comportement :**

| Fonction                   | Cas                          | Résultat      |
| -------------------------- | ---------------------------- | ------------- |
| `isEmpty NoPresent`        | cadeau vide                  | `True`        |
| `isEmpty (Wrap _)`         | cadeau emballé               | `False`       |
| `contains (Wrap x) y`      | compare le contenu avec `y`  | `x == y`      |
| `replace NoPresent newVal` | crée un nouveau cadeau       | `Wrap newVal` |
| `replace (Wrap _) newVal`  | remplace le contenu existant | `Wrap newVal` |

---

### 4️⃣ Programme principal

On crée deux cadeaux :

```haskell
let p1 = NoPresent
let p2 = Wrap "Livre"
```

et on teste les trois méthodes de la classe.

---

##  Résultat attendu

```
=== Test de Container pour Present ===
NoPresent
Wrap "Livre"

1️⃣ Test de isEmpty :
True
False

2️⃣ Test de contains :
True
False

3️⃣ Test de replace :
Wrap "Peluche"
Wrap "Montre"
```

---

##  Résumé

| Élément                      | Description                                                     |
| ---------------------------- | --------------------------------------------------------------- |
| `Present a`                  | type représentant un cadeau (vide ou emballé)                   |
| `Container`                  | classe générique avec 3 opérations (isEmpty, contains, replace) |
| `instance Container Present` | implémente le comportement pour les cadeaux                     |
| `main`                       | teste tous les cas possibles                                    |

