# Exercice – Premiers pas avec Flutter (Stateless → interactions simples)

## Objectifs d’apprentissage

* Comprendre la structure minimale d’une app Flutter (`main()`, `runApp`, `MaterialApp`, `Scaffold`).
* Utiliser des **Stateless widgets** et la composition (extraction de widgets).
* Configurer un **thème clair** (Material 3) et le **debug banner**.
* Ajouter une petite interaction (SnackBar, compteur).
* Naviguer vers une **seconde page**.

## Énoncé

À partir du squelette fourni (ci-dessous), complétez les tâches 1→7. Respectez les indices `// TODO`. Ne changez pas les noms des classes demandées.

### Tâches

1. **Import & point d’entrée (2 pts)**

   * Laissez `import 'package:flutter/material.dart';` tel quel.
   * Dans votre rapport, en 1 phrase, expliquez le rôle de cet import.

2. **Bannière de debug (2 pts)**

   * Cachez la bannière “DEBUG” dans `MaterialApp`.

3. **Thème clair lisible (6 pts)**

   * Activez **Material 3** (déjà présent) et utilisez `colorSchemeSeed: Colors.blue` pour générer une palette cohérente.
   * Définissez `brightness: Brightness.light`.
   * Interdiction d’utiliser `primarySwatch` seul : passez par `colorSchemeSeed`.

4. **AppBar & body (8 pts)**

   * Gardez la page `PageAccueil`.
   * Remplacez le `backgroundColor` manuel de l’`AppBar` par `Theme.of(context).colorScheme.primary`.
   * Vérifiez que les textes restent lisibles en clair.

5. **SnackBar sur le FAB (6 pts)**

   * Quand on clique sur le `FloatingActionButton`, affichez un **SnackBar** : “Action exécutée !”.

6. **Interaction sur une Card (10 pts)**

   * Dans `CarteInfo`, lorsque l’utilisateur tape la carte (tap), affichez un **SnackBar** avec le titre de la carte (ex. “Carte 1”).
   * Indice : envelopper `ListTile` ou `Card` avec `InkWell`/`GestureDetector`.

7. **Navigation (16 pts)**

   * Créez une page `PageDetail(titre: String)` (Stateless).
   * Depuis la **deuxième** carte, au tap, **naviguez** vers `PageDetail` et affichez le `titre` dans un grand `Text`.
   * Ajoutez un bouton “Retour” (implicite via `AppBar`).

### Barème (40 pts)

* T1: 2 | T2: 2 | T3: 6 | T4: 8 | T5: 6 | T6: 10 | T7: 16

### Rendu attendu

* Un **seul projet Flutter** compilable.
* Capture d’écran de l’app **ouverte** (page d’accueil) + capture d’écran de la **page détail**.
* Mini-rapport (5–8 lignes) : explication de l’import, des widgets utilisés, et de la navigation.

---

## Squelette de départ avec TODO (à donner aux étudiants)

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MonApplication());
}

/// Widget principal de l'application (Stateless)
class MonApplication extends StatelessWidget {
  const MonApplication({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Démonstration Flutter',
      // TODO(T2): cacher la bannière de debug
      debugShowCheckedModeBanner: true,
      theme: ThemeData(
        // TODO(T3): passer par colorSchemeSeed et brightness pour un thème clair lisible
        primarySwatch: Colors.blue, // à remplacer
        useMaterial3: true,
      ),
      home: const PageAccueil(),
    );
  }
}

/// Page d'accueil avec plusieurs composants graphiques (Stateless)
class PageAccueil extends StatelessWidget {
  const PageAccueil({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Démonstration Stateless Widgets'),
        // TODO(T4): utiliser la couleur primaire du thème au lieu d'une couleur codée en dur
        backgroundColor: Colors.blue, // à remplacer
        centerTitle: true,
      ),
      body: const SingleChildScrollView(
        padding: EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.stretch,
          children: [
            // Titre principal
            TitreSection(titre: 'Bienvenue dans Flutter!'),
            SizedBox(height: 20),

            // Section avec container coloré
            ContainerColore(
              couleur: Colors.blue,
              texte: 'Container avec fond bleu',
            ),
            SizedBox(height: 20),

            // Section avec Row
            SectionRow(),
            SizedBox(height: 20),

            // Section avec Cards
            SectionCartes(),
            SizedBox(height: 20),

            // Section avec icônes
            SectionIcones(),
            SizedBox(height: 20),

            // Bouton décoratif
            BoutonDecoratif(texte: 'Bouton Exemple'),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        // TODO(T5): afficher un SnackBar “Action exécutée !”
        onPressed: () {},
        tooltip: 'Action',
        child: const Icon(Icons.add_alert),
      ),
    );
  }
}

