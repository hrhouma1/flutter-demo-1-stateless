# Diagrammes Mermaid - Architecture Flutter

> **Thème:** Couleurs claires et professionnelles, sans emojis, optimisé pour une lecture confortable

## Palette de Couleurs Utilisée

```
Primary Blue:    #E3F2FD (très clair)    #90CAF9 (clair)    #42A5F5 (moyen)    #1976D2 (foncé)
Green:           #E8F5E9 (très clair)    #A5D6A7 (clair)    #66BB6A (moyen)
Red/Orange:      #FFEBEE (très clair)    #FFCDD2 (clair)    #E57373 (moyen)
Purple:          #F3E5F5 (très clair)    #CE93D8 (clair)    #AB47BC (moyen)
Grey:            #FAFAFA (très clair)    #E0E0E0 (clair)    #9E9E9E (moyen)
```

---

## 1. Vue d'ensemble de l'Application

```mermaid
graph TD
    A[main] -->|runApp| B[MonApplication]
    B -->|MaterialApp| C[PageAccueil]
    C -->|Scaffold| D[Structure de Page]
    
    D --> E[AppBar]
    D --> F[Body]
    D --> G[FloatingActionButton]
    
    E --> E1[Text: Démonstration Stateless Widgets]
    
    F --> H[SingleChildScrollView]
    H --> I[Column]
    
    I --> J1[TitreSection]
    I --> J2[ContainerColore]
    I --> J3[SectionRow]
    I --> J4[SectionCartes]
    I --> J5[SectionIcones]
    I --> J6[BoutonDecoratif]
    
    G --> G1[Icon: add]
    
    style A fill:#E3F2FD,stroke:#1976D2,stroke-width:2px,color:#000
    style B fill:#E8F5E9,stroke:#43A047,stroke-width:2px,color:#000
    style C fill:#FFF9C4,stroke:#F57C00,stroke-width:2px,color:#000
    style D fill:#E1BEE7,stroke:#8E24AA,stroke-width:2px,color:#000
    style E fill:#BBDEFB,stroke:#1976D2,stroke-width:1px,color:#000
    style F fill:#C8E6C9,stroke:#43A047,stroke-width:1px,color:#000
    style G fill:#FFCCBC,stroke:#E64A19,stroke-width:1px,color:#000
```

## 2. Hiérarchie Complète des Widgets

