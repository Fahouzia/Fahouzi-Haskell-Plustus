**HC12T2 : Additionner deux nombres**, avec une **explication claire et pas à pas** �

---

###  **Code**

```haskell
-- Définition de la fonction addTwoNumbers
addTwoNumbers :: Int -> Int -> Int
addTwoNumbers x y = x + y

-- Fonction principale main
main :: IO ()
main = do
    putStrLn "Entrez le premier nombre :"
    input1 <- getLine
    putStrLn "Entrez le deuxième nombre :"
    input2 <- getLine

    -- Conversion des chaînes en entiers
    let num1 = read input1 :: Int
    let num2 = read input2 :: Int

    -- Calcul de la somme
    let somme = addTwoNumbers num1 num2

    -- Affichage du résultat
    putStrLn ("La somme est : " ++ show somme)
```

---

### 🔍 **Explication pas à pas**

1. **Définition de la fonction**

   ```haskell
   addTwoNumbers :: Int -> Int -> Int
   addTwoNumbers x y = x + y
   ```

   * Cette fonction prend **deux entiers** (`x` et `y`)
   * Elle retourne leur **somme**.

2. **Fonction `main`**

   * `putStrLn` affiche un message dans le terminal.
   * `getLine` lit une entrée clavier sous forme de texte (`String`).

3. **Conversion**

   ```haskell
   let num1 = read input1 :: Int
   ```

   * Comme `getLine` renvoie une `String`, on utilise `read` pour convertir en entier (`Int`).

4. **Calcul et affichage**

   ```haskell
   let somme = addTwoNumbers num1 num2
   putStrLn ("La somme est : " ++ show somme)
   ```

   * `show` transforme un nombre en texte pour pouvoir l’afficher.
   * Le résultat final est affiché dans le terminal.

---

###  **Exemple d’exécution**

```
Entrez le premier nombre :
5
Entrez le deuxième nombre :
7
La somme est : 12
```