/// Widget pour afficher un titre (Stateless)
class TitreSection extends StatelessWidget {
  final String titre;

  const TitreSection({super.key, required this.titre});

  @override
  Widget build(BuildContext context) {
    return Text(
      titre,
      style: TextStyle(
        fontSize: 28,
        fontWeight: FontWeight.bold,
        // Bonus : utilisez la couleur du thème
        color: Theme.of(context).colorScheme.primary,
      ),
      textAlign: TextAlign.center,
    );
  }
}

/// Widget Container avec couleur personnalisée (Stateless)
class ContainerColore extends StatelessWidget {
  final Color couleur;
  final String texte;

  const ContainerColore({
    super.key,
    required this.couleur,
    required this.texte,
  });

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.all(20),
      decoration: BoxDecoration(
        color: couleur,
        borderRadius: BorderRadius.circular(15),
        boxShadow: [
          BoxShadow(
            color: Colors.black.withOpacity(.08),
            spreadRadius: 1,
            blurRadius: 8,
            offset: const Offset(0, 3),
          ),
        ],
      ),
      child: Text(
        texte,
        style: const TextStyle(
          color: Colors.white,
          fontSize: 18,
          fontWeight: FontWeight.w600,
        ),
        textAlign: TextAlign.center,
      ),
    );
  }
}

/// Section démontrant l'utilisation de Row (Stateless)
class SectionRow extends StatelessWidget {
  const SectionRow({super.key});

  @override
  Widget build(BuildContext context) {
    Widget box(Color c, String t) => Container(
          width: 100,
          height: 100,
          decoration: BoxDecoration(color: c, borderRadius: BorderRadius.circular(10)),
          child: Center(
            child: Text(
              t,
              style: const TextStyle(color: Colors.white, fontWeight: FontWeight.bold),
            ),
          ),
        );

    return Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        const Text(
          'Exemple de Row (disposition horizontale):',
          style: TextStyle(fontSize: 16, fontWeight: FontWeight.bold),
        ),
        const SizedBox(height: 10),
        Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            box(Colors.red, 'Box 1'),
            box(Colors.green, 'Box 2'),
            box(Colors.orange, 'Box 3'),
          ],
        ),
      ],
    );
  }
}

/// Section avec des cartes (Stateless)
class SectionCartes extends StatelessWidget {
  const SectionCartes({super.key});

  @override
  Widget build(BuildContext context) {
    return const Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        Text('Exemples de Cards:', style: TextStyle(fontSize: 16, fontWeight: FontWeight.bold)),
        SizedBox(height: 10),
        CarteInfo(
          titre: 'Carte 1',
          sousTitre: 'Description de la carte 1',
          icone: Icons.star,
          couleurIcone: Colors.amber,
          // TODO(T6): au tap => SnackBar avec le titre
          // TODO(T7): la navigation sera sur la 2e carte (voir plus bas)
        ),
        SizedBox(height: 10),
        CarteInfo(
          titre: 'Carte 2',
          sousTitre: 'Description de la carte 2 (tap => aller à la PageDetail)',
          icone: Icons.favorite,
          couleurIcone: Colors.red,
        ),
      ],
    );
  }
}

/// Widget Carte personnalisée (Stateless)
class CarteInfo extends StatelessWidget {
  final String titre;
  final String sousTitre;
  final IconData icone;
  final Color couleurIcone;

  const CarteInfo({
    super.key,
    required this.titre,
    required this.sousTitre,
    required this.icone,
    required this.couleurIcone,
  });

  @override
  Widget build(BuildContext context) {
    final card = Card(
      elevation: 2,
      child: ListTile(
        leading: Icon(icone, color: couleurIcone, size: 36),
        title: Text(titre, style: const TextStyle(fontWeight: FontWeight.bold)),
        subtitle: Text(sousTitre),
        trailing: const Icon(Icons.arrow_forward_ios, size: 16),
      ),
    );

    // TODO(T6 & T7):
    // - Si titre == "Carte 1": afficher un SnackBar(titre)
    // - Si titre == "Carte 2": Navigator.push vers PageDetail(titre: titre)
    return card; // à remplacer par InkWell(... child: card)
  }
}

/// Section avec des icônes (Stateless)
class SectionIcones extends StatelessWidget {
  const SectionIcones({super.key});

