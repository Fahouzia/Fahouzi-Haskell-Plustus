HC1T2 - Tâche 2 : Exemple de fonction pure


CODE 

```haskell
-- Définition de la fonction pour calculer l'aire d'un cercle
circleArea :: Floating a => a -> a
circleArea r = pi * r * r

-- Fonction principale avec un appel à circleArea avec r = 5
main :: IO ()
main = print (circleArea 5)
```



```haskell
-- Définition de la fonction pour calculer l'aire d'un cercle
circleArea :: Floating a => a -> a
```

1. **`circleArea`**
   C’est le nom de la fonction. On peut l’appeler comme on veut, mais ici c’est clair : elle calcule l’aire d’un cercle.

2. **`::` (double deux-points)**
   Ce symbole sépare le nom de la fonction de sa **signature de type**.
   Cela signifie « voici le type de données que la fonction prend et retourne ».

3. **`Floating a => a -> a`**

   * `a` est un type générique, ce qui veut dire que la fonction marche pour différents types numériques (par exemple, `Float` ou `Double`).
   * `Floating a` est une **contrainte** qui dit que `a` doit être un type qui supporte les nombres à virgule flottante et les opérations comme la multiplication et la constante `pi`.
   * `a -> a` signifie que la fonction prend un argument de type `a` (le rayon) et retourne un résultat aussi de type `a` (l’aire).

---

```haskell
circleArea r = pi * r * r
```

1. **`circleArea r =`**
   On définit la fonction ici. Elle prend un argument qu’on appelle `r` (le rayon).

2. **`pi`**
   C’est une constante prédéfinie en Haskell qui vaut approximativement 3.14159. Elle représente π (pi) .

3. *`*`*
   C’est l’opérateur de multiplication.

4. **`r * r`**
   On multiplie le rayon `r` par lui-même pour obtenir `r²` (le carré du rayon).

5. **`pi * r * r`**
   On calcule donc l’aire du cercle avec la formule mathématique : **π × r²**.

---

```haskell
main :: IO ()
```

1. **`main`**
   C’est la fonction principale en Haskell — le point d’entrée de ton programme. C’est elle qui sera exécutée automatiquement.

2. **`:: IO ()`**
   La signature de type dit que `main` est une **action d’entrée/sortie** (`IO`) qui ne retourne rien de significatif (`()` signifie « unité », une valeur vide).

---

```haskell
main = print (circleArea 5)
```

1. **`print`**
   C’est une fonction qui affiche une valeur sur la console.

2. **`circleArea 5`**
   Ici on appelle la fonction `circleArea` avec `5` comme valeur pour le rayon `r`.

3. **`print (circleArea 5)`**
   Ça signifie :

   * d’abord calculer `circleArea 5` → `pi * 5 * 5` ≈ 78.5398,
   * puis afficher ce résultat dans la console.

* La fonction `circleArea` est **pure** : pour un même `r`, elle renverra toujours la même aire.
