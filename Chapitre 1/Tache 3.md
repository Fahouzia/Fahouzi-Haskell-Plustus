HC1T3 - Tâche 3 : Vérifier si un nombre est supérieur à 18

CODE 
```haskell
-- Fonction qui vérifie si un nombre est supérieur à 18
greaterThan18 :: (Ord a, Num a) => a -> Bool
greaterThan18 x = x > 18

-- Fonction principale pour tester avec 12 et 29
main :: IO ()
main = do
    print (greaterThan18 12)  -- Devrait afficher False
    print (greaterThan18 29)  -- Devrait afficher True
```


EXPLICATION 
1. *`greaterThan18`*: nom de la fonction.

2. *`:: (Ord a, Num a) => a -> Bool`*
  La fonction prend un argument de type `a` (un nombre), où `a` doit être à la fois un type numérique (`Num a`) et ordonnable (`Ord a`, pour pouvoir utiliser `>`).
  Elle renvoie un booléen (`Bool`) : `True` si supérieur à 18, sinon `False`.
greaterThan18 : c’est le nom de la fonction.

'::' : sépare le nom de la fonction de sa signature de type.

(Ord a, Num a) => :
C’est une contrainte de type qui dit que le type a doit être :

Num (un type numérique : Int, Float, Double, etc.)

Ord (un type ordonnable, donc on peut utiliser des opérateurs de comparaison comme >, <, >=, etc.)
Ces contraintes sont nécessaires pour pouvoir faire la comparaison x > 18.
4. **`greaterThan18 x = x > 18`** :
  On compare directement la valeur `x` au nombre 18 avec l’opérateur `>`.

5. dans le main on afichera true quand le nombre entré est superieur à 18 et false si le nombre est inferieur à 18.

