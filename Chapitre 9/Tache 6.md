HC9T6 : Définir un type de données récursif

**Explications :**
### 1️ Définition du type `Tweet`

```haskell
data Tweet = Tweet
    { content   :: String      -- Le texte du tweet
    , likes     :: Int         -- Nombre de likes
    , comments  :: [Tweet]     -- Liste des commentaires, eux-mêmes des tweets
    } deriving Show
```
1. `data Tweet = Tweet`

   * Déclare un type nommé `Tweet`.

2. `{ content :: String }`

   * Champ `content` pour stocker le texte du tweet.

3. `{ likes :: Int }`

   * Champ `likes` pour stocker le nombre de likes.

4. `{ comments :: [Tweet] }`

   * Champ `comments` qui est une **liste de Tweets**.
   * C’est ce qui rend le type **récursif** : un tweet peut contenir des tweets.

5. `deriving Show`

   * Permet d’afficher facilement un tweet et ses commentaires.

---

### CODE 

```haskell
data Tweet = Tweet
    { content   :: String
    , likes     :: Int
    , comments  :: [Tweet]
    } deriving Show

main :: IO ()
main = do
    let comment1 = Tweet { content = "Super tweet !", likes = 2, comments = [] }
    let comment2 = Tweet { content = "Je suis d'accord.", likes = 1, comments = [] }

    let tweet = Tweet 
            { content = "Bonjour le monde !"
            , likes = 5
            , comments = [comment1, comment2]
            }

    print tweet
```
---

### 1️ Le type `Tweet`

```haskell
data Tweet = Tweet
    { content  :: String
    , likes    :: Int
    , comments :: [Tweet]
    } deriving Show
```

* **`Tweet`** est un **type de données**.

  * C’est une structure qu’on utilise pour représenter un **message avec son contenu, ses likes et ses commentaires**.
  * Ici, le mot `Tweet` sert **à la fois comme nom du type et comme constructeur pour créer un tweet**.

* `content :: String`

  * Le texte du tweet, par exemple `"Bonjour le monde !"`.

* `likes :: Int`

  * Le nombre de likes pour ce tweet.

* `comments :: [Tweet]`

  * Une **liste de tweets**.
  * C’est ce qui rend le type **récursif** : un tweet peut avoir des commentaires, et ces commentaires sont eux-mêmes des tweets.

---

### 2️Exemple 

```haskell
let comment1 = Tweet { content = "Super tweet !", likes = 2, comments = [] }
let tweet = Tweet { content = "Bonjour le monde !", likes = 5, comments = [comment1] }
```

* `comment1` est un tweet qui **n’a pas de commentaires** (liste vide `[]`).

* `tweet` est un tweet principal qui a **1 commentaire**, qui est `comment1`.

* Donc dans le code :

  * Le premier `Tweet` (le constructeur) crée un tweet.
  * Les champs `content`, `likes`, `comments` **décrivent les données à l’intérieur**.

---


