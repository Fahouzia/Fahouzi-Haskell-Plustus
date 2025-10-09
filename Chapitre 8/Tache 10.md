HC8T10 : Deriving Show pour Book


---

### à faire

> En utilisant `deriving Show`, définir un type `Book` avec les champs :
>
> * `title :: String`
> * `author :: String`
> * `year :: Int`
>
> Créer une instance de `Book` et l’afficher avec l’instance `Show`.

---

###  Code 

```haskell
-- HC8T10.hs

-- Définition du type Book avec la syntaxe d’enregistrement
data Book = Book
  { title  :: String
  , author :: String
  , year   :: Int
  } deriving (Show)  -- permet d'afficher directement un Book

-- Fonction principale pour tester
main :: IO ()
main = do
    -- Création d'une instance de Book
    let myBook = Book { title = "Apprendre Haskell", author = "John Doe", year = 2024 }
    
    -- Affichage grâce à l'instance Show
    putStrLn "Détails du livre :"
    print myBook
```

---

### Explication 

1. **Définition du type `Book`**

   ```haskell
   data Book = Book
     { title  :: String
     , author :: String
     , year   :: Int
     } deriving (Show)
   ```

   * On utilise la **syntaxe d’enregistrement** pour nommer les champs.
   * Le mot-clé `deriving (Show)` dit à Haskell de **générer automatiquement** une instance de la classe `Show`, ce qui permet d’afficher un `Book` avec `print`.

2. **Création d’un livre**

   ```haskell
   let myBook = Book { title = "Apprendre Haskell", author = "John Doe", year = 2024 }
   ```

   * On crée un enregistrement `Book` en précisant chaque champ.

3. **Affichage**

   ```haskell
   print myBook
   ```

   * Grâce à `deriving (Show)`, Haskell sait comment convertir `myBook` en texte pour l’afficher.

---

###  Exemple de sortie

```
Détails du livre :
Book {title = "Apprendre Haskell", author = "John Doe", year = 2024}
```

---
