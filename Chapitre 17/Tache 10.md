**HC17T10 : Instance `Monoid` pour `Config`**

---

###  Objectif

Créer une **instance `Monoid`** pour le type `Config` défini précédemment, avec les règles suivantes :

* Élément neutre (`mempty`) :

  * `loggingLevel` minimal (0)
  * `timeout` maximal (`maxBound :: Int`)
  * `retries` minimal (0)

* Combinaison (`mappend` ou `<>`) : **utiliser l’instance `Semigroup` existante**.

> Cela permet de combiner facilement plusieurs configurations avec `mconcat`.

---

###  Code 

```haskell
-- HC17T10 : Instance Monoid pour Config

import Data.Semigroup

-- Type Config
data Config = Config
    { loggingLevel :: Int
    , timeout      :: Int
    , retries      :: Int
    } deriving (Show, Eq)

-- Instance Semigroup
instance Semigroup Config where
    c1 <> c2 = Config
        { loggingLevel = max (loggingLevel c1) (loggingLevel c2)
        , timeout      = min (timeout c1) (timeout c2)
        , retries      = max (retries c1) (retries c2)
        }

-- Instance Monoid
instance Monoid Config where
    mempty  = Config { loggingLevel = 0, timeout = maxBound, retries = 0 }
    mappend = (<>)

-- Programme principal pour tester
main :: IO ()
main = do
    let cfg1 = Config { loggingLevel = 2, timeout = 30, retries = 3 }
        cfg2 = Config { loggingLevel = 4, timeout = 20, retries = 5 }
        cfg3 = Config { loggingLevel = 1, timeout = 25, retries = 2 }
    putStrLn "=== Test Monoid Config ==="
    putStrLn ("Liste des configurations : " ++ show [cfg1, cfg2, cfg3])
    putStrLn ("Configuration combinée : " ++ show (mconcat [cfg1, cfg2, cfg3]))
```

---

###  Explications pas à pas

1. **Élément neutre (`mempty`)**

```haskell
mempty = Config { loggingLevel = 0, timeout = maxBound, retries = 0 }
```

* Niveau de log minimal → n’influence pas le maximum lors de la combinaison.
* Timeout maximal → n’influence pas le minimum lors de la combinaison.
* Reprises minimal → n’influence pas le maximum lors de la combinaison.

2. **Combinaison (`mappend`)**

```haskell
mappend = (<>)
```

* Réutilise l’instance `Semigroup` pour combiner les configurations.

3. **Bloc `main`**

* Déclare plusieurs configurations.
* Utilise `mconcat` pour combiner toute la liste.
* Affiche la configuration résultante.

---

### 🧩 Exemple d’exécution

```
=== Test Monoid Config ===
Liste des configurations : [Config {loggingLevel = 2, timeout = 30, retries = 3},Config {loggingLevel = 4, timeout = 20, retries = 5},Config {loggingLevel = 1, timeout = 25, retries = 2}]
Configuration combinée : Config {loggingLevel = 4, timeout = 20, retries = 5}
```


