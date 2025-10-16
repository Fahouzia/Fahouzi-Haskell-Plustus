**HC12T5 : Vérification de palindrome**

---

###  **Code complet**

```haskell
-- Définition de la fonction isPalindrome
isPalindrome :: String -> Bool
isPalindrome str = str == reverse str

-- Fonction principale main
main :: IO ()
main = do
    putStrLn "Entrez une chaîne de caractères :"
    input <- getLine

    if isPalindrome input
        then putStrLn "C'est un palindrome !"
        else putStrLn "Ce n'est pas un palindrome."
```

---

###  **Explication pas à pas**

1. **Fonction `isPalindrome`**

   ```haskell
   isPalindrome :: String -> Bool
   isPalindrome str = str == reverse str
   ```

   * La fonction prend une **chaîne de caractères** (`String`) et retourne un **Bool** (`True` ou `False`).
   * `reverse str` renverse la chaîne.
   * On compare la chaîne originale avec sa version inversée : si elles sont identiques, c’est un palindrome.

---

2. **Lecture de l’entrée utilisateur**

   ```haskell
   input <- getLine
   ```

   * `getLine` lit la saisie de l’utilisateur sous forme de texte (`String`).

---

3. **Vérification et affichage**

   ```haskell
   if isPalindrome input
       then putStrLn "C'est un palindrome !"
       else putStrLn "Ce n'est pas un palindrome."
   ```

   * Si `isPalindrome input` est `True`, on affiche que c’est un palindrome.
   * Sinon, on affiche que ce n’en est pas un.

---

### **Exemple d’exécution**

```
Entrez une chaîne de caractères :
radar
C'est un palindrome !
```

```
Entrez une chaîne de caractères :
bonjour
Ce n'est pas un palindrome.
```

---

