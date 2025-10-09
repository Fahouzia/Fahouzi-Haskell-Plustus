HC9T4 : Extraire une valeur d’une Box

**Explications ligne par ligne :**
### 1️⃣ Rappel du type `Box`

```haskell
data Box a = Empty | Has a deriving Show
```

* `Empty` → boîte vide
* `Has a` → boîte contenant une valeur

---

### 2️⃣ Définir la fonction `extract`

```haskell
extract :: a -> Box a -> a
extract def Empty   = def
extract _   (Has x) = x
```



1. `extract :: a -> Box a -> a`

   * La fonction prend une valeur par défaut (`a`) et une `Box a`, et retourne une valeur de type `a`.

2. `extract def Empty = def`

   * Si la boîte est vide, on retourne la valeur par défaut `def`.

3. `extract _ (Has x) = x`

   * Si la boîte contient une valeur `x`, on la retourne.
   * Le `_` signifie que la valeur par défaut n’est pas utilisée dans ce cas.

---

## CODE 

```haskell
data Box a = Empty | Has a deriving Show

extract :: a -> Box a -> a
extract def Empty   = def
extract _   (Has x) = x

main :: IO ()
main = do
    let box1 = Has 42
    let box2 = Empty

    print (extract 0 box1)   -- Résultat : 42
    print (extract 0 box2)   -- Résultat : 0
```

---