```mermaid
graph TB
    Main[main.dart]
    
    Main --> App[MonApplication<br/>StatelessWidget]
    App --> MatApp[MaterialApp]
    MatApp --> Page[PageAccueil<br/>StatelessWidget]
    
    Page --> Scaffold[Scaffold]
    
    Scaffold --> AppBar[AppBar]
    Scaffold --> Body[body]
    Scaffold --> FAB[floatingActionButton]
    
    AppBar --> AppBarText[Text]
    
    Body --> Scroll[SingleChildScrollView<br/>padding: 16px]
    
    Scroll --> Col[Column<br/>crossAxisAlignment: stretch]
    
    Col --> W1[TitreSection<br/>titre: Bienvenue...]
    Col --> Space1[SizedBox height:20]
    Col --> W2[ContainerColore<br/>couleur: blue]
    Col --> Space2[SizedBox height:20]
    Col --> W3[SectionRow]
    Col --> Space3[SizedBox height:20]
    Col --> W4[SectionCartes]
    Col --> Space4[SizedBox height:20]
    Col --> W5[SectionIcones]
    Col --> Space5[SizedBox height:20]
    Col --> W6[BoutonDecoratif]
    
    W1 --> W1T[Text<br/>fontSize:28, bold, blue]
    
    W2 --> W2C[Container<br/>BorderRadius, Shadow]
    W2C --> W2T[Text<br/>white, 18px]
    
    W3 --> W3Col[Column]
    W3Col --> W3Label[Text: Exemple de Row...]
    W3Col --> W3Row[Row<br/>spaceEvenly]
    W3Row --> Box1[Container<br/>100x100 red]
    W3Row --> Box2[Container<br/>100x100 green]
    W3Row --> Box3[Container<br/>100x100 orange]
    
    W4 --> W4Col[Column]
    W4Col --> W4Label[Text: Exemples de Cards]
    W4Col --> Card1[CarteInfo<br/>Carte 1, star, amber]
    W4Col --> Card2[CarteInfo<br/>Carte 2, favorite, red]
    
    Card1 --> Card1W[Card elevation:4]
    Card1W --> Tile1[ListTile]
    Tile1 --> Lead1[Icon leading]
    Tile1 --> Title1[Text title]
    Tile1 --> Sub1[Text subtitle]
    Tile1 --> Trail1[Icon trailing]
    
    W5 --> W5Col[Column]
    W5Col --> W5Label[Text: Collection d'icônes]
    W5Col --> W5Row[Row<br/>spaceAround]
    W5Row --> Icon1[Icon Home<br/>blue]
    W5Row --> Icon2[Icon Person<br/>green]
    W5Row --> Icon3[Icon Settings<br/>grey]
    W5Row --> Icon4[Icon Notifications<br/>orange]
    
    W6 --> W6Cont[Container<br/>Gradient + Shadow]
    W6Cont --> W6Mat[Material transparent]
    W6Mat --> W6Ink[InkWell]
    W6Ink --> W6Pad[Padding]
    W6Pad --> W6Text[Text: Bouton Exemple]
    
    FAB --> FABIcon[Icon: add]
    
    style Main fill:#FAFAFA,stroke:#424242,stroke-width:2px,color:#000
    style App fill:#FFEBEE,stroke:#C62828,stroke-width:2px,color:#000
    style Page fill:#FFF3E0,stroke:#E65100,stroke-width:2px,color:#000
    style Scaffold fill:#E3F2FD,stroke:#1565C0,stroke-width:2px,color:#000
    style W1 fill:#E8F5E9,stroke:#2E7D32,stroke-width:1px,color:#000
    style W2 fill:#E8F5E9,stroke:#2E7D32,stroke-width:1px,color:#000
    style W3 fill:#E8F5E9,stroke:#2E7D32,stroke-width:1px,color:#000
    style W4 fill:#E8F5E9,stroke:#2E7D32,stroke-width:1px,color:#000
    style W5 fill:#E8F5E9,stroke:#2E7D32,stroke-width:1px,color:#000
    style W6 fill:#E8F5E9,stroke:#2E7D32,stroke-width:1px,color:#000
    style Space1 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
    style Space2 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
    style Space3 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
    style Space4 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
    style Space5 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
```

## 3. Disposition Layout - Column (Vertical)

```mermaid
graph TB
    subgraph PageAccueil["PageAccueil - Column Verticale"]
        direction TB
        T1[TitreSection<br/>Bienvenue dans Flutter!]
        S1[SizedBox 20px<br/>espacement]
        T2[ContainerColore<br/>Container avec fond bleu]
        S2[SizedBox 20px<br/>espacement]
        T3[SectionRow<br/>Disposition horizontale]
        S3[SizedBox 20px<br/>espacement]
        T4[SectionCartes<br/>Cards Material Design]
        S4[SizedBox 20px<br/>espacement]
        T5[SectionIcones<br/>Collection d'icônes]
        S5[SizedBox 20px<br/>espacement]
        T6[BoutonDecoratif<br/>Bouton avec gradient]
        
        T1 --> S1
        S1 --> T2
        T2 --> S2
        S2 --> T3
        T3 --> S3
        S3 --> T4
        T4 --> S4
        S4 --> T5
        T5 --> S5
        S5 --> T6
    end
    
    style PageAccueil fill:#FAFAFA,stroke:#424242,stroke-width:2px,color:#000
    style T1 fill:#E3F2FD,stroke:#1976D2,stroke-width:2px,color:#000
    style T2 fill:#BBDEFB,stroke:#1976D2,stroke-width:2px,color:#000
    style T3 fill:#90CAF9,stroke:#1976D2,stroke-width:2px,color:#000
    style T4 fill:#64B5F6,stroke:#1976D2,stroke-width:2px,color:#000
    style T5 fill:#42A5F5,stroke:#1976D2,stroke-width:2px,color:#000
    style T6 fill:#1E88E5,stroke:#1976D2,stroke-width:2px,color:#fff
    style S1 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
    style S2 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
    style S3 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
    style S4 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
    style S5 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#666
```

