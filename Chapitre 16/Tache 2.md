**HC16T2 : Vérifier si une chaîne est un palindrome**.

---

###  Objectif

Créer une fonction Haskell qui :

* prend une chaîne de caractères en entrée,
* renvoie `True` si la chaîne est un **palindrome** (elle se lit de la même façon dans les deux sens),
* renvoie `False` sinon.

Exemples :

* `"radar"` → ✅ palindrome
* `"bonjour"` → ❌ pas un palindrome

---

### Code

```haskell
-- HC16T2 : Vérifier si une chaîne est un palindrome

-- Fonction qui vérifie si une chaîne est un palindrome
isPalindrome :: String -> Bool
isPalindrome s = s == reverse s

-- Programme principal pour tester
main :: IO ()
main = do
    putStrLn "=== Vérification de palindrome ==="
    putStrLn "Entrez une chaîne de caractères :"
    input <- getLine
    if isPalindrome input
        then putStrLn "✅ La chaîne est un palindrome."
        else putStrLn "❌ La chaîne n'est pas un palindrome."
```

---

###  Explications détaillées

1. **Fonction `isPalindrome`**

   ```haskell
   isPalindrome :: String -> Bool
   isPalindrome s = s == reverse s
   ```

   * Elle compare la chaîne `s` avec son inverse `reverse s`.
   * Si elles sont identiques → `True`, sinon → `False`.

2. **Programme principal (`main`)**

   * Lit une chaîne saisie par l’utilisateur.
   * Appelle la fonction `isPalindrome`.
   * Affiche un message différent selon le résultat.

---

### 🧩 Exemples d’exécution

 **Cas palindrome :**

```
=== Vérification de palindrome ===
Entrez une chaîne de caractères :
radar
✅ La chaîne est un palindrome.
```

 **Cas non palindrome :**

```
=== Vérification de palindrome ===
Entrez une chaîne de caractères :
bonjour
❌ La chaîne n'est pas un palindrome.
```

---
