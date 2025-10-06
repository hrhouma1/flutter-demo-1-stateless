
# Pratique 1


## Instructions générales


  1. **L’arborescence des widgets (Widget Tree)** pour trois écrans (Accueil, Détail, Paramètres).
  2. **La navigation entre écrans** (flux “tap” → écran).
  3. **Les interactions utilisateur → réactions UI** (par ex. “tap” → SnackBar, “tap” → Navigation).

## Contraintes

* Utilisez des noms de widgets Flutter réels (MaterialApp, Scaffold, AppBar, Body, Card, Icon…).
* Aucune notion d’état interne (Idle, Loading, etc.).



## Partie 1 – Arborescence des Widgets

**À faire :** représenter la structure hiérarchique des trois écrans. Exemple de modèle ASCII à compléter :

```
Écran Accueil
└─ MaterialApp
   └─ Scaffold
      ├─ AppBar (titre: Accueil)
      ├─ Body (SingleChildScrollView)
      │  ├─ Column
      │  │  ├─ Text("Bienvenue")
      │  │  ├─ Container (bandeau info)
      │  │  ├─ Row (3 Cartes)
      │  │  └─ Bouton décoratif
      └─ FloatingActionButton (Icon: add_alert)

Écran Détail
└─ Scaffold
   ├─ AppBar (titre dynamique)
   ├─ Body (Column)
   │  ├─ Image/Hero
   │  ├─ Text descriptif
   │  └─ Boutons d’action

Écran Paramètres
└─ Scaffold
   ├─ AppBar ("Paramètres")
   └─ Body (ListView)
      ├─ Switch Thème
      └─ Radio Langue
```



## Partie 2 – Navigation entre écrans 

**À faire :** représenter les flux “tap” → écran. Exemple :

```
Accueil --(tap Carte 2)--> Détail
Accueil --(tap Icon Paramètres)--> Paramètres
Détail --(AppBar Back)--> Accueil
Paramètres --(AppBar Back)--> Accueil
```



## Partie 3 – Interactions utilisateur → Réactions UI 

**À faire :** lister au moins 4 interactions différentes. Exemple :

```
Tap FAB            -> SnackBar: "Action exécutée"
Tap Carte 1        -> SnackBar: "Carte 1"
Tap Carte 2        -> Navigation vers Détail(id)
Tap Icon Paramètres-> Navigation vers Paramètres
Switch Thème       -> Recalcul des couleurs (UI)
```





<br/>
<br/>

# Pratique 1

## Partie 1 – Arborescence des Widgets (Mermaid)

```mermaid
flowchart TD
  %% ECRAN ACCUEIL
  subgraph Accueil
    MaterialApp --> A_Scaffold[Scaffold]
    A_Scaffold --> A_AppBar[AppBar: Accueil]
    A_Scaffold --> A_Body[Body: SingleChildScrollView]
    A_Scaffold --> A_FAB[FloatingActionButton: add_alert]
    A_Body --> A_Column[Column]
    A_Column --> A_Titre[Text: Bienvenue]
    A_Column --> A_Bandeau[Container: bandeau info]
    A_Column --> A_Grille[Row/Wrap: 3 Cards]
    A_Column --> A_Bouton[Bouton decoratif]
  end

  %% ECRAN DETAIL
  subgraph Detail
    D_Scaffold[Scaffold]
    D_Scaffold --> D_AppBar[AppBar: titre dynamique]
    D_Scaffold --> D_Body[Body: Column]
    D_Body --> D_Image[Image/Hero]
    D_Body --> D_Texte[Text descriptif]
    D_Body --> D_Actions[Row: Boutons]
  end

  %% ECRAN PARAMETRES
  subgraph Parametres
    P_Scaffold[Scaffold]
    P_Scaffold --> P_AppBar[AppBar: Parametres]
    P_Scaffold --> P_List[ListView]
    P_List --> P_Switch[Switch: Theme]
    P_List --> P_Radio[Radio: Langue]
  end
```

## Partie 2 – Navigation entre écrans (Mermaid)

