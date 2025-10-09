HC8T7 : Types de données et description d’animaux

### SUJET

> Définir un nouveau type `Animal` avec les constructeurs `Dog String` et `Cat String`.
> Créer une fonction `describeAnimal :: Animal -> String` qui décrit l’animal.
> Créer des instances pour un chien et un chat.

---

### Code 

```haskell

-- Définition du type Animal
data Animal = Dog String | Cat String
  deriving Show

-- Fonction qui décrit l’animal
describeAnimal :: Animal -> String
describeAnimal (Dog name) = "C’est un chien nommé " ++ name ++ "."
describeAnimal (Cat name) = "C’est un chat nommé " ++ name ++ "."

-- Fonction principale pour tester
main :: IO ()
main = do
    let chien = Dog "Rex"
    let chat = Cat "Mimi"
    putStrLn (describeAnimal chien)
    putStrLn (describeAnimal chat)
```

---

###  Explication 

1. **`data Animal = Dog String | Cat String`**

   * On crée un **type de données algébrique** `Animal` qui peut être :

     * `Dog` avec un nom (`String`)
     * `Cat` avec un nom (`String`)
   * Exemple :
     `Dog "Rex"` ou `Cat "Mimi"`.

2. **`describeAnimal :: Animal -> String`**

   * C’est une fonction qui **prend un Animal** et **retourne une description textuelle**.

3. **`describeAnimal (Dog name)`**

   * Si l’animal est un `Dog`, on extrait le nom avec `name` et on construit une phrase.

4. **`describeAnimal (Cat name)`**

   * Même principe pour le chat.

5. **`main`**

   * On crée deux animaux : `chien` et `chat`.
   * On affiche leur description avec `putStrLn`.

---

###  Exemple de sortie

```
C’est un chien nommé Rex.
C’est un chat nommé Mimi.
```
