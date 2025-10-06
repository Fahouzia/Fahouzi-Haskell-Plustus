HC3T4 - Tâche 4 : Calculer l’aire d’un triangle avec la formule de Héron

```haskell
-- Définition de la fonction triangleArea
triangleArea :: Float -> Float -> Float -> Float
triangleArea a b c =
    let s = (a + b + c) / 2  -- demi-périmètre
    in sqrt (s * (s - a) * (s - b) * (s - c))  -- formule de Héron

-- Tests
main :: IO ()
main = do
    print (triangleArea 3 4 5)  -- Résultat attendu : 6.0
    print (triangleArea 7 8 9)  -- Résultat attendu : ≈ 26.83
```

Explication :

* **Signature de type :**

  ```haskell
  triangleArea :: Float -> Float -> Float -> Float
  ```

  → La fonction prend trois côtés de type `Float` et renvoie un `Float` (l’aire).

* **`let s = (a + b + c) / 2`**
  → On calcule le **demi-périmètre** du triangle.

* **`sqrt (s * (s - a) * (s - b) * (s - c))`**
  → C’est la **formule de Héron** pour trouver l’aire à partir des trois côtés.

---

Principe mathématique – Formule de Héron

La **formule de Héron** permet de calculer **l’aire d’un triangle** uniquement à partir de ses **trois côtés** ( a, b, c ), **sans avoir besoin d’un angle**.

### 🔹 Étapes :

1. On calcule d’abord le **demi-périmètre** du triangle :
   [
   s = \frac{a + b + c}{2}
   ]

2. Puis on applique la formule :
   [
   \text{Aire} = \sqrt{s(s - a)(s - b)(s - c)}
   ]

Cette formule vient de la géométrie : elle découle du théorème de Pythagore et du lien entre côtés et angles, mais simplifiée pour ne dépendre que des longueurs.

---

## Traduction en Haskell

Voici le code :

```haskell
triangleArea :: Float -> Float -> Float -> Float
triangleArea a b c =
    let s = (a + b + c) / 2
    in sqrt (s * (s - a) * (s - b) * (s - c))
```

 Explication pus c :

1. **Signature de type**

   ```haskell
   triangleArea :: Float -> Float -> Float -> Float
   ```

   * La fonction prend **trois nombres à virgule (Float)** représentant les côtés `a`, `b` et `c`.
   * Elle **retourne** aussi un `Float` : l’aire du triangle.

2. **Définition de la fonction**

   ```haskell
   triangleArea a b c = ...
   ```

   * Ici, `a`, `b`, et `c` sont les **paramètres** de la fonction.

3. **Calcul du demi-périmètre**

   ```haskell
   let s = (a + b + c) / 2
   ```

   * Le mot-clé **`let`** permet de définir une **variable locale** `s`.
   * On additionne les trois côtés, puis on divise par 2 pour obtenir le demi-périmètre.

4. **Calcul de l’aire**

   ```haskell
   in sqrt (s * (s - a) * (s - b) * (s - c))
   ```

   * Le mot-clé **`in`** indique ce que la fonction doit **retourner**.
   * **`sqrt`** est la fonction racine carrée.
   * On applique directement la **formule de Héron** :
     ( \sqrt{s(s - a)(s - b)(s - c)} )

---

 Exemples pratiques

### Exemple 1 :

```haskell
triangleArea 3 4 5
```

* ( s = (3 + 4 + 5) / 2 = 6 )
* ( \text{Aire} = \sqrt{6(6 - 3)(6 - 4)(6 - 5)} = \sqrt{36} = 6 )

✅ Résultat : **6.0**

---

### Exemple 2 :

```haskell
triangleArea 7 8 9
```

* ( s = (7 + 8 + 9) / 2 = 12 )
* ( \text{Aire} = \sqrt{12(12 - 7)(12 - 8)(12 - 9)} = \sqrt{12 × 5 × 4 × 3} = \sqrt{720} ≈ 26.83 )

✅ Résultat : **26.83**

---

 Remarque importante

Cette formule ne fonctionne **que si les trois côtés peuvent former un triangle**, c’est-à-dire :
[
a + b > c,\quad a + c > b,\quad b + c > a
]
Sinon, le résultat sous la racine devient négatif → erreur mathématique.
