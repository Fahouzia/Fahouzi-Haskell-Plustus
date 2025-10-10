### **HC5T6 – Fonction composition**

**Objectif :**

* Créer une fonction qui **prend une liste de nombres**, **met chaque nombre au carré**, puis **ne garde que les nombres pairs**.

**Code :**

```haskell
-- Définition de la fonction avec composition
evenSquares :: [Int] -> [Int]
evenSquares = filter even . map (^2)
-- Lire comme : "appliquer map (^2) puis filter even"

-- Fonction main pour tester
main :: IO ()
main = do
    print (evenSquares [1..10])   -- Résultat : [4,16,36,64,100]
    print (evenSquares [5,7,8])   -- Résultat : [64]
    print (evenSquares [])        -- Résultat : []
```

---

### **Explication :**

1. **`map (^2)`**

   * `map` applique une fonction à **chaque élément de la liste**.
   * Ici, `(^2)` élève chaque nombre au carré.
   * Exemple : `[1,2,3]` → `[1,4,9]`.

2. **`filter even`**

   * `filter` garde uniquement les éléments qui **satisfont la condition**.
   * `even` retourne `True` si le nombre est pair.
   * Exemple : `[1,4,9]` → `[4]`.

3. **Composition avec `(.)`**

   * `(filter even . map (^2))` = `\xs -> filter even (map (^2) xs)`
   * Haskell évalue **de droite à gauche** : `map (^2)` d’abord, puis `filter even`.
   * Avantage : **code plus lisible et sans variables intermédiaires**.

4. **Exemple concret :**

   * Entrée : `[1..10]`
   * Après `map (^2)` : `[1,4,9,16,25,36,49,64,81,100]`
   * Après `filter even` : `[4,16,36,64,100]`

---
