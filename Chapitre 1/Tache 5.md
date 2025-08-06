HC1T5 - Tâche 5 : Paresse en Haskell

CODE 

```haskell
-- infiniteNumbers : génère la liste infinie des nombres entiers positifs à partir de 1
infiniteNumbers :: [Integer]
infiniteNumbers = [1..]

-- Fonction pour extraire les n premiers éléments d'une liste
takeN :: Int -> [a] -> [a]
takeN n xs = take n xs

-- Exemple dans main
main :: IO ()
main = do
    let first10 = takeN 10 infiniteNumbers
    print first10
```

EXPLICATION 

### 1. `infiniteNumbers :: [Integer]`

* `infiniteNumbers` est une **valeur** qui représente une **liste infinie**.
* Son type est `[Integer]` : une liste de nombres entiers de type `Integer`.
* En Haskell, la notation `[1..]` signifie « la liste des entiers à partir de 1 jusqu’à l’infini . l'infini pour dire jusqu'au  nombre n entré par l'utilisateur».
* **C’est possible grâce à l’évaluation paresseuse (lazy evaluation)** : Haskell ne calcule pas toute la liste d’un coup, mais seulement les éléments dont on a besoin.


### 2. `takeN :: Int -> [a] -> [a]`

* `takeN` est une fonction qui prend :

  * un entier `n` (nombre d’éléments à prendre),
  * une liste `xs` de n’importe quel type `a`,
  * et retourne une **liste des `n` premiers éléments**.
* Elle utilise la fonction prédéfinie `take` de Haskell qui fait exactement ça.


### 3. Dans `main`

* On crée une variable `first10` qui contient les 10 premiers nombres de la liste infinie.
* Puis on affiche `first10`.
* La paresse de Haskell permet ici d’extraire uniquement ce dont on a besoin de la liste infinie, évitant une boucle infinie.


