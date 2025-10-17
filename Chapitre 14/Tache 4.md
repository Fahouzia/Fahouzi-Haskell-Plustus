**HC14T4 : Extension TypeApplications**
---

###  **Code**

```haskell
{-# LANGUAGE TypeApplications #-}

module Main where

-- Fonction qui convertit une chaîne en entier en utilisant TypeApplications
convertirEnInt :: String -> Int
convertirEnInt s = read @Int s  -- On spécifie explicitement le type lu

main :: IO ()
main = do
    putStrLn "=== Exemple d'utilisation de TypeApplications ==="
    putStrLn "Entrez un nombre entier :"
    input <- getLine
    let nombre = convertirEnInt input
    putStrLn ("Le nombre converti est : " ++ show nombre)
```

---

###  **Explications détaillées**

1. **Activation de l’extension :**

   ```haskell
   {-# LANGUAGE TypeApplications #-}
   ```

   → Elle permet de **spécifier explicitement le type d’une fonction polymorphe** (comme `read`, `show`, etc.) en écrivant `@Type`.

2. **Utilisation de `read @Int` :**

   ```haskell
   read @Int s
   ```

   * Habituellement, on écrit simplement `read s`, mais ici on **indique explicitement** que le type attendu est `Int`.
   * Cela évite les ambiguïtés possibles lorsque `read` peut retourner plusieurs types (comme `Int`, `Float`, `Double`, etc.).

3. **Fonction `convertirEnInt` :**

   * Prend une `String` en entrée (ex. `"42"`)
   * Retourne un `Int` grâce à `read @Int`

4. **Programme principal :**

   * Demande une entrée utilisateur
   * Convertit la chaîne en entier
   * Affiche le résultat

---

###  **Exécution dans le terminal**

Si tu utilises un fichier `HC14T4.hs`, exécute :

```bash
runhaskell HC14T4.hs
```

ou, dans un projet **Cabal** :

```bash
cabal run
```

