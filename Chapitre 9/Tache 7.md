HC9T7 : Fonction pour calculer l’engagement

### CODE 
```haskell
data Tweet = Tweet
    { content  :: String
    , likes    :: Int
    , comments :: [Tweet]
    } deriving Show

engagement :: Tweet -> Int
engagement (Tweet _ likes comments) =
    likes + sum (map engagement comments)

main :: IO ()
main = do
    let comment1 = Tweet { content = "Super tweet !", likes = 2, comments = [] }
    let comment2 = Tweet { content = "Je suis d'accord.", likes = 1, comments = [] }

    let tweet = Tweet 
            { content = "Bonjour le monde !"
            , likes = 5
            , comments = [comment1, comment2]
            }

    print (engagement tweet)  -- Résultat attendu : 5 + 2 + 1 = 8
```

### 1️⃣ Rappel du type `Tweet`

```haskell
data Tweet = Tweet
    { content  :: String
    , likes    :: Int
    , comments :: [Tweet]
    } deriving Show
```

---

### 2️⃣ Définition de la fonction `engagement`

```haskell
engagement :: Tweet -> Int
engagement (Tweet _ likes comments) =
    likes + sum (map engagement comments)
```

**Explications ligne par ligne :**

1. `engagement :: Tweet -> Int`

   * La fonction prend un `Tweet` et retourne un `Int` représentant le total des likes (engagement).

2. `engagement (Tweet _ likes comments)`

   * On fait un **pattern matching** sur le constructeur `Tweet`.
   * `_` : on ignore le `content` (on n’en a pas besoin pour le calcul).
   * `likes` : nombre de likes du tweet.
   * `comments` : liste des commentaires.

3. `likes + sum (map engagement comments)`

   * `map engagement comments` : applique `engagement` à chaque commentaire (récursif).
   * `sum` : somme tous les engagements des commentaires.
   * On ajoute le `likes` du tweet principal pour obtenir l’engagement total.

---