## 4. SectionRow - Disposition Horizontale

```mermaid
graph TB
    subgraph SectionRowWidget["SectionRow - Row Horizontale"]
        direction TB
        Label[Text: Exemple de Row<br/>disposition horizontale]
        
        subgraph RowLayout["Row avec MainAxisAlignment.spaceEvenly"]
            direction LR
            Space1[espace]
            Box1[Container<br/>Box 1<br/>100x100<br/>rouge clair]
            Space2[espace]
            Box2[Container<br/>Box 2<br/>100x100<br/>vert clair]
            Space3[espace]
            Box3[Container<br/>Box 3<br/>100x100<br/>orange clair]
            Space4[espace]
            
            Space1 -.-> Box1
            Box1 -.-> Space2
            Space2 -.-> Box2
            Box2 -.-> Space3
            Space3 -.-> Box3
            Box3 -.-> Space4
        end
        
        Label --> RowLayout
    end
    
    style SectionRowWidget fill:#FAFAFA,stroke:#424242,stroke-width:2px,color:#000
    style Label fill:#E0E0E0,stroke:#757575,stroke-width:1px,color:#000
    style RowLayout fill:#F5F5F5,stroke:#9E9E9E,stroke-width:2px,color:#000
    style Box1 fill:#FFCDD2,stroke:#E57373,stroke-width:2px,color:#000
    style Box2 fill:#C8E6C9,stroke:#81C784,stroke-width:2px,color:#000
    style Box3 fill:#FFE0B2,stroke:#FFB74D,stroke-width:2px,color:#000
    style Space1 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,stroke-dasharray: 5 5,color:#999
    style Space2 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,stroke-dasharray: 5 5,color:#999
    style Space3 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,stroke-dasharray: 5 5,color:#999
    style Space4 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,stroke-dasharray: 5 5,color:#999
```

## 5. SectionCartes - Structure des Cards

```mermaid
graph TB
    subgraph SectionCartesWidget["SectionCartes - Cards Material Design"]
        Label[Text: Exemples de Cards]
        
        subgraph Carte1["CarteInfo 1"]
            Card1[Card avec elevation:4]
            Card1 --> Tile1[ListTile]
            
            Tile1 --> L1[leading:<br/>Icon star<br/>couleur amber<br/>taille 40px]
            Tile1 --> T1[title:<br/>Carte 1<br/>style bold]
            Tile1 --> S1[subtitle:<br/>Description<br/>de la carte 1]
            Tile1 --> Tr1[trailing:<br/>Icon arrow<br/>forward ios]
        end
        
        subgraph Carte2["CarteInfo 2"]
            Card2[Card avec elevation:4]
            Card2 --> Tile2[ListTile]
            
            Tile2 --> L2[leading:<br/>Icon favorite<br/>couleur rouge<br/>taille 40px]
            Tile2 --> T2[title:<br/>Carte 2<br/>style bold]
            Tile2 --> S2[subtitle:<br/>Description<br/>de la carte 2]
            Tile2 --> Tr2[trailing:<br/>Icon arrow<br/>forward ios]
        end
        
        Label --> Carte1
        Carte1 --> Carte2
    end
    
    style SectionCartesWidget fill:#FAFAFA,stroke:#424242,stroke-width:2px,color:#000
    style Label fill:#E0E0E0,stroke:#757575,stroke-width:1px,color:#000
    style Carte1 fill:#FFF8E1,stroke:#FFA726,stroke-width:2px,color:#000
    style Carte2 fill:#FFEBEE,stroke:#E57373,stroke-width:2px,color:#000
    style Card1 fill:#FFFFFF,stroke:#BDBDBD,stroke-width:1px,color:#000
    style Card2 fill:#FFFFFF,stroke:#BDBDBD,stroke-width:1px,color:#000
    style Tile1 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#000
    style Tile2 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,color:#000
    style L1 fill:#FFE082,stroke:#FFA726,stroke-width:1px,color:#000
    style L2 fill:#FFCDD2,stroke:#E57373,stroke-width:1px,color:#000
```

