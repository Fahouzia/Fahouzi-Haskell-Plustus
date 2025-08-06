HC1T1 - Tâche 1 : Composition de fonctions


LE CODE :
```haskell
-- Fonction qui multiplie un nombre par 2
double :: Int -> Int
double x = x * 2

-- Fonction qui ajoute 1 à un nombre
increment :: Int -> Int
increment x = x + 1

-- Fonction qui applique double puis increment
doubleThenIncrement :: Int -> Int
doubleThenIncrement = increment . double

-- Exemple d'utilisation
main :: IO ()
main = do
    let nombre = 4
    putStrLn ("Nombre initial : " ++ show nombre)
    putStrLn ("Double : " ++ show (double nombre))
    putStrLn ("Résultat après doubleThenIncrement : " ++ show (doubleThenIncrement nombre))
```

---

EXPLICATION 

1. Ligne 1-2 : Déclaration de `double`

```haskell
double :: Int -> Int
double x = x * 2
```

* `double` est une fonction qui prend un `Int` et retourne un `Int`.En effet double prend un entier naturel  et retourne un entier .
* Elle prend un argument `x`, et retourne `x * 2` (donc le double).En effet le x est l'entier  à rendre et le retour cela x*2
* Exemple : `double 4` renvoie `8`.

2. Ligne 4-5 : Déclaration de `increment`
Incrémenter signifie augmenter une valeur de 1.
```haskell
increment :: Int -> Int
increment x = x + 1
```

* `increment` prend un `Int`, retourne ce nombre augmenté de 1.
* Exemple : `increment 8` renvoie `9`.

 3. Ligne 7-8  Composition des deux fonctions

```haskell
doubleThenIncrement :: Int -> Int
doubleThenIncrement = increment . double
```

* Ici, on compose deux fonctions avec l'opérateur `.` (point).
* `(f . g) x` signifie `f (g x)` → on applique `g` d’abord, puis `f`.
* Donc : `doubleThenIncrement x = increment (double x)`
* Exemple : `doubleThenIncrement 4` → `increment (double 4)` → `increment 8` → `9`.

4. Ligne 10-14 : Programme principal (main)

```haskell
main :: IO ()
main = do
    let nombre = 4
    putStrLn ("Nombre initial : " ++ show nombre)
    putStrLn ("Double : " ++ show (double nombre))
    putStrLn ("Résultat après doubleThenIncrement : " ++ show (doubleThenIncrement nombre))
```

* `main` est le point d’entrée du programme.
* On définit `nombre = 4`.
* On affiche :

  * Le nombre initial (`4`).
  * Le résultat de `double 4` → `8`.
  * Le résultat de `doubleThenIncrement 4` → `9`.


5. le symbole . s’appelle l’opérateur de composition de fonctions.
Il permet de joindre deux fonctions, pour que le résultat de la première soit automatiquement envoyé dans la seconde.

6. -- permet  utilisé pour faire un commentaire sur une seule ligne.
Un commentaire est un texte dans le code qui n’est pas exécuté.
Il sert juste à expliquer ce que fait le code.

