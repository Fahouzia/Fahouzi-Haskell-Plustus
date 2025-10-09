

### 1️⃣ Rappel du type `Sequence`

```haskell
data Sequence a = EmptyNode | Node a (Sequence a) deriving Show
```

* `EmptyNode` → fin de la séquence
* `Node a next` → nœud contenant `a` et un lien vers le nœud suivant

---

### 2️⃣ Définition de `elemSeq`

```haskell
elemSeq :: Eq a => a -> Sequence a -> Bool
elemSeq _ EmptyNode       = False
elemSeq x (Node y next)
    | x == y    = True
    | otherwise = elemSeq x next
```

**Explications ligne par ligne :**

1. `elemSeq :: Eq a => a -> Sequence a -> Bool`

   * La fonction prend un élément de type `a` et une `Sequence a`.
   * Retourne `True` si l’élément est présent, `False` sinon.
   * `Eq a =>` signifie que les éléments doivent être **comparables avec `==`**.

2. `elemSeq _ EmptyNode = False`

   * Si on arrive à la fin de la séquence, l’élément n’est pas présent.

3. `elemSeq x (Node y next)`

   * On compare `x` avec la valeur du nœud actuel `y`.
   * `x == y` → True
   * Sinon → on continue à vérifier dans le nœud suivant `next` (récursif).

---
CODE 

```haskell
data Sequence a = EmptyNode | Node a (Sequence a) deriving Show

elemSeq :: Eq a => a -> Sequence a -> Bool
elemSeq _ EmptyNode       = False
elemSeq x (Node y next)
    | x == y    = True
    | otherwise = elemSeq x next

main :: IO ()
main = do
    let seq1 = Node 1 (Node 2 (Node 3 EmptyNode))
    
    print (elemSeq 2 seq1)  -- Résultat : True
    print (elemSeq 5 seq1)  -- Résultat : False
```

---
