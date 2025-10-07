
```haskell
-- Définition de la fonction specialBirthday
specialBirthday :: Int -> String
specialBirthday 18 = "Félicitations pour ta majorité !"
specialBirthday 21 = "Bienvenue dans le club des 21 ans !"
specialBirthday 30 = "30 ans, le début de nouvelles aventures !"
specialBirthday _  = "Joyeux anniversaire !"

-- Exemples de test
main :: IO ()
main = do
    print (specialBirthday 18)  -- "Félicitations pour ta majorité !"
    print (specialBirthday 21)  -- "Bienvenue dans le club des 21 ans !"
    print (specialBirthday 25)  -- "Joyeux anniversaire !"
    print (specialBirthday 30)  -- "30 ans, le début de nouvelles aventures !"
```

On peut le réécrire avec **pattern matching** comme suit :

```haskell
specialBirthday :: Int -> String
specialBirthday 18 = "Félicitations pour ta majorité !"
specialBirthday 21 = "Bienvenue dans le club des 21 ans !"
specialBirthday 30 = "30 ans, le début de nouvelles aventures !"
specialBirthday _  = "Joyeux anniversaire !"
```

Explication :

* `specialBirthday 18 = ...` → si l’âge est exactement 18, renvoie ce message.
* `specialBirthday _ = ...` → le `_` est un **wildcard** : correspond à **tout autre âge**, c’est l’équivalent du `else`.
* Pas besoin de `if-else` : Haskell choisit le motif qui correspond le premier.

Tu peux tester la fonction avec :

```haskell
specialBirthday 18  -- "Félicitations pour ta majorité !"
specialBirthday 21  -- "Bienvenue dans le club des 21 ans !"
specialBirthday 25  -- "Joyeux anniversaire !"
specialBirthday 30  -- "30 ans, le début de nouvelles aventures !"
```

```haskell
-- Définition de la fonction specialBirthday
specialBirthday :: Int -> String
```

1. **Commentaire** : `--` indique un commentaire en Haskell, donc cette ligne n’est pas exécutée.
2. **Type de la fonction** : `specialBirthday :: Int -> String` signifie que la fonction prend un **entier** (`Int`, ici l’âge) en entrée et renvoie une **chaîne de caractères** (`String`) en sortie.

```haskell
specialBirthday 18 = "Félicitations pour ta majorité !"
```

* **Pattern matching** : ici, on dit que si l’âge est exactement `18`, alors la fonction renvoie `"Félicitations pour ta majorité !"`.
* Pas besoin de `if` : Haskell compare directement l’argument avec `18`.

```haskell
specialBirthday 21 = "Bienvenue dans le club des 21 ans !"
```

* Même principe : si l’âge est `21`, on renvoie ce message spécifique.

```haskell
specialBirthday 30 = "30 ans, le début de nouvelles aventures !"
```

* Idem : si l’âge est `30`, on renvoie ce message particulier.

```haskell
specialBirthday _  = "Joyeux anniversaire !"
```

* Le `_` est un **wildcard** : il correspond à **toute valeur qui n’a pas été capturée avant** (18, 21, 30).
* C’est l’équivalent du `else` dans un `if-else`.
* Ici, on renvoie `"Joyeux anniversaire !"` pour **tout autre âge**.

```haskell
-- Exemples de test
main :: IO ()
```

* **Commentaire** : on indique que ce qui suit sert à tester la fonction.
* `main :: IO ()` définit le point d’entrée du programme.
* `IO ()` signifie que cette fonction effectue des actions d’entrée/sortie (`print`) et ne renvoie rien d’utile.

```haskell
main = do
    print (specialBirthday 18)  -- "Félicitations pour ta majorité !"
    print (specialBirthday 21)  -- "Bienvenue dans le club des 21 ans !"
    print (specialBirthday 25)  -- "Joyeux anniversaire !"
    print (specialBirthday 30)  -- "30 ans, le début de nouvelles aventures !"
```

* `do` introduit une **séquence d’actions IO**.
* `print (...)` affiche la valeur renvoyée par la fonction dans la console.
* Chaque ligne teste `specialBirthday` avec un âge différent pour montrer tous les cas possibles.

