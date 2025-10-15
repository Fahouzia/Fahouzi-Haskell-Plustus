HC10T8 : Sous-classe AdvancedEq de Eq
### **Code :**

```haskell
-- HC10T8 : Sous-classe AdvancedEq de Eq

-- Définition de la sous-classe AdvancedEq
class Eq a => AdvancedEq a where
    compareEquality :: a -> a -> Bool

-- Définition d’un type Blockchain
data Blockchain = Blockchain {
    name :: String,
    blocks :: Int
} deriving (Show)

-- Instance Eq de base
instance Eq Blockchain where
    (==) b1 b2 = name b1 == name b2 && blocks b1 == blocks b2

-- Implémentation de AdvancedEq pour Blockchain
instance AdvancedEq Blockchain where
    compareEquality b1 b2 =
        if b1 == b2
            then True
            else
                -- Comparaison "avancée" : même nom, mais nombre de blocs différent
                if name b1 == name b2
                    then True
                    else False

-- Fonction principale pour tester
main :: IO ()
main = do
    let btc1 = Blockchain "Bitcoin" 800000
    let btc2 = Blockchain "Bitcoin" 800000
    let btc3 = Blockchain "Bitcoin" 700000
    let eth  = Blockchain "Ethereum" 600000

    putStrLn ("btc1 == btc2 : " ++ show (btc1 == btc2))
    putStrLn ("btc1 == btc3 : " ++ show (btc1 == btc3))
    putStrLn ("compareEquality btc1 btc2 : " ++ show (compareEquality btc1 btc2))
    putStrLn ("compareEquality btc1 btc3 : " ++ show (compareEquality btc1 btc3))
    putStrLn ("compareEquality btc1 eth  : " ++ show (compareEquality btc1 eth))
```

---

###  **Explication pas à pas :**

#### 1. **Création d’une sous-classe de `Eq`**

```haskell
class Eq a => AdvancedEq a where
    compareEquality :: a -> a -> Bool
```

* On crée une **nouvelle classe `AdvancedEq`** qui hérite de `Eq`.
* Le `Eq a =>` signifie que **tout type `a` qui est `AdvancedEq` doit déjà être `Eq`**.
* Elle ajoute une **méthode supplémentaire** :
  `compareEquality`, qui permet une comparaison plus “souple” ou “intelligente”.

---

#### 2. **Définition du type `Blockchain`**

```haskell
data Blockchain = Blockchain {
    name :: String,
    blocks :: Int
} deriving (Show)
```

* Une blockchain est représentée par :

  * `name` : son nom (ex. "Bitcoin")
  * `blocks` : le nombre de blocs dans la chaîne

---

#### 3. **Instance `Eq` de base**

```haskell
instance Eq Blockchain where
    (==) b1 b2 = name b1 == name b2 && blocks b1 == blocks b2
```

* Deux blockchains sont **égales** si elles ont **le même nom et le même nombre de blocs**.

---

#### 4. **Instance `AdvancedEq`**

```haskell
instance AdvancedEq Blockchain where
    compareEquality b1 b2 =
        if b1 == b2
            then True
            else if name b1 == name b2
                then True
                else False
```

* Si les deux blockchains sont exactement identiques (`==`), on retourne `True`.
* Sinon, si elles ont **le même nom** (même blockchain, mais blocs différents),
  on considère qu’elles sont "proches", donc `True`.
* Sinon `False`.

---

#### 5. **Fonction `main` pour tester**

On crée quatre blockchains et on teste :

* L’égalité (`==`)
* La comparaison avancée (`compareEquality`)

---

###  **Sortie attendue dans le terminal :**

```
btc1 == btc2 : True
btc1 == btc3 : False
compareEquality btc1 btc2 : True
compareEquality btc1 btc3 : True
compareEquality btc1 eth  : False
```

---

###  **Différence entre `==` et `compareEquality`**

| Fonction          | Sens    | Exemples                                                                                                            |
| ----------------- | ------- | ------------------------------------------------------------------------------------------------------------------- |
| `(==)`            | stricte | Deux blockchains sont égales **seulement si tout est identique**                                                    |
| `compareEquality` | avancée | Deux blockchains peuvent être considérées “égales” si elles ont **le même nom**, même si le nombre de blocs diffère |

---
