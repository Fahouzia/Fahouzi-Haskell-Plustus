HC10T5 : Classe de type ShowDetailed


 **Code :**

```haskell
-- HC10T5 : Classe de type ShowDetailed

-- Définition de la classe ShowDetailed
class ShowDetailed a where
    showDetailed :: a -> String

-- Définition du type User
data User = User {
    userId :: Int,
    name :: String,
    email :: String
} deriving (Show)

-- Implémentation de la classe ShowDetailed pour User
instance ShowDetailed User where
    showDetailed (User id name email) =
        "=== Détails de l'utilisateur ===\n"
        ++ "Identifiant : " ++ show id ++ "\n"
        ++ "Nom         : " ++ name ++ "\n"
        ++ "Email       : " ++ email ++ "\n"
        ++ "==============================="

-- Fonction principale pour tester
main :: IO ()
main = do
    let user1 = User 1 "Ali" "ali@example.com"
    let user2 = User 2 "Fahouzia" "fahouzia@example.com"

    putStrLn (showDetailed user1)
    putStrLn ""
    putStrLn (showDetailed user2)
```

---

###  **Explication pas à pas :**

1. **Création de la classe `ShowDetailed`**

   ```haskell
   class ShowDetailed a where
       showDetailed :: a -> String
   ```

   * Cette classe définit une **fonction de conversion personnalisée** (`showDetailed`)
     qui doit renvoyer une description textuelle complète de l’objet.

2. **Définition du type `User`**

   ```haskell
   data User = User {
       userId :: Int,
       name :: String,
       email :: String
   } deriving (Show)
   ```

   * `User` est un **type enregistrement** avec trois champs :

     * `userId` : identifiant unique (type `Int`)
     * `name` : nom de l’utilisateur (type `String`)
     * `email` : adresse email (type `String`)

3. **Implémentation de la classe pour `User`**

   ```haskell
   instance ShowDetailed User where
       showDetailed (User id name email) = ...
   ```

   * On extrait les champs du constructeur `User` directement dans les paramètres.
   * On retourne une chaîne bien formatée décrivant l’utilisateur.

4. **Fonction `main` pour tester**

   * On crée deux instances (`user1` et `user2`).
   * On affiche leur description avec `showDetailed`.

---

###  **Sortie attendue dans le terminal :**

```
=== Détails de l'utilisateur ===
Identifiant : 1
Nom         : Ali
Email       : ali@example.com
===============================

=== Détails de l'utilisateur ===
Identifiant : 2
Nom         : Fahouzia
Email       : fahouzia@example.com
===============================
```

---
