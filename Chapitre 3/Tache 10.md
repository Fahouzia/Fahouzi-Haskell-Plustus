HC3T10 : Vérifier si une chaîne est un palindrome (récursion + gardes)

```haskell

isPalindrome :: String -> Bool
isPalindrome str
    | length str <= 1 = True
    | head str == last str = isPalindrome (init (tail str))
    | otherwise = False

main :: IO ()
main = do
    putStrLn ("isPalindrome \"racecar\" → " ++ show (isPalindrome "racecar"))
    putStrLn ("isPalindrome \"haskell\" → " ++ show (isPalindrome "haskell"))
    putStrLn ("isPalindrome \"madam\"   → " ++ show (isPalindrome "madam"))
```

---

**Résultats attendus :**

```
isPalindrome "racecar" → True
isPalindrome "haskell" → False
isPalindrome "madam"   → True
```

---

**Explication complète**

###  1. Signature

```haskell
isPalindrome :: String -> Bool
```

 La fonction prend une **chaîne de caractères (`String`)**
et retourne un **booléen (`True` ou `False`)**.

---

###  2. Les gardes (conditions)

```haskell
isPalindrome str
    | length str <= 1 = True
```

 Si la chaîne a **0 ou 1 caractère**, elle est forcément un palindrome
(exemples : `""`, `"a"`) → on retourne `True`.

---

```haskell
    | head str == last str = isPalindrome (init (tail str))
```

Si **le premier** (`head str`) et **le dernier caractère** (`last str`) sont identiques,
on vérifie **récursivement** le reste de la chaîne, c’est-à-dire :

* on enlève le premier avec `tail`
* on enlève le dernier avec `init`

Par exemple :
`"racecar"`
→ tête = `'r'`, dernier = `'r'`
→ on vérifie `"aceca"`

---

```haskell
    | otherwise = False
```

 Si les deux caractères ne sont pas identiques,
ce n’est **pas un palindrome** → on retourne `False`.

---

###  3. Le `main`

```haskell
main = do
    putStrLn ("isPalindrome \"racecar\" → " ++ show (isPalindrome "racecar"))
```

 `putStrLn` affiche le texte à l’écran.
`show` convertit la valeur booléenne (`True` ou `False`) en texte.

---

1. Cas de base : chaîne vide ou d’un seul caractère → True
2. Sinon :

   * Si premier == dernier → vérifier le reste
   * Sinon → False
