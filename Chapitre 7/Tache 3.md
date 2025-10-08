 **HC7T3 – Fonction avec contraintes multiples**et **explication claire pas à pas**.

---

##  Objectif

* Créer une fonction `compareValues` qui prend **deux valeurs du même type** et renvoie **la plus grande**.
* Assurer que le type `a` **implémente à la fois `Eq` et `Ord`**.

---

## Code

```haskell
-- HC7T3 : Fonction avec contraintes multiples

-- Définition de la fonction compareValues
compareValues :: (Eq a, Ord a) => a -> a -> a
compareValues x y
    | x == y    = x        -- Si les deux sont égaux, on renvoie x
    | x > y     = x        -- Si x est plus grand, on renvoie x
    | otherwise = y        -- Sinon, on renvoie y

-- Fonction principale main pour tester
main :: IO ()
main = do
    let a = 10
    let b = 20
    putStrLn ("Le plus grand entre " ++ show a ++ " et " ++ show b ++ " est : " ++ show (compareValues a b))

    let c = 'z'
    let d = 'a'
    putStrLn ("Le plus grand entre '" ++ show c ++ "' et '" ++ show d ++ "' est : " ++ show (compareValues c d))
```

---

## Explication pas à pas

### 1️⃣ Signature de la fonction

```haskell
compareValues :: (Eq a, Ord a) => a -> a -> a
```

* `(Eq a, Ord a) =>` → contraintes multiples : le type `a` doit être **comparable pour l’égalité (`Eq`)** et pour l’ordre (`Ord`)
* `a -> a -> a` → prend **deux valeurs du même type** et retourne **une valeur du même type**

---

### 2️⃣ Cas avec gardes

```haskell
compareValues x y
    | x == y    = x
    | x > y     = x
    | otherwise = y
```

* `x == y` → valeurs égales → renvoyer `x` (ou `y`, identique)
* `x > y` → `x` plus grand → renvoyer `x`
* `otherwise` → `y` est plus grand → renvoyer `y`

✅ Cette logique couvre **tous les cas possibles**.

---

### 3️⃣ Fonction `main` (tests)

* Test avec **entiers** : 10 et 20 → renvoie 20
* Test avec **caractères** : `'z'` et `'a'` → `'z'` est plus grand selon l’ordre ASCII

---

### 🧾 Exemple de sortie

```
Le plus grand entre 10 et 20 est : 20
Le plus grand entre 'z' et 'a' est : 'z'
```

---

 **Remarque**

* Grâce aux contraintes `(Eq a, Ord a)`, cette fonction est **générique** et fonctionne pour tous les types comparables, par exemple : `Int`, `Char`, `Float`, ou même un type personnalisé avec `Eq` et `Ord` définis.

---

