HC4T5 - Tâche 5 : Ajouter un cas générique avec un message personnalisé

```haskell
-- Définition de la fonction specialBirthday
specialBirthday :: Int -> String
specialBirthday 18 = "Félicitations pour ta majorité !"
specialBirthday 21 = "Bienvenue dans le club des 21 ans !"
specialBirthday 30 = "30 ans, le début de nouvelles aventures !"
specialBirthday age = "Joyeux anniversaire ! Tu as " ++ show age ++ " ans."

-- Exemples de test
main :: IO ()
main = do
    print (specialBirthday 18)  -- "Félicitations pour ta majorité !"
    print (specialBirthday 21)  -- "Bienvenue dans le club des 21 ans !"
    print (specialBirthday 25)  -- "Joyeux anniversaire ! Tu as 25 ans."
    print (specialBirthday 30)  -- "30 ans, le début de nouvelles aventures !"
```

### Explication :

```haskell
specialBirthday age = "Joyeux anniversaire ! Tu as " ++ show age ++ " ans."
```

1. **`age`** : capture tout âge qui ne correspond pas aux cas 18, 21 ou 30.
2. **`show age`** : convertit l’entier `age` en `String` pour pouvoir le concaténer.
3. **`++`** : opérateur de concaténation de chaînes en Haskell.
4. Résultat : le message contient maintenant l’âge réel.

```haskell
-- Définition de la fonction specialBirthday
specialBirthday :: Int -> String
```

1. **Commentaire** : `--` indique que cette ligne est un commentaire et n’est pas exécutée.
2. **Type de la fonction** : `specialBirthday :: Int -> String` signifie que la fonction prend un **entier** (`Int`, l’âge) et renvoie une **chaîne de caractères** (`String`).

```haskell
specialBirthday 18 = "Félicitations pour ta majorité !"
```

* **Pattern matching** : si l’âge est exactement `18`, la fonction renvoie `"Félicitations pour ta majorité !"`.

```haskell
specialBirthday 21 = "Bienvenue dans le club des 21 ans !"
```

* Si l’âge est exactement `21`, on renvoie ce message particulier.

```haskell
specialBirthday 30 = "30 ans, le début de nouvelles aventures !"
```

* Si l’âge est exactement `30`, on renvoie ce message spécifique.

```haskell
specialBirthday age = "Joyeux anniversaire ! Tu as " ++ show age ++ " ans."
```

* **`age`** : capture tout âge qui **n’a pas été défini** dans les cas précédents (c’est le cas générique).
* **`show age`** : convertit l’entier `age` en chaîne de caractères (`String`) pour pouvoir l’utiliser dans le message.
* **`++`** : opérateur de concaténation de chaînes en Haskell.
* Résultat : le message inclut maintenant l’âge réel, par exemple `"Joyeux anniversaire ! Tu as 25 ans."`.

```haskell
-- Exemples de test
main :: IO ()
```

* Commentaire pour indiquer que ce qui suit sert à tester la fonction.
* `main :: IO ()` définit le point d’entrée du programme. `IO ()` signifie que cette fonction effectue des actions d’entrée/sortie (affichage) et ne renvoie rien d’autre.

```haskell
main = do
    print (specialBirthday 18)  -- "Félicitations pour ta majorité !"
    print (specialBirthday 21)  -- "Bienvenue dans le club des 21 ans !"
    print (specialBirthday 25)  -- "Joyeux anniversaire ! Tu as 25 ans."
    print (specialBirthday 30)  -- "30 ans, le début de nouvelles aventures !"
```

* `do` : introduit une **séquence d’actions IO**.
* `print (...)` : affiche dans la console le résultat de `specialBirthday` pour différents âges.
* Chaque ligne teste la fonction pour un cas précis et montre comment le message générique s’adapte à un âge non prédéfini (ici `25`).

