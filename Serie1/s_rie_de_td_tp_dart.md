# Série N°1 : Premiers pas, types et conditions

> **Durée TD :** 40 min | **Durée TP :** 80 min  
> **Chapitre couvert :** Sections 1 à 3 (Premiers pas, variables et types, opérateurs et conditions)  
> **Outils :** DartPad ([dartpad.dev](https://dartpad.dev)) pour le TD ; Dart SDK + VS Code (`dart run`) pour le TP.

---

## 🎯 Objectifs
À la fin de cette série, vous saurez :
- Écrire et exécuter un programme Dart.
- Choisir le bon **type** de donnée.
- Utiliser les **opérateurs**.
- Lire une saisie clavier et prendre des décisions avec `if`, `switch` et l'opérateur ternaire.

---

## 📝 Partie A -- TD (Papier / Réponses écrites) — *40 min*

### Exercice 1 : Prédire les résultats (*10 min*)
*Donnez le résultat affiché par chaque instruction (écrivez `erreur` si le code est refusé).*

| N° | Instruction(s) | Votre réponse |
| :---: | :--- | :--- |
| **1** | `print(10 / 4);` | <!-- Écrire la réponse ici --> |
| **2** | `print(10 ~/ 4);` | <!-- Écrire la réponse ici --> |
| **3** | `print(10 % 4);` | <!-- Écrire la réponse ici --> |
| **4** | `print('Dart' + ' ' + 'MST');` | <!-- Écrire la réponse ici --> |
| **5** | `print('2' + '3');` | <!-- Écrire la réponse ici --> |
| **6** | `print(2 + 3 * 4 - 1);` | <!-- Écrire la réponse ici --> |
| **7** | `int x = 5; x += 3; x *= 2; print(x);` | <!-- Écrire la réponse ici --> |
| **8** | `print(5 > 3 && 2 > 4);` | <!-- Écrire la réponse ici --> |
| **9** | `print(!(5 == 5) \|\| 3 < 4);` | <!-- Écrire la réponse ici --> |
| **10**| `String? s; print(s ?? 'vide');` | <!-- Écrire la réponse ici --> |

---

### Exercice 2 : Quel type pour quelle valeur ? (*7 min*)
*Indiquez le type Dart le plus adapté (`int`, `double`, `String`, `bool`) pour chaque valeur ou expression.*

| Valeur / Expression | Votre réponse | Valeur / Expression | Votre réponse |
| :--- | :--- | :--- | :--- |
| `42` | <!-- Type --> | `'42'` | <!-- Type --> |
| `3.14` | <!-- Type --> | `10 / 2` | <!-- Type --> |
| `true` | <!-- Type --> | `10 ~/ 2` | <!-- Type --> |
| `"Settat"` | <!-- Type --> | `7 > 3` | <!-- Type --> |

---

### Exercice 3 : Chasse aux erreurs (*8 min*)
*Le programme suivant contient **6 erreurs**. Repérez-les, indiquez la ligne, le type d'erreur (syntaxe, type, logique) et la correction.*

```dart
1: void main() {
2:   int age = 'vingt';
3:   double prix = 12,5;
4:   String nom = 'Sara";
5:   const tva = 0.2
6:   tva = 0.25;
7:   print('Age : ' + age);
8: }
```

#### Vos réponses :

| Ligne | Type d'erreur | Problème identifié | Correction proposée |
| :---: | :--- | :--- | :--- |
| **2** | <!-- Syntaxe/Type/Logique --> | <!-- Explication --> | `int age = 20;` |
| **3** | <!-- Syntaxe/Type/Logique --> | <!-- Explication --> | <!-- Correction --> |
| **4** | <!-- Syntaxe/Type/Logique --> | <!-- Explication --> | <!-- Correction --> |
| **5** | <!-- Syntaxe/Type/Logique --> | <!-- Explication --> | <!-- Correction --> |
| **6** | <!-- Syntaxe/Type/Logique --> | <!-- Explication --> | <!-- Correction --> |
| **7** | <!-- Syntaxe/Type/Logique --> | <!-- Explication --> | <!-- Correction --> |

---

### Exercice 4 : Conditions (*15 min*)

#### a) Trace de code
*Donnez le résultat des appels suivants selon la fonction ci-dessous :*

```dart
String mention(double m) {
  if (m >= 16) {
    return 'Très bien';
  } else if (m >= 14) {
    return 'Bien';
  } else if (m >= 12) {
    return 'Assez bien';
  } else if (m >= 10) {
    return 'Passable';
  } else {
    return 'Insuffisant';
  }
}
```

| Appel | `mention(17)` | `mention(13.99)` | `mention(10)` | `mention(9.5)` |
| :--- | :---: | :---: | :---: | :---: |
| **Résultat** | <!-- Rep1 --> | <!-- Rep2 --> | <!-- Rep3 --> | <!-- Rep4 --> |

#### b) Expressions booléennes
*Écrivez en Dart la condition qui vaut `true` lorsque :*

1. `a` est compris entre 10 et 20 (bornes incluses) :
```dart
// Votre réponse ici
```

2. `n` est un entier **pair et strictement positif** :
```dart
// Votre réponse ici
```

3. `annee` est une année **bissextile** (divisible par 4 mais pas par 100, ou divisible par 400) :
```dart
// Votre réponse ici
```

#### c) Réécriture
*Réécrivez la structure `if/else` suivante avec l'opérateur ternaire :*

```dart
String statut;
if (age >= 18) {
  statut = 'majeur';
} else {
  statut = 'mineur';
}
```

**Votre réécriture :**
```dart
// Votre code ici
```

---

## 💻 Partie B -- TP (Sur machine) — *80 min*

> 💡 **Consigne :** Créez un dossier `tp1` et enregistrez chaque exercice dans un fichier séparé (`tp1_ex1.dart`, etc.). Exécution : `dart run tp1_ex1.dart`.  
> *Note : Les exercices TP3 à TP5 utilisent `stdin` (non compatibles avec DartPad).*

---

### TP 1 : Environnement et premier programme (*10 min*)

1. **Version installée :**
   ```bash
   # Collez le résultat de `dart --version` ici
   ```

2. **Code de la carte de visite (`tp1_ex1.dart`) :**
```dart
// Collez votre code Dart ici
```

3. **Remarque sur l'erreur de syntaxe testée :**
   * <!-- Expliquez ce qu'a affiché le compilateur lors de l'oubli du ';' -->

---

### TP 2 : Calcul d'une facture (*15 min*)

- **Code source (`tp1_ex2.dart`) :**
```dart
// Collez votre code Dart ici
```

- **Question :** Pourquoi utiliser `const` plutôt que `var` pour la TVA ?
  > **Réponse :** <!-- Votre explication ici -->

---

### TP 3 : Moyenne et mention (*15 min*)

- **Code source (`tp1_ex3.dart`) :**
```dart
// Collez votre code Dart ici
```

---

### TP 4 : Calculatrice à deux opérandes (*20 min*)

- **Code source (`tp1_ex4.dart`) :**
```dart
// Collez votre code Dart ici
```

- **Bonus : Année bissextile (`tp1_ex4_bonus.dart`) :**
```dart
// Collez votre code Dart ici
```

---

### TP 5 : Conversion d'une durée (*20 min*)

- **Code source (`tp1_ex5.dart`) :**
```dart
// Collez votre code Dart ici
```

- **Défi (Gestion des pluriels et unités nulles) :**
```dart
// Collez le code du défi ici (optionnel)
```

---

## 📦 Livrable
Cochez les éléments à remettre :
- [ ] Le présent fichier Markdown complété
- [ ] Les 5 fichiers `.dart` dans le dossier `tp1`
- [ ] Une capture d'écran d'exécution du **TP3**