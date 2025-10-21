**HC16T1 : Inverser une chaîne de caractères**
---

###  Objectif

Créer une fonction qui **inverse une chaîne de caractères**, par exemple :
`"bonjour"` → `"ruojnob"`

---

###  Code
```haskell
-- HC16T1 : Inverser une chaîne de caractères

-- Fonction qui inverse une chaîne
reverseString :: String -> String
reverseString s = reverse s

-- Programme principal pour tester
main :: IO ()
main = do
    putStrLn "=== Inversion d'une chaîne ==="
    putStrLn "Entrez une chaîne de caractères :"
    input <- getLine
    putStrLn ("Chaîne inversée : " ++ reverseString input)
```

---

###  Explications détaillées

1. **Type de la fonction**

   ```haskell
   reverseString :: String -> String
   ```

   Elle prend une chaîne (`String`) et retourne une autre chaîne (`String`).

2. **Utilisation de la fonction intégrée `reverse`**

   * `reverse` est une fonction standard de Haskell (définie dans le Prelude).
   * Elle retourne une nouvelle chaîne contenant les caractères dans l’ordre inverse.

3. **Bloc `main`**

   * Lit une entrée utilisateur avec `getLine`.
   * Appelle `reverseString`.
   * Affiche le résultat.

---

###  Exemple d’exécution

```
=== Inversion d'une chaîne ===
Entrez une chaîne de caractères :
bonjour
Chaîne inversée : ruojnob
```
