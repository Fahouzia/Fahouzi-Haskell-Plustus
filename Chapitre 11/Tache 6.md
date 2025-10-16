HC11T6 : AdvancedEq pour Blockchain


On va :

1. créer une **classe de type dérivée de `Eq`**, appelée `AdvancedEq`,
2. y ajouter une méthode personnalisée `compareEquality`,
3. définir un **type `Blockchain`**,
4. et enfin **implémenter `AdvancedEq` pour ce type**.

---

##  Code
```haskell
-- Définition du type Blockchain
data Blockchain = Bitcoin | Ethereum | Cardano | Solana deriving (Show, Eq)

-- Définition de la classe de type AdvancedEq
class Eq a => AdvancedEq a where
    compareEquality :: a -> a -> String

-- Instance de AdvancedEq pour Blockchain
instance AdvancedEq Blockchain where
    compareEquality a b
        | a == b    = "✅ Les deux blockchains sont identiques : " ++ show a
        | otherwise = "❌ Les blockchains sont différentes : " ++ show a ++ " ≠ " ++ show b

-- Programme principal pour tester
main :: IO ()
main = do
    let b1 = Bitcoin
    let b2 = Bitcoin
    let b3 = Ethereum
    let b4 = Cardano

    putStrLn "=== Test de AdvancedEq pour Blockchain ===\n"

    print (compareEquality b1 b2)
    print (compareEquality b1 b3)
    print (compareEquality b3 b4)
```

---

## Explication pas à pas

### 1️⃣ Type `Blockchain`

```haskell
data Blockchain = Bitcoin | Ethereum | Cardano | Solana deriving (Show, Eq)
```

* On crée un **type énuméré** représentant plusieurs blockchains.
* `deriving (Show, Eq)` permet :

  * `Show` → d’afficher les valeurs (`print`),
  * `Eq` → de pouvoir les comparer avec `==`.

---

### 2️⃣ Classe `AdvancedEq`

```haskell
class Eq a => AdvancedEq a where
    compareEquality :: a -> a -> String
```

* `class Eq a => AdvancedEq a` signifie :

  * `AdvancedEq` **hérite** de `Eq` :
    tout type qui appartient à `AdvancedEq` doit **déjà** appartenir à `Eq`.
* `compareEquality` est une **méthode personnalisée** :

  * elle compare deux valeurs,
  * et renvoie une **chaîne de caractères descriptive** plutôt qu’un simple `Bool`.

---

### 3️⃣ Instance pour `Blockchain`

```haskell
instance AdvancedEq Blockchain where
    compareEquality a b
        | a == b    = "✅ Les deux blockchains sont identiques : " ++ show a
        | otherwise = "❌ Les blockchains sont différentes : " ++ show a ++ " ≠ " ++ show b
```

* On utilise la fonction `(==)` héritée de `Eq` pour tester l’égalité.
* Si elles sont identiques → message positif ✅
* Sinon → message négatif ❌ avec les deux valeurs affichées.

---

### 4️⃣ Fonction `main`

```haskell
main :: IO ()
main = do
    let b1 = Bitcoin
    let b2 = Bitcoin
    let b3 = Ethereum
    let b4 = Cardano

    print (compareEquality b1 b2)
    print (compareEquality b1 b3)
    print (compareEquality b3 b4)
```

On compare plusieurs blockchains entre elles pour tester le comportement.

---

## Résultat attendu

```
=== Test de AdvancedEq pour Blockchain ===

"✅ Les deux blockchains sont identiques : Bitcoin"
"❌ Les blockchains sont différentes : Bitcoin ≠ Ethereum"
"❌ Les blockchains sont différentes : Ethereum ≠ Cardano"
```

---

##  Résumé

| Élément                          | Description                                                 |
| -------------------------------- | ----------------------------------------------------------- |
| `class Eq a => AdvancedEq a`     | crée une classe qui **étend `Eq`**                          |
| `compareEquality`                | compare deux valeurs et retourne un message textuel         |
| `Blockchain`                     | type représentant des blockchains (Bitcoin, Ethereum, etc.) |
| `instance AdvancedEq Blockchain` | implémente la logique de comparaison personnalisée          |
| `main`                           | permet de tester les différents cas                         |

---
