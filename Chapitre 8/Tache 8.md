HC8T8 : Synonymes de type et fonction de salutation

### SUJET 

> Utiliser des synonymes de type `Name` pour `String` et `Age` pour `Int`.
> Définir une fonction `greet :: Name -> Age -> String` qui prend un nom et un âge, et retourne un message de salutation.

---

###  Code
```haskell


-- Définition de synonymes de types
type Name = String
type Age  = Int

-- Fonction de salutation
greet :: Name -> Age -> String
greet name age = "Bonjour " ++ name ++ ", tu as " ++ show age ++ " ans !"

-- Fonction principale pour tester
main :: IO ()
main = do
    let personName = "Alice"
    let personAge = 25
    putStrLn (greet personName personAge)
```

---

###  Explication

1. **`type Name = String` et `type Age = Int`**

   * On crée deux **synonymes de types** pour rendre le code plus lisible.
     Exemple :

     * `Name` représente une chaîne de caractères (`String`).
     * `Age` représente un entier (`Int`).

2. **`greet :: Name -> Age -> String`**

   * La fonction prend un nom et un âge, et renvoie une phrase de salutation.

3. **`greet name age = "Bonjour " ++ name ++ ", tu as " ++ show age ++ " ans !"`**

   * `++` concatène les chaînes.
   * `show` convertit l’âge (un `Int`) en `String` pour pouvoir l’afficher.

4. **`main`**

   * On crée un exemple avec `"Alice"` et `25`.
   * Puis on affiche le message avec `putStrLn`.

---

###  Exemple de sortie

```
Bonjour Alice, tu as 25 ans !
```

---
