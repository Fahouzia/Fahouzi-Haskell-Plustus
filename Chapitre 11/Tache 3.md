**HC11T3 : la classe de type `Container`**.
---

##  Code

```haskell
{-# LANGUAGE MultiParamTypeClasses #-}
{-# LANGUAGE FlexibleInstances #-}

module Main where

-- Définition du type paramétrique Box
data Box a = Empty | Has a deriving (Show, Eq)

-- Classe multi-paramétrique : Container c a
class Container c a where
    isEmpty  :: c a -> Bool
    contains :: c a -> a -> Bool
    replace  :: c a -> a -> c a

-- Instance de Container pour Box avec la contrainte Eq a
instance Eq a => Container Box a where
    isEmpty Empty     = True
    isEmpty (Has _)   = False

    contains Empty _  = False
    contains (Has x) y = x == y

    replace _ newValue = Has newValue

-- Programme principal pour tester
main :: IO ()
main = do
    let b1 = Empty    :: Box Int
    let b2 = Has 42   :: Box Int
    putStrLn "=== Test de Container pour Box ==="
    print b1
    print b2

    putStrLn "\n1️⃣ Test de isEmpty :"
    print (isEmpty b1)   -- True
    print (isEmpty b2)   -- False

    putStrLn "\n2️⃣ Test de contains :"
    print (contains b2 42)   -- True
    print (contains b2 99)   -- False

    putStrLn "\n3️⃣ Test de replace :"
    print (replace b1 10 :: Box Int)    -- Has 10
    print (replace b2 99 :: Box Int)    -- Has 99

```

---

##  Explication pas à pas

### 1️ Type `Box a`

```haskell
data Box a = Empty | Has a deriving (Show, Eq)
```

* `Box` est un **type paramétrique** : il peut contenir une valeur de n’importe quel type `a`.
* `Empty` : la boîte est vide.
* `Has a` : la boîte contient une valeur.
* `deriving (Eq)` permet de comparer facilement deux boîtes.

---

### 2️ Classe de type `Container`

```haskell
class Container c where
    isEmpty  :: c a -> Bool
    contains :: (Eq a) => c a -> a -> Bool
    replace  :: c a -> a -> c a
```

Cette classe définit le comportement général d’un **conteneur générique** (comme une boîte, un sac, etc.) :

| Méthode    | Rôle                                                     |
| ---------- | -------------------------------------------------------- |
| `isEmpty`  | Vérifie si le conteneur est vide                         |
| `contains` | Vérifie si une valeur donnée est dans le conteneur       |
| `replace`  | Remplace le contenu du conteneur par une nouvelle valeur |

Remarque :
`contains` a besoin de la contrainte `(Eq a)` pour pouvoir comparer les éléments.

---

### 3️ Instance pour `Box`

```haskell
instance Container Box where
    isEmpty Empty     = True
    isEmpty (Has _)   = False

    contains Empty _  = False
    contains (Has x) y = x == y

    replace Empty newValue = Has newValue
    replace (Has _) newValue = Has newValue
```

**Comportement détaillé :**

| Fonction                   | Cas                                   | Résultat       |
| -------------------------- | ------------------------------------- | -------------- |
| `isEmpty Empty`            | boîte vide                            | `True`         |
| `isEmpty (Has _)`          | boîte pleine                          | `False`        |
| `contains Empty y`         | boîte vide                            | `False`        |
| `contains (Has x) y`       | compare `x` et `y`                    | `x == y`       |
| `replace Empty newValue`   | remplace vide par une nouvelle valeur | `Has newValue` |
| `replace (Has _) newValue` | remplace l’ancien contenu             | `Has newValue` |

---

### 4️ Programme principal

```haskell
main :: IO ()
main = do
    let b1 = Empty
    let b2 = Has 42
    ...
```

On teste toutes les méthodes :

* `isEmpty` → renvoie `True` ou `False`.
* `contains` → vérifie si la boîte contient une certaine valeur.
* `replace` → retourne une nouvelle boîte avec une valeur mise à jour.

---

##  Résultat attendu

```
=== Test de Container pour Box ===
Empty
Has 42

1️⃣ Test de isEmpty :
True
False

2️⃣ Test de contains :
True
False

3️⃣ Test de replace :
Has 10
Has 99
```

---

##  Résumé

| Élément                  | Description                                           |
| ------------------------ | ----------------------------------------------------- |
| `class Container`        | définit les opérations communes à tous les conteneurs |
| `instance Container Box` | implémente ces opérations pour `Box`                  |
| `isEmpty`                | teste si la boîte est vide                            |
| `contains`               | vérifie la présence d’une valeur                      |
| `replace`                | change le contenu de la boîte                         |
| `main`                   | permet de tester toutes les fonctionnalités           |

---
