**HC17T6 : Fonction `maxSeverity`**
---

###  Objectif

Créer une fonction `maxSeverity` qui :

* Prend une **liste de `Severity`** : `[Low, Medium, High, Critical]` par exemple.
* Combine toutes les valeurs en utilisant **`mconcat`**.
* Retourne la **sévérité maximale**.

> On utilise ici l’instance `Monoid` définie précédemment pour `Severity`, où `mempty = Low` et `<> = max`.

---

### Code

```haskell
-- HC17T6 : Fonction maxSeverity

import Data.Monoid

-- Type Severity avec Monoid
data Severity = Low | Medium | High | Critical
    deriving (Show, Eq, Ord)

instance Semigroup Severity where
    s1 <> s2 = max s1 s2

instance Monoid Severity where
    mempty = Low
    mappend = (<>)

-- Fonction qui combine une liste de Severity et retourne la plus élevée
maxSeverity :: [Severity] -> Severity
maxSeverity = mconcat

-- Programme principal pour tester
main :: IO ()
main = do
    let urgences = [Low, Medium, High, Medium, Critical, Low]
    putStrLn "=== Test maxSeverity ==="
    putStrLn ("Liste des urgences : " ++ show urgences)
    putStrLn ("Urgence la plus sévère : " ++ show (maxSeverity urgences))
```

---

### 🔍 Explications pas à pas

1. **Instance `Semigroup`**

```haskell
s1 <> s2 = max s1 s2
```

* L’opérateur `<>` retourne la **sévérité maximale** entre deux valeurs.

2. **Instance `Monoid`**

```haskell
mempty = Low
mappend = (<>)
```

* `mempty` est le niveau minimal (`Low`).
* Permet d’utiliser `mconcat` pour combiner toute une liste.

3. **Fonction `maxSeverity`**

```haskell
maxSeverity = mconcat
```

* `mconcat` combine tous les éléments de la liste en utilisant `mappend`.
* Retourne la sévérité maximale de la liste.

4. **Bloc `main`**

* Teste la fonction avec une liste de valeurs `Severity`.
* Affiche le résultat.

---

### 🧩 Exemple d’exécution

```
=== Test maxSeverity ===
Liste des urgences : [Low,Medium,High,Medium,Critical,Low]
Urgence la plus sévère : Critical
```

---

Si tu veux, je peux te montrer **une version interactive** où l’utilisateur peut **saisir ses urgences sous forme de texte** et obtenir la sévérité maximale directement.
Veux‑tu que je fasse ça ?
