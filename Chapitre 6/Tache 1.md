HC6T1 : Factorielle (récursif)

---

### Étape 1 : Définir le type

La factorielle prend un entier et retourne un entier.

```haskell
factorial :: Integer -> Integer
```

* On utilise `Integer` plutôt que `Int` pour gérer de très grands nombres.

---

### Étape 2 : Cas de base

La factorielle de 0 est définie comme 1.

```haskell
factorial 0 = 1
```

---

### Étape 3 : Cas récursif

Pour un nombre `n > 0`, la factorielle est `n * factorial (n-1)`

```haskell
factorial n = n * factorial (n - 1)
```

---

### Code complet

```haskell
factorial :: Integer -> Integer
factorial 0 = 1
factorial n = n * factorial (n - 1)
```

---

### Explication

1. **factorial 0 = 1** → Cas de base pour arrêter la récursion.
2. **factorial n = n * factorial (n - 1)** → Appelle la fonction elle-même jusqu’à atteindre 0.

Exemples :

```haskell
factorial 5
-- Résultat : 120
factorial 0
-- Résultat : 1
```

---