## 6. SectionIcones - Disposition des Icônes

```mermaid
graph TB
    subgraph SectionIconesWidget["SectionIcones - Row avec spaceAround"]
        direction TB
        
        LabelIcones[Text: Collection d'icônes]
        
        subgraph RowIcones["Row - 4 icônes avec labels"]
            direction LR
            
            S1[espace]
            
            subgraph Icon1Col["Column 1"]
                I1[Icon home<br/>couleur bleu<br/>taille 40px]
                T1[Text: Home<br/>taille 12px]
                I1 --> T1
            end
            
            S2[espace]
            
            subgraph Icon2Col["Column 2"]
                I2[Icon person<br/>couleur vert<br/>taille 40px]
                T2[Text: Profil<br/>taille 12px]
                I2 --> T2
            end
            
            S3[espace]
            
            subgraph Icon3Col["Column 3"]
                I3[Icon settings<br/>couleur gris<br/>taille 40px]
                T3[Text: Paramètres<br/>taille 12px]
                I3 --> T3
            end
            
            S4[espace]
            
            subgraph Icon4Col["Column 4"]
                I4[Icon notifications<br/>couleur orange<br/>taille 40px]
                T4[Text: Alertes<br/>taille 12px]
                I4 --> T4
            end
            
            S5[espace]
            
            S1 -.-> Icon1Col
            Icon1Col -.-> S2
            S2 -.-> Icon2Col
            Icon2Col -.-> S3
            S3 -.-> Icon3Col
            Icon3Col -.-> S4
            S4 -.-> Icon4Col
            Icon4Col -.-> S5
        end
        
        LabelIcones --> RowIcones
    end
    
    style SectionIconesWidget fill:#FAFAFA,stroke:#424242,stroke-width:2px,color:#000
    style LabelIcones fill:#E0E0E0,stroke:#757575,stroke-width:1px,color:#000
    style RowIcones fill:#F5F5F5,stroke:#9E9E9E,stroke-width:2px,color:#000
    style Icon1Col fill:#E3F2FD,stroke:#42A5F5,stroke-width:2px,color:#000
    style Icon2Col fill:#E8F5E9,stroke:#66BB6A,stroke-width:2px,color:#000
    style Icon3Col fill:#EEEEEE,stroke:#78909C,stroke-width:2px,color:#000
    style Icon4Col fill:#FFF3E0,stroke:#FFB74D,stroke-width:2px,color:#000
    style S1 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,stroke-dasharray: 5 5,color:#999
    style S2 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,stroke-dasharray: 5 5,color:#999
    style S3 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,stroke-dasharray: 5 5,color:#999
    style S4 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,stroke-dasharray: 5 5,color:#999
    style S5 fill:#FAFAFA,stroke:#E0E0E0,stroke-width:1px,stroke-dasharray: 5 5,color:#999
```

## 7. BoutonDecoratif - Architecture en Couches

