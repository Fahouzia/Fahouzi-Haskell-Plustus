HC4T8 - Tâche 8 : Extraire des valeurs de tuples

```haskell
-- Fonction qui décrit un tuple de 3 éléments
describeTuple :: (Show a, Show b, Show c) => (a, b, c) -> String
describeTuple (x, y, z) = "Premier: " ++ show x ++ ", Deuxième: " ++ show y ++ ", Troisième: " ++ show z

-- Exemple de tests
main :: IO ()
main = do
    putStrLn (describeTuple (1, "Hello", 3.5))
    putStrLn (describeTuple ('a', True, 42))
```

### Explication :

1. `describeTuple :: (Show a, Show b, Show c) => (a, b, c) -> String`

   * La fonction prend un tuple de trois éléments de types quelconques (`a`, `b`, `c`).
   * Chaque type doit être **affichable** (`Show`) pour pouvoir être converti en chaîne avec `show`.
   * Elle retourne une `String`.

2. `describeTuple (x, y, z) = ...`

   * On **déstructure le tuple** pour accéder aux trois éléments.
   * `show x`, `show y`, `show z` convertissent les valeurs en chaînes.
   * On les concatène avec un texte descriptif pour créer la phrase.

3. `main`

   * Sert à tester la fonction avec différents tuples.
