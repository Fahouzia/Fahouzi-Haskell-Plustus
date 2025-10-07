HC4T7 - Tâche 7 : Ignorer des éléments dans une liste

```haskell
-- Fonction qui retourne le premier et le troisième élément d'une liste
firstAndThird :: [a] -> [a]
firstAndThird (x:_:z:_) = [x, z]
firstAndThird _         = []

-- Exemples de test
main :: IO ()
main = do
    print (firstAndThird [1,2,3,4,5])       -- [1,3]
    print (firstAndThird ["a","b","c","d"]) -- ["a","c"]
    print (firstAndThird [10])              -- []
```
### Explication :

```haskell
-- Définition de la fonction
firstAndThird :: [a] -> [a]
firstAndThird (x:_:z:_) = [x, z]  -- On prend le premier (x) et le troisième (z), on ignore le reste
firstAndThird _         = []      -- Cas où la liste a moins de 3 éléments
```


1. `firstAndThird :: [a] -> [a]`

   * Déclare que `firstAndThird` prend une liste de n’importe quel type `a` et retourne une liste du même type.

2. `firstAndThird (x:_:z:_) = [x, z]`

   * `(x:_:z:_)` utilise le **pattern matching** :

     * `x` : le premier élément de la liste
     * `_` : le deuxième élément (on l’ignore)
     * `z` : le troisième élément
     * `_` : tous les éléments restants (on les ignore aussi)
   * On retourne seulement `[x, z]`, le premier et le troisième élément.

3. `firstAndThird _ = []`

   * Cas générique pour les listes trop courtes (<3 éléments), on retourne une liste vide.

Exemples de tests :

```haskell
firstAndThird [1,2,3,4,5]  -- résultat : [1,3]
firstAndThird ["a","b","c","d"]  -- résultat : ["a","c"]
firstAndThird [10]  -- résultat : []
``