```mermaid
graph TB
    subgraph BoutonWidget["BoutonDecoratif - 5 Couches Imbriquées"]
        
        Layer1[Couche 1: Container<br/>Conteneur principal]
        Layer1Desc[BoxDecoration:<br/>- LinearGradient bleu vers violet<br/>- BorderRadius 30px forme pilule<br/>- BoxShadow ombre bleue floue]
        
        Layer2[Couche 2: Material<br/>Surface Material Design]
        Layer2Desc[Propriété:<br/>color transparent<br/>permet de voir le gradient]
        
        Layer3[Couche 3: InkWell<br/>Zone interactive]
        Layer3Desc[Propriétés:<br/>onTap pour action<br/>borderRadius 30px<br/>effet ondulation au clic]
        
        Layer4[Couche 4: Padding<br/>Espacement interne]
        Layer4Desc[EdgeInsets:<br/>horizontal 40px<br/>vertical 16px]
        
        Layer5[Couche 5: Text<br/>Contenu textuel]
        Layer5Desc[Style:<br/>Bouton Exemple<br/>blanc, bold, 18px<br/>letterSpacing 0.5]
        
        Layer1 --> Layer1Desc
        Layer1 --> Layer2
        Layer2 --> Layer2Desc
        Layer2 --> Layer3
        Layer3 --> Layer3Desc
        Layer3 --> Layer4
        Layer4 --> Layer4Desc
        Layer4 --> Layer5
        Layer5 --> Layer5Desc
    end
    
    style BoutonWidget fill:#FAFAFA,stroke:#424242,stroke-width:3px,color:#000
    style Layer1 fill:#E1BEE7,stroke:#8E24AA,stroke-width:2px,color:#000
    style Layer2 fill:#CE93D8,stroke:#8E24AA,stroke-width:2px,color:#000
    style Layer3 fill:#BA68C8,stroke:#8E24AA,stroke-width:2px,color:#000
    style Layer4 fill:#AB47BC,stroke:#8E24AA,stroke-width:2px,color:#fff
    style Layer5 fill:#9C27B0,stroke:#8E24AA,stroke-width:2px,color:#fff
    style Layer1Desc fill:#F3E5F5,stroke:#BA68C8,stroke-width:1px,color:#000
    style Layer2Desc fill:#F3E5F5,stroke:#BA68C8,stroke-width:1px,color:#000
    style Layer3Desc fill:#F3E5F5,stroke:#BA68C8,stroke-width:1px,color:#000
    style Layer4Desc fill:#F3E5F5,stroke:#BA68C8,stroke-width:1px,color:#000
    style Layer5Desc fill:#F3E5F5,stroke:#BA68C8,stroke-width:1px,color:#000
```

## 8. Flux de Construction des Widgets

```mermaid
sequenceDiagram
    participant Main as main()
    participant App as MonApplication
    participant Mat as MaterialApp
    participant Page as PageAccueil
    participant Scaffold as Scaffold
    participant Body as Body Widgets
    
    Main->>App: runApp()
    Note over App: Instanciation du<br/>widget racine
    
    App->>Mat: build(context)
    Note over Mat: Configuration du<br/>MaterialApp + Theme
    
    Mat->>Page: home: PageAccueil()
    Note over Page: Création de la<br/>page principale
    
    Page->>Scaffold: build(context)
    Note over Scaffold: Structure de page<br/>Material Design
    
    Scaffold->>Scaffold: Créer AppBar
    Scaffold->>Body: Créer Body
    Scaffold->>Scaffold: Créer FAB
    
    Body->>Body: TitreSection.build()
    Body->>Body: ContainerColore.build()
    Body->>Body: SectionRow.build()
    Body->>Body: SectionCartes.build()
    Body->>Body: SectionIcones.build()
    Body->>Body: BoutonDecoratif.build()
    
    Note over Body: Tous les widgets<br/>sont construits
    
    Body-->>Scaffold: Widget tree complet
    Scaffold-->>Page: Scaffold configuré
    Page-->>Mat: Page construite
    Mat-->>App: MaterialApp configuré
    App-->>Main: Application lancée
    
    Note over Main,Body: L'interface est affichée<br/>à l'écran
```

## 9. Types de Widgets Utilisés

```mermaid
mindmap
  root((Widgets<br/>Flutter))
    Stateless Custom
      MonApplication
      PageAccueil
      TitreSection
      ContainerColore
      SectionRow
      SectionCartes
      CarteInfo
      SectionIcones
      BoutonDecoratif
    Material Design
      MaterialApp
      Scaffold
      AppBar
      Card
      ListTile
      FloatingActionButton
    Layout
      Column
      Row
      SingleChildScrollView
      Center
      Padding
    Basic
      Container
      Text
      Icon
      SizedBox
      Material
      InkWell
```

