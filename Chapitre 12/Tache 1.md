HC12T1 : Afficher un message de bienvenue

## 🔹 Énoncé

> Créer un programme Haskell qui affiche
> **« Bienvenue dans la programmation Haskell ! »** dans le terminal.

---

## 🔹 Code complet (copiable)

```haskell
-- 

main :: IO ()
main = putStrLn "Bienvenue dans la programmation Haskell !"
```

---

## 🔹 Explication pas à pas

1. **`main :: IO ()`**

   * `main` est le point d’entrée du programme Haskell.
   * Le type `IO ()` indique que la fonction effectue une action d’entrée/sortie (ici, afficher du texte).

2. **`putStrLn`**

   * C’est une fonction standard qui affiche une chaîne de caractères suivie d’un saut de ligne (`\n`).
   * Syntaxe :

     ```haskell
     putStrLn "ton message"
     ```

3. **Exécution :**

   * Sauvegarde ton code dans un fichier `HC12T1.hs`.
   * Compile ou exécute directement avec GHCi :

     ```bash
     runhaskell HC12T1.hs
     ```
   * Résultat attendu :

     ```
     Bienvenue dans la programmation Haskell !
     ```


##  Programme (rappel)

Ton fichier s’appelle par exemple **`HC12T1.hs`** et contient ceci 

```haskell
-- HC12T1 : Afficher un message de bienvenue

main :: IO ()
main = putStrLn "Bienvenue dans la programmation Haskell !"
```

---

##  Étape 1 : Vérifier si Haskell est installé

Ouvre ton terminal et tape :

```bash
ghc --version
```

### 🔹 Si tu obtiens un résultat comme :

```
The Glorious Glasgow Haskell Compilation System, version 9.x.x
```

➡️ Haskell est bien installé 

### 🔹 Sinon, installe-le avec :

```bash
sudo apt update
sudo apt install ghc
```

---

## 🧾 Étape 2 : Aller dans le dossier contenant ton fichier

Par exemple, si ton fichier `HC12T1.hs` est sur ton Bureau :

```bash
cd ~/Bureau
```

ou s’il est dans un dossier spécifique :

```bash
cd ~/Documents/Haskell
```

---

## ⚙️ Étape 3 : Compiler le programme

Tape la commande :

```bash
ghc HC12T1.hs -o HC12T1
```

Cette commande fait deux choses :

* **Compile** le fichier `HC12T1.hs`
* **Crée un exécutable** nommé `HC12T1`

---

## ▶️ Étape 4 : Exécuter le programme

Toujours dans le même dossier, exécute :

```bash
./HC12T1
```

### 🔹 Résultat affiché :

```
Bienvenue dans la programmation Haskell !
```

---

##  Alternative : Exécution sans compilation

Tu peux aussi exécuter directement sans créer d’exécutable avec :

```bash
runhaskell HC12T1.hs
```

 Cela lance le fichier **directement dans l’interpréteur Haskell**.
C’est plus rapide pour tester de petits programmes.

---

##  Résumé rapide

| Étape     | Commande                  | Description            |
| :-------- | :------------------------ | :--------------------- |
| 1️⃣       | `ghc --version`           | Vérifie l’installation |
| 2️⃣       | `cd dossier`              | Va dans le dossier     |
| 3️⃣       | `ghc HC12T1.hs -o HC12T1` | Compile                |
| 4️⃣       | `./HC12T1`                | Exécute                |
|  Option | `runhaskell HC12T1.hs`    | Lance sans compiler    |

---


---
