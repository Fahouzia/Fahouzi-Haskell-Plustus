HC2T2 - Tâche 2 : Signatures de fonctions

CODE 

```haskell
-- 1. Fonction add : prend deux Int et retourne leur somme
add :: Int -> Int -> Int
add x y = x + y

-- 2. Fonction isEven : prend un Int et retourne True si pair
isEven :: Int -> Bool
isEven n = n `mod` 2 == 0

-- 3. Fonction concatStrings : prend deux String et les concatène
concatStrings :: String -> String -> String
concatStrings s1 s2 = s1 ++ s2

-- Exemple d'utilisation dans main
main :: IO ()
main = do
    print (add 4 7)                    -- Résultat : 11
    print (isEven 6)                  -- Résultat : True
    print (isEven 5)                  -- Résultat : False
    print (concatStrings "Hello, " "World!")  -- Résultat : "Hello, World!"
```

EXPLICATION 
La signature de fonction est une ligne qui décrit le type des entrées (arguments) et le type de la sortie (résultat) d’une fonction.

C’est comme une carte d’identité de la fonction.
Elle indique :

Combien d’arguments la fonction prend,

Le type de chaque argument,

Le type de la valeur que la fonction retourne.

### 1. `add`

```haskell
add :: Int -> Int -> Int
add x y = x + y
```

* **Signature** : prend deux entiers (`Int`) et retourne un `Int`.
* `x + y` : addition simple.
* Type **curried** : `(Int -> (Int -> Int))` — on peut l’utiliser partiellement si besoin.

---

### 2. `isEven`

```haskell
isEven :: Int -> Bool
isEven n = n `mod` 2 == 0
```

* `mod` calcule le **reste de la division**.
* Si le reste de `n ÷ 2` est `0`, alors `n` est **pair** → retourne `True`.
* Sinon, retourne `False`.

---

### 3. `concatStrings`

```haskell
concatStrings :: String -> String -> String
concatStrings s1 s2 = s1 ++ s2
```

* `++` est l’opérateur de **concaténation de chaînes** en Haskell.
* Prend deux chaînes (`String`) et retourne leur **fusion**.

---