## 10. Paramètres et Props Flow

```mermaid
graph LR
    subgraph PropsFlow["Flux des Paramètres - Top Down"]
        Parent[PageAccueil<br/>Widget parent]
        
        Parent -->|titre: String| W1[TitreSection<br/>Widget enfant]
        
        Parent -->|couleur: Color<br/>texte: String| W2[ContainerColore<br/>Widget enfant]
        
        Parent -->|Aucun paramètre| W3[SectionRow<br/>Widget enfant]
        
        Parent -->|Aucun paramètre| W4[SectionCartes<br/>Widget enfant]
        
        W4 -->|titre: String<br/>sousTitre: String<br/>icone: IconData<br/>couleurIcone: Color| C1[CarteInfo 1<br/>Widget petit-enfant]
        
        W4 -->|titre: String<br/>sousTitre: String<br/>icone: IconData<br/>couleurIcone: Color| C2[CarteInfo 2<br/>Widget petit-enfant]
        
        Parent -->|Aucun paramètre| W5[SectionIcones<br/>Widget enfant]
        
        Parent -->|texte: String| W6[BoutonDecoratif<br/>Widget enfant]
    end
    
    style PropsFlow fill:#FAFAFA,stroke:#424242,stroke-width:2px,color:#000
    style Parent fill:#FFF9C4,stroke:#F57C00,stroke-width:3px,color:#000
    style W1 fill:#C8E6C9,stroke:#43A047,stroke-width:2px,color:#000
    style W2 fill:#C8E6C9,stroke:#43A047,stroke-width:2px,color:#000
    style W3 fill:#C8E6C9,stroke:#43A047,stroke-width:2px,color:#000
    style W4 fill:#C8E6C9,stroke:#43A047,stroke-width:2px,color:#000
    style W5 fill:#C8E6C9,stroke:#43A047,stroke-width:2px,color:#000
    style W6 fill:#C8E6C9,stroke:#43A047,stroke-width:2px,color:#000
    style C1 fill:#A5D6A7,stroke:#2E7D32,stroke-width:2px,color:#000
    style C2 fill:#A5D6A7,stroke:#2E7D32,stroke-width:2px,color:#000
```

## 11. Cycle de Vie des Stateless Widgets

```mermaid
stateDiagram-v2
    [*] --> Creation: Widget instancié
    Creation --> Build: build() appelé
    Build --> Rendu: Widget tree construit
    Rendu --> Affichage: Rendu sur l'écran
    
    Affichage --> Build: Parent reconstruit
    Affichage --> [*]: Widget détruit
    
    note right of Creation
        const MonWidget({
          required this.data
        })
        Construction du widget
        avec paramètres
    end note
    
    note right of Build
        Widget build(BuildContext context) {
          return Container(...);
        }
        Création de l'arbre
        des widgets enfants
    end note
    
    note right of Affichage
        Widget affiché à l'écran
        Pas de setState()
        Immuable (final fields)
        Ne peut pas changer
    end note
```

## 12. Architecture Visuelle de l'Écran

