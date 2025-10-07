 HC4T3 - Définir une fonction gradeComment avec un main


```haskell
gradeComment :: Int -> String
gradeComment grade
    | grade >= 90 && grade <= 100 = "Excellent !"
    | grade >= 70 && grade <= 89  = "Bon travail !"
    | grade >= 50 && grade <= 69  = "Tu as réussi."
    | grade >= 0  && grade <= 49  = "Peut mieux faire."
    | otherwise                   = "Note invalide."

main :: IO ()
main = do
    putStrLn "Entrez la note (0 à 100) :"
    input <- getLine
    let grade = read input :: Int
    putStrLn (gradeComment grade)
```

### Explication :

* `gradeComment :: Int -> String`
  → la fonction prend une **note entière** et renvoie un **message**.
* Les **gardes (`|`)** permettent de tester plusieurs conditions.
* `otherwise` correspond à « tous les autres cas » (ici, note invalide).
* `read input :: Int` convertit la saisie clavier (texte) en un entier.

Exemple  :

```
Entrez la note (0 à 100) :
85
Bon travail !
```

Et pour :

```
Entrez la note (0 à 100) :
45
Peut mieux faire.
```
