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
| **1** | `print(10 / 4);` | 2.5 |
| **2** | `print(10 ~/ 4);` | 2 |
| **3** | `print(10 % 4);` | 2 |
| **4** | `print('Dart' + ' ' + 'MST');` | Dart MST |
| **5** | `print('2' + '3');` | 23 |
| **6** | `print(2 + 3 * 4 - 1);` | 13 |
| **7** | `int x = 5; x += 3; x *= 2; print(x);` | 16 |
| **8** | `print(5 > 3 && 2 > 4);` | False |
| **9** | `print(!(5 == 5) \|\| 3 < 4);` | True |
| **10**| `String? s; print(s ?? 'vide');` | vide |

---

### Exercice 2 : Quel type pour quelle valeur ? (*7 min*)
*Indiquez le type Dart le plus adapté (`int`, `double`, `String`, `bool`) pour chaque valeur ou expression.*

| Valeur / Expression | Votre réponse | Valeur / Expression | Votre réponse |
| :--- | :--- | :--- | :--- |
| `42` | int | `'42'` | string |
| `3.14` | double | `10 / 2` | double  |
| `true` | bool | `10 ~/ 2` | int |
| `"Settat"` | string | `7 > 3` | bool |

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
| **2** | Type | on doit faire affectation d'un string dans une variable int | `int age = 20;` |
| **3** | Syntaxe | on doit mettre le point au lieu de virgule | 'double prix = 12.5;' |
| **4** | Syntaxe | problème dans guillemets | 'String nom = 'Sara';' |
| **5** | Syntaxe | on doit mettre ';' | 'const tva = 0.2;'|
| **6** | Type/Logique | on ne peut pas modifier const | 'var tva = 0.2;' |
| **7** | Type | imposible de concaténer string + int | print('Age : $ age'); |

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
| **Résultat** | Trés bien | Assez bien | Passable | Insuffisant |

#### b) Expressions booléennes
*Écrivez en Dart la condition qui vaut `true` lorsque :*

1. `a` est compris entre 10 et 20 (bornes incluses) :
```dart
a >= 10 && a <= 20;
```

2. `n` est un entier **pair et strictement positif** :
```dart
n > 0 && n % 2 == 0;
```

3. `annee` est une année **bissextile** (divisible par 4 mais pas par 100, ou divisible par 400) :
```dart
(annee % 4 == 0 && annee % 100 != 0) || (annee % 400 == 0);
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
String statut = age >= 18 ? 'majeur':'mineur';
```

---

## 💻 Partie B -- TP (Sur machine) — *80 min*

> 💡 **Consigne :** Créez un dossier `tp1` et enregistrez chaque exercice dans un fichier séparé (`tp1_ex1.dart`, etc.). Exécution : `dart run tp1_ex1.dart`.  
> *Note : Les exercices TP3 à TP5 utilisent `stdin` (non compatibles avec DartPad).*

---

### TP 1 : Environnement et premier programme (*10 min*)

1. **Version installée :**
   ```bash
   Dart SDK version: 3.13.5 (stable) 
   ```

2. **Code de la carte de visite (`tp1_ex1.dart`) :**
```dart
void main() {
  String nom = 'Masouab';
  String filiere = 'SIOC';
  String ville = 'Casablanca';

  print('Carte de visite');
  print('Nom : $nom');
  print('Filière : $filiere');
  print('Ville : $ville');
}
```

3. **Remarque sur l'erreur de syntaxe testée :**
   * <!-- main.dart:9:25: Error: Expected ';' after this.
  l'erreur c'est le manque de ';' dans la ligne 9-->


---

### TP 2 : Calcul d'une facture (*15 min*)

- **Code source (`tp1_ex2.dart`) :**
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

- **Question :** Pourquoi utiliser `const` plutôt que `var` pour la TVA ?
  > **Réponse :** const est une constante de compilation : sa valeur est fixée à la compilation et ne peut jamais être réaffectée
---

### TP 3 : Moyenne et mention (*15 min*)

- **Code source (`tp1_ex3.dart`) :**
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
    print('Saisie invalide. Arrêt du programme');
    return;
  }

  double moyenne = (n1 + n2) / 2;
  String mention;

  if (moyenne >= 16) {
    mention = 'Très bien';
  } else if (moyenne >= 14) {
    mention = 'Bien';
  } else if (moyenne >= 12) {
    mention = 'Assez bien';
  } else if (moyenne >= 10) {
    mention = 'Passable';
  } else {
    mention = 'Insuffisant';
  }

  print('$nom : ${moyenne.toStringAsFixed(2)} ($mention)');
}
```

---

### TP 4 : Calculatrice à deux opérandes (*20 min*)

- **Code source (`tp1_ex4.dart`) :**
```dart
import 'dart:io';

void main() {
  stdout.write('a = ');
  double? a = double.tryParse(stdin.readLineSync() ?? '');

  stdout.write('b = ');
  double? b = double.tryParse(stdin.readLineSync() ?? '');

  stdout.write('Opérateur (+, -, *, /) : ');
  String op = stdin.readLineSync() ?? '';

  if (a == null || b == null || op.isEmpty) {
    print('Saisie invalide.');
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
        print('Erreur : la division par zéro n est pas possible.');
      } else {
        print('Résultat : ${a / b}');
      }
      break;
    default:
      print('Erreur : Opérateur inconnu.');
  }
}
```

- **Bonus : Année bissextile (`tp1_ex4_bonus.dart`) :**
```dart
import 'dart:io';

void main() {
  stdout.write('Année : ');
  int? annee = int.tryParse(stdin.readLineSync() ?? '');

  if (annee == null) {
    print('saisie invalide.');
    return;
  }

  bool bissextile = 
  (annee % 4 == 0 && annee % 100 != 0) || (annee % 400 == 0);
  print('$annee : ${bissextile ? "bissextile" : "non bissextile"}');
}
```

---

### TP 5 : Conversion d'une durée (*20 min*)

- **Code source (`tp1_ex5.dart`) :**
```dart
import 'dart:io';

void main() {
  stdout.write('Saisir le nombre de secondes : ');
  int? total = int.tryParse(stdin.readLineSync() ?? '');

  if (total == null || total < 0) {
    print('Erreur : saisie invalide.');
    return;
  }
  int h = total ~/ 3600;
  int reste = total % 3600;
  int m = reste ~/ 60;
  int s = reste % 60;

  print('$total s = $h h $m min $s s');
}
```

- **Défi (Gestion des pluriels et unités nulles) :**
```dart
import 'dart:io';

void main() {
  stdout.write('Saisir le nombre de secondes : ');
  int? total = int.tryParse(stdin.readLineSync() ?? '');

  if (total == null || total < 0) {
    print('Saisie invalide.');
    return;
  }

  int h = total ~/ 3600;
  int m = (total % 3600) ~/ 60;
  int s = total % 60;

  List<String> parties = [];

  if (h > 0)   parties.add('$h ${h > 1 ? "heures" : "heure"}');
  if (m > 0)   parties.add('$m ${m > 1 ? "minutes" : "minute"}');
  if (s > 0 || parties.isEmpty) {
    parties.add('$s ${s > 1 ? "secondes" : "seconde"}');
  }
  print('$total s = ${parties.join(" ")}');
}
```

---

## 📦 Livrable
Cochez les éléments à remettre :
- [ ] Le présent fichier Markdown complété
- [ ] Les 5 fichiers `.dart` dans le dossier `tp1`
- [ ] Une capture d'écran d'exécution du **TP3**