```mermaid
graph TB
    subgraph Screen["Ecran de l'Application Flutter"]
        subgraph AppBarZone["AppBar - Barre superieure"]
            AppBarContent[Demonstration Stateless Widgets<br/>Titre centre, fond bleu, texte blanc]
        end
        
        subgraph ScrollZone["Zone Defilante - SingleChildScrollView"]
            Zone1[TitreSection<br/>Bienvenue dans Flutter!<br/>Titre 28px, bleu fonce, centre]
            
            Zone2[ContainerColore<br/>Container avec fond colore<br/>BorderRadius 15px, BoxShadow<br/>Texte blanc 18px centre]
            
            Zone3[SectionRow<br/>Exemple de Row disposition horizontale<br/>3 Containers 100x100: rouge, vert, orange<br/>Alignement spaceEvenly]
            
            Zone4[SectionCartes<br/>Exemples de Cards Material Design<br/>Card 1: Icon star amber + texte<br/>Card 2: Icon favorite rouge + texte<br/>ListTile avec leading, title, subtitle, trailing]
            
            Zone5[SectionIcones<br/>Collection d'icones avec labels<br/>Row spaceAround avec 4 Columns<br/>Icons: home, person, settings, notifications<br/>Taille 40px avec labels 12px]
            
            Zone6[BoutonDecoratif<br/>Bouton avec gradient bleu vers violet<br/>BorderRadius 30px forme pilule<br/>BoxShadow + InkWell effet tactile<br/>Texte blanc bold 18px centre]
        end
        
        subgraph FABZone["FloatingActionButton"]
            FABContent[Bouton flottant<br/>Icon add +<br/>Fond bleu, icone blanche]
        end
        
        AppBarZone --> Zone1
        Zone1 --> Zone2
        Zone2 --> Zone3
        Zone3 --> Zone4
        Zone4 --> Zone5
        Zone5 --> Zone6
        Zone6 -.-> FABZone
    end
    
    style Screen fill:#F5F5F5,stroke:#424242,stroke-width:3px,color:#000
    style AppBarZone fill:#1976D2,stroke:#0D47A1,stroke-width:2px,color:#fff
    style AppBarContent fill:#1565C0,stroke:#0D47A1,stroke-width:1px,color:#fff
    style ScrollZone fill:#FAFAFA,stroke:#9E9E9E,stroke-width:2px,color:#000
    style Zone1 fill:#E3F2FD,stroke:#1976D2,stroke-width:1px,color:#000
    style Zone2 fill:#BBDEFB,stroke:#1976D2,stroke-width:1px,color:#000
    style Zone3 fill:#90CAF9,stroke:#1976D2,stroke-width:1px,color:#000
    style Zone4 fill:#64B5F6,stroke:#1976D2,stroke-width:1px,color:#000
    style Zone5 fill:#42A5F5,stroke:#1976D2,stroke-width:1px,color:#000
    style Zone6 fill:#1E88E5,stroke:#1976D2,stroke-width:1px,color:#fff
    style FABZone fill:#FF6F00,stroke:#E65100,stroke-width:2px,color:#fff
    style FABContent fill:#FB8C00,stroke:#E65100,stroke-width:1px,color:#fff
```

## 13. Comparaison Row vs Column

```mermaid
graph TB
    subgraph Comparison["Comparaison des Layouts"]
        
        subgraph ColLayout["Column - Disposition Verticale"]
            direction TB
            C1[Widget 1<br/>Premier enfant]
            C2[Widget 2<br/>Deuxieme enfant]
            C3[Widget 3<br/>Troisieme enfant]
            C1 --> C2
            C2 --> C3
            CLabel[Main Axis: vertical vers le bas<br/>Cross Axis: horizontal gauche-droite<br/>MainAxisAlignment pour vertical<br/>CrossAxisAlignment pour horizontal]
        end
        
        subgraph RowLayout["Row - Disposition Horizontale"]
            direction LR
            R1[Widget 1<br/>Premier<br/>enfant]
            R2[Widget 2<br/>Deuxieme<br/>enfant]
            R3[Widget 3<br/>Troisieme<br/>enfant]
            R1 --> R2
            R2 --> R3
            RLabel[Main Axis: horizontal gauche-droite<br/>Cross Axis: vertical haut-bas<br/>MainAxisAlignment pour horizontal<br/>CrossAxisAlignment pour vertical]
        end
    end
    
    style Comparison fill:#FAFAFA,stroke:#424242,stroke-width:3px,color:#000
    style ColLayout fill:#F3E5F5,stroke:#8E24AA,stroke-width:2px,color:#000
    style RowLayout fill:#E8F5E9,stroke:#43A047,stroke-width:2px,color:#000
    style C1 fill:#FFCDD2,stroke:#E57373,stroke-width:2px,color:#000
    style C2 fill:#F8BBD0,stroke:#F06292,stroke-width:2px,color:#000
    style C3 fill:#E1BEE7,stroke:#BA68C8,stroke-width:2px,color:#000
    style R1 fill:#C5CAE9,stroke:#7986CB,stroke-width:2px,color:#000
    style R2 fill:#BBDEFB,stroke:#64B5F6,stroke-width:2px,color:#000
    style R3 fill:#B2EBF2,stroke:#4DD0E1,stroke-width:2px,color:#000
    style CLabel fill:#FCE4EC,stroke:#F06292,stroke-width:1px,color:#000
    style RLabel fill:#E0F2F1,stroke:#4DB6AC,stroke-width:1px,color:#000
```

