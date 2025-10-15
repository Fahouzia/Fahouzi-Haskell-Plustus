 **HC11T2 : la fonction `fancyFunction`** 

---

##  Code 

```haskell
-- Définition de la classe WeAccept
class WeAccept a where
    weAccept :: a -> Bool
    fancyFunction :: a -> String           -- fonction supplémentaire
    fancyFunction x =
        if weAccept x
            then " Accepted: " ++ show x
            else " Rejected: " ++ show x

-- Type de paiement Cardano
data Cardano = ADA deriving (Show)

-- Type de paiement Cash
data Cash = USD | EUR | GBP deriving (Show)

-- Type Country
data Country = France | Burkina | USA | Unknown deriving (Show)

-- Instances de WeAccept pour chaque type

-- Pour Cardano : toujours accepté
instance WeAccept Cardano where
    weAccept ADA = True

-- Pour Cash : on accepte seulement certaines devises
instance WeAccept Cash where
    weAccept USD = True
    weAccept EUR = True
    weAccept _   = False

-- Pour Country : on accepte certains pays
instance WeAccept Country where
    weAccept France  = True
    weAccept Burkina = True
    weAccept _       = False

-- Programme principal
main :: IO ()
main = do
    putStrLn "=== Test de fancyFunction ==="
    print (fancyFunction ADA)
    print (fancyFunction USD)
    print (fancyFunction GBP)
    print (fancyFunction France)
    print (fancyFunction USA)
```

---

##  Explication pas à pas

### 1️ Classe `WeAccept`

```haskell
class WeAccept a where
    weAccept :: a -> Bool
    fancyFunction :: a -> String
```

* La classe de type `WeAccept` déclare deux fonctions :

  * `weAccept` : décide si une valeur est **acceptée ou non**.
  * `fancyFunction` : **fournit une version textuelle** de ce verdict.

---

### 2️ Implémentation par défaut

```haskell
fancyFunction x =
    if weAccept x
        then " Accepted: " ++ show x
        else " Rejected: " ++ show x
```

* Cette **implémentation par défaut** est dans la classe elle-même.
* Elle appelle `weAccept` et utilise `show` pour convertir la valeur en texte (cela nécessite que le type dérive `Show`).

---

### 3️ Types concrets

On crée **trois types simples** :

```haskell
data Cardano = ADA deriving (Show)
data Cash = USD | EUR | GBP deriving (Show)
data Country = France | Burkina | USA | Unknown deriving (Show)
```

Ces types servent à représenter différents **moyens de paiement** et **pays**.

---

### 4️ Instances de `WeAccept`

On définit les règles d’acceptation spécifiques à chaque type :

```haskell
instance WeAccept Cardano where
    weAccept ADA = True
```

→ Cardano est **toujours accepté**.

```haskell
instance WeAccept Cash where
    weAccept USD = True
    weAccept EUR = True
    weAccept _   = False
```

→ Seuls les paiements en **USD** et **EUR** sont acceptés.

```haskell
instance WeAccept Country where
    weAccept France  = True
    weAccept Burkina = True
    weAccept _       = False
```

→ Seuls certains pays sont acceptés.

---

### 5️ Fonction `main`

```haskell
main :: IO ()
main = do
    putStrLn "=== Test de fancyFunction ==="
    print (fancyFunction ADA)
    print (fancyFunction USD)
    print (fancyFunction GBP)
    print (fancyFunction France)
    print (fancyFunction USA)
```

On teste ici **plusieurs valeurs** pour vérifier que `fancyFunction` utilise bien `weAccept`.

---



---

##  Résumé

| Élément             | Description                                      |
| ------------------- | ------------------------------------------------ |
| `weAccept`          | Vérifie si une valeur est acceptée               |
| `fancyFunction`     | Donne un message textuel avec un ✅ ou ❌          |
| `instance WeAccept` | Spécifie la règle d’acceptation pour chaque type |
| `main`              | Teste différents types (Cardano, Cash, Country)  |

---
