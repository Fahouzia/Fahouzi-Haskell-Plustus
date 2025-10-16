 **HC11T5 : la fonction `guessWhat'sInside`** pour la classe **`Container`** 

Cette fonction doit :

* fonctionner **avec n’importe quel type de conteneur** (`Box`, `Present`, etc.) ;
* prendre un conteneur et une valeur à rechercher ;
* vérifier si cet élément est **contenu dedans**, puis **afficher un message approprié**.

---

## Code 
```haskell
-- Définition du type Box
data Box a = Empty | Has a deriving (Show, Eq)

-- Définition du type Present
data Present a = NoPresent | Wrap a deriving (Show, Eq)

-- Définition de la classe Container
class Container c where
    isEmpty  :: c a -> Bool
    contains :: (Eq a) => c a -> a -> Bool
    replace  :: c a -> a -> c a

-- Instance de Container pour Box
instance Container Box where
    isEmpty Empty      = True
    isEmpty (Has _)    = False

    contains Empty _   = False
    contains (Has x) y = x == y

    replace Empty newVal    = Has newVal
    replace (Has _) newVal  = Has newVal

-- Instance de Container pour Present
instance Container Present where
    isEmpty NoPresent    = True
    isEmpty (Wrap _)     = False

    contains NoPresent _ = False
    contains (Wrap x) y  = x == y

    replace NoPresent newVal = Wrap newVal
    replace (Wrap _) newVal  = Wrap newVal

-- Fonction générique guessWhat'sInside
guessWhat'sInside :: (Container c, Eq a, Show a) => c a -> a -> String
guessWhat'sInside cont item
    | isEmpty cont       = " Le conteneur est vide."
    | contains cont item = " Trouvé ! L'élément " ++ show item ++ " est à l'intérieur."
    | otherwise           = " L'élément " ++ show item ++ " n'est pas dans le conteneur."

-- Programme principal pour tester
main :: IO ()
main = do
    let b1 = Empty
    let b2 = Has 42
    let p1 = NoPresent
    let p2 = Wrap "Livre"

    putStrLn "=== Test de guessWhat'sInside ===\n"

    print (guessWhat'sInside b1 42)
    print (guessWhat'sInside b2 42)
    print (guessWhat'sInside b2 99)
    print (guessWhat'sInside p1 "Livre")
    print (guessWhat'sInside p2 "Livre")
    print (guessWhat'sInside p2 "Chaussures")
```

---

##  Explication pas à pas

### 1️⃣ Classe `Container`

On réutilise la même classe que dans les exercices précédents :

```haskell
class Container c where
    isEmpty  :: c a -> Bool
    contains :: (Eq a) => c a -> a -> Bool
    replace  :: c a -> a -> c a
```

Cette classe définit les opérations qu’un conteneur doit pouvoir faire.

---

### 2️ Instances pour `Box` et `Present`

On garde les définitions déjà faites :

* **`Box a`** → `Empty` ou `Has a`
* **`Present a`** → `NoPresent` ou `Wrap a`

Elles implémentent toutes les trois méthodes `isEmpty`, `contains`, et `replace`.

---

### 3️ Fonction `guessWhat'sInside`

```haskell
guessWhat'sInside :: (Container c, Eq a, Show a) => c a -> a -> String
```

* Elle est **générique** : elle fonctionne avec **tout type `c`** qui fait partie de la classe `Container`.
* `(Eq a, Show a)` permet de comparer et d’afficher les éléments.
* Elle vérifie trois cas :

```haskell
guessWhat'sInside cont item
    | isEmpty cont       = " Le conteneur est vide."
    | contains cont item = " Trouvé ! L'élément " ++ show item ++ " est à l'intérieur."
    | otherwise           = " L'élément " ++ show item ++ " n'est pas dans le conteneur."
```

| Cas            | Résultat                                             |
| -------------- | ---------------------------------------------------- |
| Conteneur vide | affiche “ Le conteneur est vide.”                  |
| Élément trouvé | affiche “ Trouvé ! …”                              |
| Élément absent | affiche “ L’élément … n’est pas dans le conteneur.” |

---

### 4️⃣ Fonction `main`

On crée quelques conteneurs :

```haskell
let b1 = Empty
let b2 = Has 42
let p1 = NoPresent
let p2 = Wrap "Livre"
```

Puis on teste plusieurs cas avec `guessWhat'sInside`.

---

##  Résultat attendu

```
=== Test de guessWhat'sInside ===

" Le conteneur est vide."
" Trouvé ! L'élément 42 est à l'intérieur."
" L'élément 99 n'est pas dans le conteneur."
" Le conteneur est vide."
" Trouvé ! L'élément \"Livre\" est à l'intérieur."
" L'élément \"Chaussures\" n'est pas dans le conteneur."
```

---

##  Résumé

| Élément             | Rôle                                                               |
| ------------------- | ------------------------------------------------------------------ |
| `Container`         | Classe générique définissant les opérations communes               |
| `Box`, `Present`    | Deux types concrets de conteneurs                                  |
| `guessWhat'sInside` | Fonction générique qui vérifie si un élément est dans un conteneur |
| `main`              | Programme de test complet                                          |

