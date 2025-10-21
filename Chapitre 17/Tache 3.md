 **HC17T3 : Instance `Monoid` pour le type `Severity`**

---

###  Objectif

Créer une **instance `Monoid`** pour le type `Severity` défini précédemment :

* Les niveaux sont : `Low < Medium < High < Critical`.
* La combinaison de deux sévérités utilise le **Semigroup** existant (`<>` = maximum).
* La **valeur neutre** (`mempty`) doit être `Low`.

Cela permet d’utiliser des fonctions comme `mconcat` pour combiner plusieurs sévérités.

---

### Code

```haskell
-- HC17T3 : Instance Monoid pour Severity

import Data.Semigroup

-- Type Severity
data Severity = Low | Medium | High | Critical
    deriving (Show, Eq, Ord)

-- Semigroup déjà défini
instance Semigroup Severity where
    s1 <> s2 = max s1 s2

-- Monoid pour Severity
instance Monoid Severity where
    mempty = Low
    mappend = (<>)

-- Programme principal pour tester
main :: IO ()
main = do
    let urgences = [Low, Medium, High, Medium, Critical, Low]
    putStrLn "=== Test Monoid Severity ==="
    putStrLn ("Liste des urgences : " ++ show urgences)
    putStrLn ("Urgence la plus sévère : " ++ show (mconcat urgences))
```

---

###  Explications pas à pas

1. **Valeur neutre (`mempty`)**

```haskell
mempty = Low
```

* `Low` est le niveau minimal, donc combiner `Low` avec une autre sévérité n’influence pas le maximum.

2. **Combinaison (`mappend`)**

```haskell
mappend = (<>)
```

* On utilise le `Semigroup` déjà défini pour combiner les sévérités.
* `<>` retourne la sévérité maximale entre deux valeurs.

3. **Bloc `main`**

* `mconcat urgences` combine toutes les valeurs de la liste en utilisant `mappend`.
* Affiche la **sévérité maximale**.

---

###  Exemple d’exécution

```
=== Test Monoid Severity ===
Liste des urgences : [Low,Medium,High,Medium,Critical,Low]
Urgence la plus sévère : Critical
```

