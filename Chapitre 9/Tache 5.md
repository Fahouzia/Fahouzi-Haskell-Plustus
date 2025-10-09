HC9T5 : Type de données paramétrique avec syntaxe d’enregistrement

**Explications :**

### 1️⃣ Définition du type

```haskell
data Shape a 
    = Circle { color :: a }
    | Rectangle { color :: a }
    deriving Show
```


1. `data Shape a`

   * Déclare un type paramétrique `Shape` avec un type générique `a`.
   * Cela signifie que la couleur (`color`) peut être de n’importe quel type : `String`, `Int`, etc.

2. `Circle { color :: a }`

   * `Circle` est un constructeur avec un champ nommé `color` de type `a`.

3. `Rectangle { color :: a }`

   * Même principe pour `Rectangle`.

4. `deriving Show`

   * Permet d’afficher facilement les valeurs de `Shape`.

---

### CODE 

```haskell
data Shape a 
    = Circle { color :: a }
    | Rectangle { color :: a }
    deriving Show

main :: IO ()
main = do
    let c1 = Circle { color = "Red" }
    let r1 = Rectangle { color = "Blue" }

    print c1  -- Résultat : Circle {color = "Red"}
    print r1  -- Résultat : Rectangle {color = "Blue"}
```

---
