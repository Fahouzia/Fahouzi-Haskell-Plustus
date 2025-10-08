En Haskell,
l’opérateur `$` permet d’éviter les parenthèses en changeant la priorité d’évaluation. On peut donc réécrire la fonction comme ceci :

```haskell
result = sum $ map (*2) $ filter (>3) [1..10]
```

Explication :

* `filter (>3) [1..10]` sélectionne les nombres supérieurs à 3 → `[4,5,6,7,8,9,10]`
* `map (*2)` double chaque élément → `[8,10,12,14,16,18,20]`
* `sum` fait la somme de tous les éléments → `98`

L’opérateur `$` évite les parenthèses imbriquées et rend l’expression plus lisible.
