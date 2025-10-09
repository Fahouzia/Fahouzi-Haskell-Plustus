

### 1️⃣ Définir le type `Box`

On commence par un type paramétrique `Box a` avec deux constructeurs :

```haskell
data Box a = Empty | Has a
```

* `Empty` représente une boîte vide.
* `Has a` représente une boîte contenant une valeur de type `a`.

---

### 2️⃣ Définir la fonction `addN`

La fonction `addN` prend un nombre `n` et une `Box a`. Si la boîte contient un nombre, on ajoute `n` à ce nombre ; si elle est vide, on retourne `Empty`.

```haskell
addN :: Num a => a -> Box a -> Box a
addN n Empty     = Empty
addN n (Has x)   = Has (x + n)
```

**Explications :**

* `Num a =>` signifie que `a` doit être un type numérique (`Int`, `Float`, etc.).
* `addN n Empty = Empty` : si la boîte est vide, on ne fait rien.
* `addN n (Has x) = Has (x + n)` : si la boîte contient `x`, on retourne `Has (x + n)`.

---

### CODE 

```haskell
data Box a = Empty | Has a deriving Show

addN :: Num a => a -> Box a -> Box a
addN n Empty     = Empty
addN n (Has x)   = Has (x + n)

main :: IO ()
main = do
    let box1 = Has 10
    let box2 = Empty

    print (addN 5 box1)  -- Résultat attendu : Has 15
    print (addN 5 box2)  -- Résultat attendu : Empty
```

---