---

## Legende

| Terme | Signification |
|-------|--------------|
| **Widget** | Composant de l'interface Flutter |
| **Stateless** | Widget immuable sans état interne |
| **Container** | Boîte avec décoration et contraintes |
| **Column** | Disposition verticale des enfants |
| **Row** | Disposition horizontale des enfants |
| **Card** | Surface Material Design avec élévation |
| **Scaffold** | Structure de base d'une page Material |
| **AppBar** | Barre d'application en haut de l'écran |
| **FAB** | FloatingActionButton - Bouton flottant |
| **Main Axis** | Axe principal de la disposition |
| **Cross Axis** | Axe perpendiculaire à l'axe principal |
| **Elevation** | Hauteur visuelle d'une surface (ombre) |
| **Theme** | Configuration globale du style visuel |

---

## Convention de Couleurs dans les Diagrammes

- **Bleu clair** (#E3F2FD - #42A5F5) : Widgets principaux, structure
- **Vert clair** (#E8F5E9 - #66BB6A) : Widgets personnalisés
- **Orange/Jaune** (#FFF3E0 - #FFB74D) : Points d'entrée, actions
- **Violet clair** (#F3E5F5 - #AB47BC) : Couches, architecture
- **Gris clair** (#FAFAFA - #9E9E9E) : Espacement, métadonnées
- **Rouge clair** (#FFEBEE - #E57373) : Accents, avertissements

---

## Utilisation des Diagrammes

### Pour les Étudiants

1. **Commencer par le diagramme 1** pour voir la vue d'ensemble
2. **Consulter le diagramme 2** pour la hiérarchie complète
3. **Étudier les diagrammes 3, 4, 13** pour comprendre les layouts
4. **Analyser les diagrammes 5, 6, 7** pour les widgets spécifiques
5. **Examiner les diagrammes 8, 10, 11** pour le flux de données

### Visualisation

Ces diagrammes Mermaid peuvent être visualisés dans :

- **GitHub** : Rendu automatique des diagrammes Mermaid
- **VS Code** : Extension "Markdown Preview Mermaid Support"
- **En ligne** : [mermaid.live](https://mermaid.live) ou [mermaid-js.github.io](https://mermaid-js.github.io/mermaid-live-editor)
- **Documentation** : GitBook, MkDocs, Docusaurus (support natif)

### Export

Pour exporter en image :
1. Copier le code Mermaid
2. Ouvrir [mermaid.live](https://mermaid.live)
3. Coller le code
4. Cliquer sur "Export" (PNG, SVG, PDF)

---

## Notes Pédagogiques

### Points Clés à Retenir

1. **Composition** : Flutter utilise la composition de widgets simples pour créer des interfaces complexes
2. **Immutabilité** : Les Stateless Widgets sont immuables (const, final)
3. **Hiérarchie** : L'arbre des widgets définit la structure de l'interface
4. **Props Flow** : Les données descendent du parent vers les enfants
5. **Build Method** : Chaque widget définit son rendu via build()

### Exercices Suggérés

1. Identifier le widget racine dans le diagramme 1
2. Tracer le chemin de main() jusqu'à un widget Text
3. Compter le nombre de niveaux dans la hiérarchie
4. Expliquer la différence entre Row et Column
5. Dessiner un nouveau widget personnalisé et son intégration
