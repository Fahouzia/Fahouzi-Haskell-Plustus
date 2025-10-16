HC12T7 : Calculer l’aire d’un cercle
---

###  **Objectif**

Créer une fonction `calculateCircleArea` qui calcule l’aire
d’un cercle à partir du rayon fourni par l’utilisateur, puis l’afficher dans la fonction `main`.

---

###  **Code 

```haskell

-- Définition de la fonction pour calculer l'aire
calculateCircleArea :: Float -> Float
calculateCircleArea radius = pi * radius * radius

-- Fonction principale
main :: IO ()
main = do
    putStrLn "=== Calcul de l’aire d’un cercle ==="
    putStrLn "Entrez le rayon du cercle :"
    input <- getLine                     -- Lire le rayon depuis l’utilisateur
    let radius = read input :: Float     -- Conversion en nombre
    let area = calculateCircleArea radius
    putStrLn ("L’aire du cercle est : " ++ show area)
```

---

### 🔍 **Explication pas à pas**

1. **`calculateCircleArea :: Float -> Float`**
   → Signature de type : la fonction prend un `Float` (le rayon) et renvoie un `Float` (l’aire).

2. **`calculateCircleArea radius = pi * radius * radius`**
   → Formule mathématique :
   [
   \text{Aire} = \pi \times r^2
   ]
   `pi` est une constante intégrée dans Haskell.

3. **Lecture de l’entrée utilisateur**

   ```haskell
   input <- getLine
   let radius = read input :: Float
   ```

   → On lit le texte tapé au clavier, puis on le convertit en nombre (`Float`).

4. **Affichage du résultat**

   ```haskell
   putStrLn ("L’aire du cercle est : " ++ show area)
   ```

   → `show` convertit le nombre en chaîne de caractères pour l’affichage.

---

###  **Exemple d’exécution**

```
=== Calcul de l’aire d’un cercle ===
Entrez le rayon du cercle :
3
L’aire du cercle est : 28.274334
```

*(puisque π × 3² = 28.274334)*

