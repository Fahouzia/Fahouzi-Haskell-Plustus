HC10T6 : Récursivité mutuelle dans Eq pour Blockchain

---

### **Code :**

```haskell 
-- Définition du type Blockchain
data Blockchain = Blockchain {
    name :: String,
    blocks :: Int
} deriving (Show)

-- Définition de l'instance Eq avec récursivité mutuelle
instance Eq Blockchain where
    -- Définition de ==
    (==) b1 b2 = name b1 == name b2 && blocks b1 == blocks b2

    -- Définition de /= en termes de ==
    (/=) b1 b2 = not (b1 == b2)

-- Fonction principale pour tester
main :: IO ()
main = do
    let btc1 = Blockchain "Bitcoin" 800000
    let btc2 = Blockchain "Bitcoin" 800000
    let eth  = Blockchain "Ethereum" 600000

    putStrLn ("btc1 == btc2 ? " ++ show (btc1 == btc2))
    putStrLn ("btc1 /= btc2 ? " ++ show (btc1 /= btc2))
    putStrLn ("btc1 == eth  ? " ++ show (btc1 == eth))
    putStrLn ("btc1 /= eth  ? " ++ show (btc1 /= eth))
```

---

###  **Explication pas à pas :**

#### 1. **Rappel : la classe `Eq`**

La classe `Eq` est une classe standard de Haskell, utilisée pour les comparaisons d’égalité.

```haskell
class Eq a where
    (==), (/=) :: a -> a -> Bool
    x /= y = not (x == y)
    x == y = not (x /= y)
```

 Cela veut dire :

* `==` et `/=` sont **mutuellement récursives**.
* Si tu définis **l’une des deux**, l’autre peut être déduite automatiquement.
* Mais ici, tu dois **les définir explicitement toutes les deux** pour montrer la *récursivité mutuelle*.

---

#### 2. **Définition du type `Blockchain`**

```haskell
data Blockchain = Blockchain {
    name :: String,
    blocks :: Int
} deriving (Show)
```

* Une `Blockchain` possède :

  * un nom (`name`) — par exemple "Bitcoin"
  * un nombre de blocs (`blocks`) — par exemple 800000.

---

#### 3. **Instance `Eq` avec récursivité mutuelle**

```haskell
instance Eq Blockchain where
    (==) b1 b2 = name b1 == name b2 && blocks b1 == blocks b2
    (/=) b1 b2 = not (b1 == b2)
```

* Ici :

  * `==` compare deux `Blockchain` champ par champ.
  * `/=` est défini **en fonction de** `==`, ce qui crée une **récursion mutuelle logique** (comme dans la vraie définition de la classe `Eq`).
* Cela permet à `/=` d’être toujours cohérent avec `==`.

---

#### 4. **Fonction `main`**

* On crée deux blockchains identiques (`btc1`, `btc2`) et une différente (`eth`).
* On affiche les résultats de `==` et `/=`.

---

###  **Sortie attendue :**

```
btc1 == btc2 ? True
btc1 /= btc2 ? False
btc1 == eth  ? False
btc1 /= eth  ? True
```

---

### *Résumé du principe de récursivité mutuelle :**

| Fonction | Définie à partir de | Description            |
| -------- | ------------------- | ---------------------- |
| `(==)`   | champs du type      | Compare deux valeurs   |
| `(/=)`   | `not (==)`          | Opposé logique de `==` |

Ainsi, `==` et `/=` se **référencent mutuellement**, assurant la cohérence entre égalité et inégalité.

---
