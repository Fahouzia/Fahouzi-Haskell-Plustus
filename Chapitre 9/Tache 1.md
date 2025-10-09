HC9T1 : Définir un synonyme de type paramétrique

---

### **Code Haskell**

```haskell
-- 

-- On définit un synonyme de type paramétrique appelé Entity
-- Il prend un paramètre de type 'a' (générique)
type Entity a = (String, a)
-- Ici, le String représente l'adresse (ou le nom),
-- et 'a' représente le type d'entité (cela peut être Int, String, Bool, etc.)

-- Exemple d'utilisation :
main :: IO ()
main = do
    -- Une entité où 'a' est de type Int
    let user :: Entity Int
        user = ("Adresse: 12 Rue du Code", 12345)

    -- Une entité où 'a' est de type String
    let company :: Entity String
        company = ("Adresse: 42 Avenue Haskell", "OpenAI")

    -- Une entité où 'a' est de type Bool
    let sensor :: Entity Bool
        sensor = ("Adresse: Capteur-7", True)

    -- Affichage des entités
    putStrLn "=== Exemples d'entités (Entity a) ==="
    print user
    print company
    print sensor
```

---

###  **Explication**

1. **Ligne 4 :**

   ```haskell
   type Entity a = (String, a)
   ```

   * On crée un **synonyme de type** (avec `type`).
   * `Entity` est le **nouveau nom** du type.
   * `a` est un **paramètre de type générique** : il peut représenter n’importe quel type (comme `Int`, `String`, etc.).
   * `(String, a)` signifie qu’une entité est un **couple** composé :

     * d’une **adresse** (`String`),
     * et d’une **valeur d’entité** de type `a`.

2. **Dans `main` :**

   * On crée plusieurs entités avec des types différents :

     * `Entity Int` → un identifiant numérique.
     * `Entity String` → un nom d’entreprise.
     * `Entity Bool` → un état (vrai/faux).

3. **Exemple de sortie à l’exécution :**

   ```
   === Exemples d'entités (Entity a) ===
   ("Adresse: 12 Rue du Code",12345)
   ("Adresse: 42 Avenue Haskell","OpenAI")
   ("Adresse: Capteur-7",True)
   ```

---