  @override
  Widget build(BuildContext context) {
    Widget iconWithLabel(IconData icone, String label, Color couleur) => Column(
          children: [
            Icon(icone, size: 40, color: couleur),
            const SizedBox(height: 5),
            Text(label, style: const TextStyle(fontSize: 12)),
          ],
        );

    return Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        const Text('Collection d\'icônes:',
            style: TextStyle(fontSize: 16, fontWeight: FontWeight.bold)),
        const SizedBox(height: 10),
        Row(
          mainAxisAlignment: MainAxisAlignment.spaceAround,
          children: [
            iconWithLabel(Icons.home, 'Home', Colors.blue),
            iconWithLabel(Icons.person, 'Profil', Colors.green),
            iconWithLabel(Icons.settings, 'Paramètres', Colors.grey),
            iconWithLabel(Icons.notifications, 'Alertes', Colors.orange),
          ],
        ),
      ],
    );
  }
}

/// Bouton décoratif (Stateless)
class BoutonDecoratif extends StatelessWidget {
  final String texte;

  const BoutonDecoratif({super.key, required this.texte});

  @override
  Widget build(BuildContext context) {
    return Container(
      decoration: BoxDecoration(
        gradient: const LinearGradient(
          colors: [Colors.blue, Colors.purple],
          begin: Alignment.topLeft,
          end: Alignment.bottomRight,
        ),
        borderRadius: BorderRadius.circular(30),
        boxShadow: [
          BoxShadow(
            color: Colors.black.withOpacity(.1),
            spreadRadius: 1,
            blurRadius: 8,
            offset: const Offset(0, 3),
          ),
        ],
      ),
      child: Material(
        color: Colors.transparent,
        child: InkWell(
          borderRadius: BorderRadius.circular(30),
          onTap: () {
            // Bonus: SnackBar “Bouton Exemple cliqué”
          },
          child: const Padding(
            padding: EdgeInsets.symmetric(horizontal: 40, vertical: 15),
            child: Center(
              child: Text('Bouton Exemple',
                  style: TextStyle(color: Colors.white, fontSize: 18, fontWeight: FontWeight.bold)),
            ),
          ),
        ),
      ),
    );
  }
}

// TODO(T7): créer une page de détail simple et lisible
// class PageDetail extends StatelessWidget { ... }
```



<br/>
<br/>

# Corrigé minimal 

> Ne regardez pas cette partie avant de me remettre votre travail 😉

```dart
// ——— Correctifs principaux ———
// T2, T3, T4, T5, T6, T7 implémentés

import 'package:flutter/material.dart';

void main() {
  runApp(const MonApplication());
}

class MonApplication extends StatelessWidget {
  const MonApplication({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Démonstration Flutter',
      debugShowCheckedModeBanner: false, // T2
      theme: ThemeData(
        useMaterial3: true,
        colorSchemeSeed: Colors.blue,      // T3
        brightness: Brightness.light,      // T3
      ),
      home: const PageAccueil(),
    );
  }
}

class PageAccueil extends StatelessWidget {
  const PageAccueil({super.key});

  void _showSnack(BuildContext context, String msg) {
    ScaffoldMessenger.of(context).showSnackBar(SnackBar(content: Text(msg)));
  }

  @override
  Widget build(BuildContext context) {
    final primary = Theme.of(context).colorScheme.primary; // T4
    return Scaffold(
      appBar: AppBar(
        title: const Text('Démonstration Stateless Widgets'),
        backgroundColor: primary, // T4
        centerTitle: true,
      ),
      body: const SingleChildScrollView(
        padding: EdgeInsets.all(16),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.stretch,
          children: [
            TitreSection(titre: 'Bienvenue dans Flutter!'),
            SizedBox(height: 20),
            ContainerColore(couleur: Colors.blue, texte: 'Container avec fond bleu'),
            SizedBox(height: 20),
            SectionRow(),
            SizedBox(height: 20),
            SectionCartes(),
            SizedBox(height: 20),
            BoutonDecoratif(texte: 'Bouton Exemple'),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () => _showSnack(context, 'Action exécutée !'), // T5
        tooltip: 'Action',
        child: const Icon(Icons.add_alert),
      ),
    );
  }
}

class TitreSection extends StatelessWidget {
  final String titre;
  const TitreSection({super.key, required this.titre});

  @override
  Widget build(BuildContext context) {
    return Text(
      titre,
      style: TextStyle(
        fontSize: 28,
        fontWeight: FontWeight.bold,
        color: Theme.of(context).colorScheme.primary,
      ),
      textAlign: TextAlign.center,
    );
  }
}

class ContainerColore extends StatelessWidget {
  final Color couleur;
  final String texte;
  const ContainerColore({super.key, required this.couleur, required this.texte});

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.all(20),
      decoration: BoxDecoration(
        color: couleur,
        borderRadius: BorderRadius.circular(15),
        boxShadow: [
          BoxShadow(
            color: Colors.black.withOpacity(.08),
            spreadRadius: 1,
            blurRadius: 8,
            offset: const Offset(0, 3),
          ),
        ],
      ),
      child: Text(
        texte,
        style: const TextStyle(color: Colors.white, fontSize: 18, fontWeight: FontWeight.w600),
        textAlign: TextAlign.center,
      ),
    );
  }
}

