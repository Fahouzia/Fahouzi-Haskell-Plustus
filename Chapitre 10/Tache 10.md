HC10T10 : Classe Concatenatable
###  **Énoncé **

> Créer une classe de type `Concatenatable` avec une fonction
> `concatWith :: a -> a -> a`.
> L’implémenter pour le type `[Char]` (c’est-à-dire `String`).

---

### **Code Haskell complet**

```haskell
-- HC10T10 : Classe Concatenatable
class Concatenatable a where
    concatWith :: a -> a -> a

-- Implémentation pour le type String
instance Concatenatable String where
    concatWith s1 s2 = s1 ++ s2

-- Programme principal pour tester
main :: IO ()
main = do
    let texte1 = "Hello"
    let texte2 = "World!"
    let resultat = concatWith texte1 (" " ++ texte2)
    putStrLn ("Résultat de la concaténation : " ++ resultat)
```

---

###  **Explication pas à pas**

1. **Définition de la classe**

   ```haskell
   class Concatenatable a where
       concatWith :: a -> a -> a
   ```

   → On crée une **classe de type** nommée `Concatenatable`
   → Elle définit une **fonction générique** `concatWith`
   qui prend **deux valeurs du même type `a`** et **retourne une valeur du même type `a`**.

---

2. **Instance pour `String`**

   ```haskell
   instance Concatenatable String where
       concatWith s1 s2 = s1 ++ s2
   ```

   → Ici, `String` est une liste de caractères (`[Char]`).
   → On utilise l’opérateur `++` pour **concaténer** deux chaînes.
   → Exemple : `"Hello" ++ "World"` → `"HelloWorld"`

---

3. **Programme principal**

   ```haskell
   main :: IO ()
   main = do
       let texte1 = "Hello"
       let texte2 = "World!"
       let resultat = concatWith texte1 (" " ++ texte2)
       putStrLn ("Résultat de la concaténation : " ++ resultat)
   ```

   → On définit deux chaînes (`texte1` et `texte2`).
   → On utilise `concatWith` pour les coller ensemble.
   → Le résultat est affiché à l’écran.

---

###  **Exécution attendue**

```
Résultat de la concaténation : Hello World!
```

---
