

```haskell
-- Définition du type BST
data BST a = EmptyBST 
           | NodeBST a (BST a) (BST a)
           deriving Show

-- Fonction pour insérer un élément dans le BST
insertBST :: Ord a => a -> BST a -> BST a
insertBST x EmptyBST = NodeBST x EmptyBST EmptyBST
insertBST x (NodeBST y left right)
    | x < y     = NodeBST y (insertBST x left) right
    | x > y     = NodeBST y left (insertBST x right)
    | otherwise = NodeBST y left right  -- Pas de doublons

-- Fonction pour vérifier si un élément est présent
elemBST :: Ord a => a -> BST a -> Bool
elemBST _ EmptyBST = False
elemBST x (NodeBST y left right)
    | x == y    = True
    | x < y     = elemBST x left
    | otherwise = elemBST x right

-- Exemple complet dans main
main :: IO ()
main = do
    let bst0 = EmptyBST
    let bst1 = insertBST 5 bst0
    let bst2 = insertBST 3 bst1
    let bst3 = insertBST 7 bst2
    let bst4 = insertBST 4 bst3

    print bst4                     -- Affiche l’arbre complet
    print (elemBST 4 bst4)         -- True
    print (elemBST 10 bst4)        -- False
```

---

**ExplicationS :**

1. `insertBST` : insère un élément en respectant la propriété BST (gauche < nœud < droite).
2. `elemBST` : recherche un élément dans l’arbre.
3. `main` : crée un BST, insère plusieurs valeurs et teste la recherche.

---


### 1️⃣ Définition du type `BST`

```haskell
data BST a = EmptyBST 
           | NodeBST a (BST a) (BST a)
           deriving Show
```

**Explications ligne par ligne :**

1. `data BST a`

   * Déclare un type **paramétrique** `BST` avec des éléments de type `a`.

2. `EmptyBST`

   * Représente un arbre vide.

3. `NodeBST a (BST a) (BST a)`

   * Représente un **nœud** avec :

     * `a` : la valeur du nœud
     * `(BST a)` : le sous-arbre gauche
     * `(BST a)` : le sous-arbre droit
   * Cela permet de construire **un arbre récursif**.

4. `deriving Show`

   * Permet d’afficher facilement l’arbre.

---

### 2️⃣ Exemple d’un arbre BST

```haskell
main :: IO ()
main = do
    -- Créer un BST simple : 
    --       5
    --      / \
    --     3   7
    let bst = NodeBST 5 
                (NodeBST 3 EmptyBST EmptyBST) 
                (NodeBST 7 EmptyBST EmptyBST)
    
    print bst
```

**Résultat attendu :**

```
NodeBST 5 (NodeBST 3 EmptyBST EmptyBST) (NodeBST 7 EmptyBST EmptyBST)
```

---

### 3️⃣ Comment ça fonctionne

* Chaque `NodeBST` contient une **valeur et deux sous-arbres**.
* Les sous-arbres peuvent eux-mêmes être vides (`EmptyBST`) ou contenir d’autres nœuds.
* C’est exactement la structure d’un **arbre binaire de recherche**, où :

  * Le sous-arbre gauche contient des valeurs **inférieures** à la valeur du nœud.
  * Le sous-arbre droit contient des valeurs **supérieures**.

---
