### **HC5T7 – Utilisation de `$`**

**Objectif :**

* Réécrire `result = sum (map (*2) (filter (>3) [1..10]))` **en utilisant `$`** pour éviter les parenthèses imbriquées.

**Code :**

```haskell
-- Utilisation de $ pour simplifier les parenthèses
result :: Int
result = sum $ map (*2) $ filter (>3) [1..10]

-- Fonction main pour tester
main :: IO ()
main = print result  -- Résultat : 92
```

---

### **Explication  :**

1. **Sans `$` :**

   ```haskell
   sum (map (*2) (filter (>3) [1..10]))
   ```

   * Haskell commence par `filter (>3) [1..10]` → `[4,5,6,7,8,9,10]`
   * Puis `map (*2)` → `[8,10,12,14,16,18,20]`
   * Puis `sum` → `92`

2. **Avec `$` :**

   ```haskell
   sum $ map (*2) $ filter (>3) [1..10]
   ```

   * L’opérateur `$` permet de **réduire les parenthèses**.
   * `f $ x` est équivalent à `f x`, mais avec priorité plus faible → simplifie la lecture.
   * Haskell lit :

     1. `filter (>3) [1..10]`
     2. `map (*2)` appliqué au résultat
     3. `sum` appliqué au résultat final

3. **Avantages :**

   * Code plus **lisible** et **compact**
   * Utile surtout pour des **chaînes de transformations de données**

---