```mermaid
flowchart LR
  Accueil -- tap Carte 2 --> Detail
  Accueil -- tap Icon Parametres --> Parametres
  Detail -- AppBar Back --> Accueil
  Parametres -- AppBar Back --> Accueil
```

## Partie 3 – Interactions utilisateur → Réactions UI (Mermaid)

```mermaid
flowchart LR
  TapFAB((Tap FAB)) --> SnackFAB[SnackBar: Action executee]
  TapCarte1((Tap Carte 1)) --> SnackC1[SnackBar: Carte 1]
  TapCarte2((Tap Carte 2)) --> GoDetail[Navigate to Detail(id)]
  TapIconParams((Tap Icon Parametres)) --> GoSettings[Navigate to Parametres]
  ToggleTheme((Switch Theme)) --> Recompute[Recompute color scheme]
```




# Partie 3 — Interactions UI (Mermaid, corrigé)


## Version A — Flowchart  

```mermaid
flowchart LR
  TapFAB((Tap FAB)) --> SnackFAB[SnackBar: Action executee]
  TapCarte1((Tap Carte 1)) --> SnackC1[SnackBar: Carte 1]
  TapCarte2((Tap Carte 2)) --> GoDetail[Navigate to Detail (id)]
  TapIconParams((Tap Icon Parametres)) --> GoSettings[Navigate to Parametres]
  ToggleTheme((Switch Theme)) --> Recompute[Recompute color scheme]
```



## Version B — Flowchart avec déclaration des nœuds puis liens

```mermaid
flowchart LR
  %% --- Nodes ---
  TapFAB((Tap FAB))
  SnackFAB[SnackBar: Action executee]

  TapCarte1((Tap Carte 1))
  SnackC1[SnackBar: Carte 1]

  TapCarte2((Tap Carte 2))
  GoDetail[[Navigate to Detail id]]

  TapIconParams((Tap Icon Parametres))
  GoSettings[[Navigate to Parametres]]

  ToggleTheme((Switch Theme))
  Recompute[Recompute color scheme]

  %% --- Edges ---
  TapFAB --> SnackFAB
  TapCarte1 --> SnackC1
  TapCarte2 --> GoDetail
  TapIconParams --> GoSettings
  ToggleTheme --> Recompute
```



## Version C — Flowchart avec sous-graphes 

```mermaid
flowchart TD
  subgraph Actions
    TapFAB((Tap FAB))
    TapCarte1((Tap Carte 1))
    TapCarte2((Tap Carte 2))
    TapIconParams((Tap Icon Parametres))
    ToggleTheme((Switch Theme))
  end

  subgraph Reactions
    SnackFAB[SnackBar: Action executee]
    SnackC1[SnackBar: Carte 1]
    GoDetail[[Navigate to Detail id]]
    GoSettings[[Navigate to Parametres]]
    Recompute[Recompute color scheme]
  end

  TapFAB --> SnackFAB
  TapCarte1 --> SnackC1
  TapCarte2 --> GoDetail
  TapIconParams --> GoSettings
  ToggleTheme --> Recompute
```


## Version D — Sequence Diagram 

```mermaid
sequenceDiagram
  actor U as User
  participant A as Accueil
  participant SM as ScaffoldMessenger
  participant N as Navigator

  U->>A: Tap FAB
  A->>SM: showSnackBar(Action executee)

  U->>A: Tap Carte 1
  A->>SM: showSnackBar(Carte 1)

  U->>A: Tap Carte 2
  A->>N: push(Detail, id)

  U->>A: Tap Icon Parametres
  A->>N: push(Parametres)
```



## Version E — interaction 

```mermaid
flowchart LR
  U1((Tap FAB)) --> R1[SnackBar: Action executee]
  U2((Tap Carte 1)) --> R2[SnackBar: Carte 1]
  U3((Tap Carte 2)) --> R3[[Navigate to Detail id]]
  U4((Tap Icon Parametres)) --> R4[[Navigate to Parametres]]
  U5((Switch Theme)) --> R5[Recompute color scheme]
```






