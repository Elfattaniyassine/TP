# TP 1 : Premiers pas, types et conditions en Dart

**Durée TD :** 40 min | **Durée TP :** 80 min  
**Chapitre couvert :** Sections 1 à 3 (premiers pas, variables et types, opérateurs et conditions)  
**Outils nécessaires :** 
- [DartPad](https://dartpad.dev) (pour les exercices sans saisie clavier)
- Dart SDK + VS Code (`dart run`) pour les exercices avec `stdin`

---

## 🎯 Objectifs
À la fin de cette série, vous saurez :
* Écrire et exécuter un programme Dart.
* Choisir le bon **type** de donnée.
* Utiliser les **opérateurs**.
* Lire une saisie clavier (`stdin`).
* Prendre des décisions avec `if`, `switch` et l'opérateur ternaire.

---

## 📝 Partie A -- TD (Papier, sans ordinateur) - 40 min

### Exercice 1 : Prédire les résultats
Donnez le résultat affiché par chaque instruction (ou `erreur` si le code est refusé).

| N° | Instruction(s) | Résultat | Explication / Correction |
| :---: | :--- | :---: | :--- |
| **1** | `print(10 / 4);` | `2.5` | `/` renvoie toujours un `double` |
| **2** | `print(10 ~/ 4);` | `2` | Division entière |
| **3** | `print(10 % 4);` | `2` | Reste de la division ($10 = 2 \times 4 + 2$) |
| **4** | `print('Dart' + ' ' + 'MST');` | `Dart MST` | Concaténation de chaînes |
| **5** | `print('2' + '3');` | `23` | Concaténation de textes (pas une addition) |
| **6** | `print(2 + 3 * 4 - 1);` | `13` | Priorité de la multiplication ($2 + 12 - 1$) |
| **7** | `int x = 5; x += 3; x *= 2; print(x);` | `16` | $5 \to 8 \to 16$ |
| **8** | `print(5 > 3 && 2 > 4);` | `false` | `true && false` |
| **9** | `print(!(5 == 5) \|\| 3 < 4);` | `true` | `false \|\| true` |
| **10** | `String? s; print(s ?? 'vide');` | `vide` | `s` vaut `null`, la valeur par défaut est utilisée |

---

### Exercice 2 : Quel type pour quelle valeur ?
Indiquez le type Dart le plus adapté (`int`, `double`, `String`, `bool`) pour chaque valeur ou expression.

| Valeur | Type | Valeur | Type |
| :--- | :--- | :--- | :--- |
| `42` | `int` | `'42'` | `String` |
| `3.14` | `double` | `10 / 2` | `double` *(valeur 5.0)* |
| `true` | `bool` | `10 ~/ 2` | `int` |
| `"Settat"` | `String` | `7 > 3` | `bool` |

---

### Exercice 3 : Chasse aux erreurs
Le programme suivant contient **6 erreurs**. 

```dart
// Code comportant des erreurs :
void main() {
  int age = 'vingt';
  double prix = 12,5;
  String nom = 'Sara";
  const tva = 0.2
  tva = 0.25;
  print('Age : ' + age);
}
```

#### Table des corrections :

| Ligne | Type d'erreur | Problème | Correction |
| :---: | :---: | :--- | :--- |
| **2** | Type | Affectation d'un `String` dans une variable `int` | `int age = 20;` |
| **3** | Syntaxe | Utilisation d'une virgule au lieu d'un point décimal | `double prix = 12.5;` |
| **4** | Syntaxe | Guillemets non appariés (`'` et `"`) | `String nom = 'Sara';` |
| **5** | Syntaxe | Point-virgule `;` manquant | `const tva = 0.2;` |
| **6** | Logique / Type | Tentative de re-déclaration/modification d'une `const` | Supprimer la ligne (ou utiliser `var`) |
| **7** | Type | Concaténation directe `String + int` interdite | `print('Age : $age');` |

---

### Exercice 4 : Conditions

#### a) Trace
Soit la fonction suivante :
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

**Résultats des appels :**
* `mention(17)` $\to$ **Très bien**
* `mention(13.99)` $\to$ **Assez bien** *(car $13.99 < 14$)*
* `mention(10)` $\to$ **Passable**
* `mention(9.5)` $\to$ **Insuffisant**

#### b) Expressions booléennes
Écrivez en Dart la condition qui vaut `true` lorsque :
1. `a` est compris entre 10 et 20 (bornes incluses) :
   ```dart
   a >= 10 && a <= 20
   ```
2. `n` est un entier **pair et strictement positif** :
   ```dart
   n > 0 && n % 2 == 0
   ```
3. `annee` est une année **bissextile** (divisible par 4 mais pas par 100, ou divisible par 400) :
   ```dart
   (annee % 4 == 0 && annee % 100 != 0) || (annee % 400 == 0)
   ```

#### c) Réécriture avec l'opérateur ternaire
```dart
// Code initial :
String statut;
if (age >= 18) {
  statut = 'majeur';
} else {
  statut = 'mineur';
}

// Code réécrit :
String statut = age >= 18 ? 'majeur' : 'mineur';
```

---

## 💻 Partie B -- TP (Sur machine) - 80 min

> 💡 **Consignes :**  
> Créez un dossier `tp1` et enregistrez chaque exercice dans un fichier séparé (`tp1_ex1.dart`, etc.).  
> Pour exécuter vos programmes : `dart run tp1_ex1.dart`.  
> *Note : Les exercices TP3 à TP5 utilisent `stdin` et nécessitent de s'exécuter dans un terminal local (ils ne fonctionnent pas sur DartPad).*

---

### TP 1 : Environnement et premier programme
1. Vérifiez votre installation dans un terminal :
   ```bash
   dart --version
   ```
2. Écrivez un programme qui affiche une **carte de visite** avec votre nom, votre filière et votre ville, en utilisant des variables et l'interpolation de chaînes.
3. Introduisez volontairement une erreur de syntaxe (oubli de `;`), observez l'erreur dans le terminal, puis corrigez.

---

### TP 2 : Calcul d'une facture
Écrivez un programme qui calcule le prix TTC d'un article.
* Le taux de TVA (20%) est une constante (`const`).
* Le prix HT vaut 250 DH.
* Affichez le prix HT, le montant de la TVA et le prix TTC avec 2 décimales.

**Exemple de sortie :**
```text
Prix HT  : 250.00 DH
TVA (20%): 50.00 DH
Prix TTC : 300.00 DH
```

#### Solution TP 2 :
```dart
void main() {
  const double tva = 0.20;
  double prixHT = 250;
  double montantTVA = prixHT * tva;
  double prixTTC = prixHT + montantTVA;

  print('Prix HT  : ${prixHT.toStringAsFixed(2)} DH');
  print('TVA (20%): ${montantTVA.toStringAsFixed(2)} DH');
  print('Prix TTC : ${prixTTC.toStringAsFixed(2)} DH');
}
```
> **Question :** Pourquoi utiliser `const` plutôt que `var` pour la TVA ?  
> **Réponse :** `const` empêche toute modification accidentelle du taux au cours de l'exécution et indique une valeur immuable définie dès la compilation.

---

### TP 3 : Moyenne et mention (saisie clavier)
Écrivez un programme qui lit le **nom** d'un étudiant et **deux notes**, puis affiche sa moyenne et sa mention.
* Utilisez `double.tryParse` et gérez la saisie invalide (affichage d'un message puis arrêt).
* Formatage de la moyenne : 2 décimales.

**Exemple de sortie :**
```text
Nom : Sara
Note 1 : 15
Note 2 : 17
Sara : 16.00 (Très bien)
```

#### Solution TP 3 :
```dart
import 'dart:io';

void main() {
  stdout.write('Nom : ');
  String nom = stdin.readLineSync() ?? 'Inconnu';

  stdout.write('Note 1 : ');
  double? n1 = double.tryParse(stdin.readLineSync() ?? '');
  
  stdout.write('Note 2 : ');
  double? n2 = double.tryParse(stdin.readLineSync() ?? '');

  if (n1 == null || n2 == null) {
    print('Saisie invalide. Veuillez entrer des nombres valides.');
    return;
  }

  double moy = (n1 + n2) / 2;
  String mention;

  if (moy >= 16) {
    mention = 'Très bien';
  } else if (moy >= 14) {
    mention = 'Bien';
  } else if (moy >= 12) {
    mention = 'Assez bien';
  } else if (moy >= 10) {
    mention = 'Passable';
  } else {
    mention = 'Insuffisant';
  }

  print('$nom : ${moy.toStringAsFixed(2)} ($mention)');
}
```

---

### TP 4 : Calculatrice à deux opérandes
1. Lisez deux nombres réels `a` et `b`, puis un opérateur (`+`, `-`, `*`, `/`).
2. À l'aide d'un `switch`, affichez le résultat. Empêchez la division par zéro.
3. Pour un opérateur inconnu, affichez un message d'erreur (`default`).

#### Solution TP 4 :
```dart
import 'dart:io';

void main() {
  stdout.write('a = ');
  double? a = double.tryParse(stdin.readLineSync() ?? '');

  stdout.write('Opérateur (+ - * /) : ');
  String op = stdin.readLineSync() ?? '';

  stdout.write('b = ');
  double? b = double.tryParse(stdin.readLineSync() ?? '');

  if (a == null || b == null) {
    print('Nombres invalides.');
    return;
  }

  switch (op) {
    case '+':
      print('Résultat : ${a + b}');
      break;
    case '-':
      print('Résultat : ${a - b}');
      break;
    case '*':
      print('Résultat : ${a * b}');
      break;
    case '/':
      if (b == 0) {
        print('Erreur : Division par zéro impossible.');
      } else {
        print('Résultat : ${a / b}');
      }
      break;
    default:
      print('Erreur : Opérateur inconnu.');
  }
}
```

#### Bonus : Année bissextile
Programme qui détermine si une année saisie est bissextile *(tests suggérés : 1900, 2000, 2024, 2026)*.

```dart
import 'dart:io';

void main() {
  stdout.write('Année : ');
  int? annee = int.tryParse(stdin.readLineSync() ?? '');

  if (annee == null) {
    print('Année invalide.');
    return;
  }

  bool bissextile = (annee % 4 == 0 && annee % 100 != 0) || (annee % 400 == 0);
  print('$annee : ${bissextile ? "bissextile" : "non bissextile"}');
}
```

---

### TP 5 : Conversion d'une durée
Lisez un nombre entier de secondes et affichez-le sous la forme `h heures min minutes s secondes`. Utiliser uniquement `~/` (division entière) et `%` (modulo).

**Exemple de sortie :**
```text
3725 s = 1 h 2 min 5 s
```

#### Solution TP 5 (Version de base) :
```dart
import 'dart:io';

void main() {
  stdout.write('Saisir une durée en secondes : ');
  int total = int.parse(stdin.readLineSync()!);

  int h = total ~/ 3600;
  int reste = total % 3600;
  int m = reste ~/ 60;
  int s = reste % 60;

  print('$total s = $h h $m min $s s');
}
```

#### Version Défi (sans unités nulles) :
```dart
import 'dart:io';

void main() {
  stdout.write('Saisir une durée en secondes : ');
  int total = int.parse(stdin.readLineSync()!);

  List<String> parties = [];

  int h = total ~/ 3600;
  int m = (total % 3600) ~/ 60;
  int s = total % 60;

  if (h > 0) parties.add('$h h');
  if (m > 0) parties.add('$m min');
  if (s > 0) parties.add('$s s');

  print(parties.isEmpty ? '0 s' : parties.join(' '));
}
```

---

## 📦 Livrables à rendre
1. Les **5 fichiers `.dart`** des exercices pratiques (`tp1_ex1.dart` à `tp1_ex5.dart`).
2. Une **capture d'écran** montrant l'exécution de l'exercice **TP3**.
3. Assurez-vous que le code soit **clairement indenté** et **commenté**.