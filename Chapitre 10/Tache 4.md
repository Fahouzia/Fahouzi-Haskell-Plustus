HC10T4 : Instance Eq pour Box

CODE 

```haskell
-- HC10T4 : Instance Eq pour Box

-- Définition du type paramétrique Box
data Box a = Empty | Has a
    deriving (Show)

-- Définition de l'instance Eq pour Box
instance (Eq a) => Eq (Box a) where
    Empty == Empty = True
    (Has x) == (Has y) = x == y
    _ == _ = False

-- Fonction principale pour tester
main :: IO ()
main = do
    let b1 = Has 10
    let b2 = Has 10
    let b3 = Has 5
    let b4 = Empty

    putStrLn ("b1 == b2 ? " ++ show (b1 == b2))
    putStrLn ("b1 == b3 ? " ++ show (b1 == b3))
    putStrLn ("b1 == b4 ? " ++ show (b1 == b4))
    putStrLn ("b4 == Empty ? " ++ show (b4 == Empty))
```

---

###  **Explication pas à pas :**

1. **Création du type `Box` paramétrique :**

   ```haskell
   data Box a = Empty | Has a
   ```

   * `Box a` est un type **paramétrique** : il peut contenir n’importe quel type (`Int`, `String`, etc.).
   * `Empty` représente une boîte vide.
   * `Has a` représente une boîte contenant une valeur de type `a`.

   Exemples :

   ```haskell
   Has 5      -- une Box contenant 5
   Empty      -- une Box vide
   Has "Hi"   -- une Box contenant une chaîne
   ```

2. **Création de l’instance `Eq` :**

   ```haskell
   instance (Eq a) => Eq (Box a) where
       Empty == Empty = True
       (Has x) == (Has y) = x == y
       _ == _ = False
   ```

   * `(Eq a) =>` signifie que la comparaison n’est possible que si le type `a` lui-même peut être comparé avec `==`.
   * On définit trois cas :

     1. Deux boîtes vides sont égales.
     2. Deux boîtes contenant des valeurs sont égales **si** leurs contenus sont égaux.
     3. Toute autre combinaison (`Empty` vs `Has`) est **fausse**.

3. **Fonction `main` pour tester :**

   * On crée plusieurs boîtes : `b1`, `b2`, `b3`, `b4`.
   * On compare les différentes paires avec `==` et on affiche les résultats.

---

###  **Sortie attendue :**

```
b1 == b2 ? True
b1 == b3 ? False
b1 == b4 ? False
b4 == Empty ? True
```

---

Souhaites-tu que je te montre **une version plus avancée** où `Box` est aussi **instance de Ord** (pour permettre les comparaisons `<`, `>`, etc.) ?
