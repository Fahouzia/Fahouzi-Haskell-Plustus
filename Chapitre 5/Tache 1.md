HC5T1 : Utiliser applyTwice


### Étape 1 : Comprendre le problème

On a besoin d’une fonction, appelons-la `applyThrice`, qui :

1. Prend en entrée :

   * Une fonction `f :: Int -> Int`
   * Un entier `x :: Int`
2. Applique `f` **trois fois** sur `x`.

On peut utiliser `applyTwice` comme fonction auxiliaire. Typiquement, `applyTwice` est définie comme :

```haskell
applyTwice :: (a -> a) -> a -> a
applyTwice f x = f (f x)
```

Donc `applyTwice f x` applique `f` deux fois à `x`.

---

### Étape 2 : Définir `applyThrice`

On veut appliquer `f` trois fois. Une idée simple :

* On applique `applyTwice f` pour deux applications.
* Puis une dernière application avec `f`.

```haskell
applyThrice :: (Int -> Int) -> Int -> Int
applyThrice f x = f (applyTwice f x)
```

---

### Étape 3 : Exemple

Si on définit :

```haskell
increment :: Int -> Int
increment n = n + 1
```

Alors :

```haskell
applyThrice increment 5
-- Évaluation :
-- applyThrice increment 5 = increment (applyTwice increment 5)
-- applyTwice increment 5 = increment (increment 5) = 7
-- increment 7 = 8
-- Résultat final : 8
```

```haskell
-- Fonction applyTwice déjà définie
applyTwice :: (Int -> Int) -> Int -> Int
applyTwice f x = f (f x)

-- Fonction applyThrice qui applique une fonction trois fois
applyThrice :: (Int -> Int) -> Int -> Int
applyThrice f x = f (applyTwice f x)

-- Exemple d'utilisation
increment :: Int -> Int
increment n = n + 1

main :: IO ()
main = do
    print (applyThrice increment 5)  -- Affiche 8
```

Ce code applique `increment` trois fois à 5 et retourne 8.