class SectionRow extends StatelessWidget {
  const SectionRow({super.key});

  @override
  Widget build(BuildContext context) {
    Widget box(Color c, String t) => Container(
          width: 100,
          height: 100,
          decoration: BoxDecoration(color: c, borderRadius: BorderRadius.circular(10)),
          child: Center(
            child: Text(t, style: const TextStyle(color: Colors.white, fontWeight: FontWeight.bold)),
          ),
        );

    return Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        const Text('Exemple de Row (disposition horizontale):',
            style: TextStyle(fontSize: 16, fontWeight: FontWeight.bold)),
        const SizedBox(height: 10),
        Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [box(Colors.red, 'Box 1'), box(Colors.green, 'Box 2'), box(Colors.orange, 'Box 3')],
        ),
      ],
    );
  }
}

class SectionCartes extends StatelessWidget {
  const SectionCartes({super.key});

  @override
  Widget build(BuildContext context) {
    return Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        const Text('Exemples de Cards:', style: TextStyle(fontSize: 16, fontWeight: FontWeight.bold)),
        const SizedBox(height: 10),
        CarteInfo(
          titre: 'Carte 1',
          sousTitre: 'Description de la carte 1',
          icone: Icons.star,
          couleurIcone: Colors.amber,
          onTap: () => ScaffoldMessenger.of(context)
              .showSnackBar(const SnackBar(content: Text('Carte 1'))), // T6
        ),
        const SizedBox(height: 10),
        CarteInfo(
          titre: 'Carte 2',
          sousTitre: 'Description de la carte 2 (tap => aller à la PageDetail)',
          icone: Icons.favorite,
          couleurIcone: Colors.red,
          onTap: () => Navigator.of(context).push(
            MaterialPageRoute(builder: (_) => const PageDetail(titre: 'Carte 2')), // T7
          ),
        ),
      ],
    );
  }
}

class CarteInfo extends StatelessWidget {
  final String titre;
  final String sousTitre;
  final IconData icone;
  final Color couleurIcone;
  final VoidCallback? onTap;

  const CarteInfo({
    super.key,
    required this.titre,
    required this.sousTitre,
    required this.icone,
    required this.couleurIcone,
    this.onTap,
  });

  @override
  Widget build(BuildContext context) {
    final card = Card(
      elevation: 2,
      child: ListTile(
        leading: Icon(icone, color: couleurIcone, size: 36),
        title: Text(titre, style: const TextStyle(fontWeight: FontWeight.bold)),
        subtitle: Text(sousTitre),
        trailing: const Icon(Icons.arrow_forward_ios, size: 16),
      ),
    );
    return InkWell(onTap: onTap, child: card); // T6/T7
  }
}

class BoutonDecoratif extends StatelessWidget {
  final String texte;
  const BoutonDecoratif({super.key, required this.texte});

  @override
  Widget build(BuildContext context) {
    return Container(
      decoration: BoxDecoration(
        gradient: const LinearGradient(colors: [Colors.blue, Colors.purple], begin: Alignment.topLeft, end: Alignment.bottomRight),
        borderRadius: BorderRadius.circular(30),
        boxShadow: [
          BoxShadow(color: Colors.black.withOpacity(.1), spreadRadius: 1, blurRadius: 8, offset: const Offset(0, 3)),
        ],
      ),
      child: Material(
        color: Colors.transparent,
        child: InkWell(
          borderRadius: BorderRadius.circular(30),
          onTap: () => ScaffoldMessenger.of(context).showSnackBar(
            const SnackBar(content: Text('Bouton Exemple cliqué')),
          ),
          child: Padding(
            padding: const EdgeInsets.symmetric(horizontal: 40, vertical: 15),
            child: Center(
              child: Text(texte, style: const TextStyle(color: Colors.white, fontSize: 18, fontWeight: FontWeight.bold)),
            ),
          ),
        ),
      ),
    );
  }
}

class PageDetail extends StatelessWidget {
  final String titre;
  const PageDetail({super.key, required this.titre});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(titre)),
      body: Center(
        child: Text(
          titre,
          style: const TextStyle(fontSize: 28, fontWeight: FontWeight.bold),
        ),
      ),
    );
  }
}
```

