HC1T8 - Tâche 8 : Fonctions d’ordre supérieur

CODE 
```haskell
-- Définition de applyTwice
applyTwice :: (a -> a) -> a -> a
applyTwice f x = f (f x)

-- Exemple d’utilisation dans main
main :: IO ()
main = do
    print (applyTwice (+1) 5)      -- Résultat : 7
    print (applyTwice (*2) 3)      -- Résultat : 12
    print (applyTwice reverse "abc") -- Résultat : "abc"
```

EXPLICATION 
Une fonction d’ordre supérieur est une fonction qui fait au moins l’une des deux choses suivantes :

 Elle prend une fonction en argument.

 Elle renvoie une fonction comme résultat.


### Signature de type

```haskell
applyTwice :: (a -> a) -> a -> a
```

* `(a -> a)` : le **premier paramètre** est une fonction qui prend un `a` et retourne un `a`.
   Par exemple : `(+1)`, `(*2)`, `reverse` (sur des chaînes), etc.
* `a -> a` : le **deuxième paramètre** est une valeur `x` de type `a`.
* Résultat final : un `a`, qui est le **résultat de f appliqué deux fois à x**.

### Corps de la fonction

```haskell
applyTwice f x = f (f x)
```

* Tu prends la fonction `f`,
* Tu l’appliques une première fois à `x` → `f x`,
* Puis tu appliques `f` une seconde fois → `f (f x)`.

---

QUELQUES EXEMPLES 

### 1. `applyTwice (+1) 5`

* `f = (+1)`, `x = 5`
* `f x = 6`
* `f (f x) = 7`
* Résultat : `7`

---

### 2. `applyTwice (*2) 3`

* `f = (*2)`, `x = 3`
* `f x = 6`
* `f (f x) = 12`
  * Résultat : `12`

---

### 3. `applyTwice reverse "abc"`

* `f = reverse`, `x = "abc"`
* `reverse "abc"` → `"cba"`
* `reverse "cba"` → `"abc"`
* Résultat : `"abc"`


