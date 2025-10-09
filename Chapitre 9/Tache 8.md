HC9T8 : Définir un type récursif Sequence
---

### 1️⃣ Définition du type `Sequence`

```haskell
data Sequence a = EmptyNode | Node a (Sequence a) deriving Show
```

**Explications :**

1. `data Sequence a`

   * Déclare un type **paramétrique** `Sequence` avec des éléments de type `a`.

2. `EmptyNode`

   * Représente la **fin de la séquence** (équivalent de `null` ou `nil` dans d’autres langages).

3. `Node a (Sequence a)`

   * Représente un **nœud contenant une valeur `a` et un lien vers le nœud suivant**.
   * C’est **récursif**, car le second champ est de type `Sequence a`.

4. `deriving Show`

   * Permet d’afficher facilement une séquence.

---

### 2️⃣ Exemple d’une séquence

```haskell
main :: IO ()
main = do
    -- Créer une séquence de trois éléments : 1 -> 2 -> 3
    let seq1 = Node 1 (Node 2 (Node 3 EmptyNode))
    
    print seq1
```

**Résultat attendu :**

```
Node 1 (Node 2 (Node 3 EmptyNode))
```

---

### 3️⃣ Comment ça fonctionne

* `Node 1 (Node 2 (Node 3 EmptyNode))`

  * Premier nœud : valeur `1`, pointe vers le nœud suivant `Node 2 ...`
  * Deuxième nœud : valeur `2`, pointe vers le nœud suivant `Node 3 ...`
  * Troisième nœud : valeur `3`, pointe vers `EmptyNode` → fin de la séquence


---
