---
title: Riferimento di Directed Graph Markup Language (DGML)
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2363e5131dd499dd85a5822ed15e2bfe473f1e1c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596636"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Riferimento di Directed Graph Markup Language (DGML)

Directed Graph Markup Language (DGML) descrive le informazioni usate per la visualizzazione e per eseguire l'analisi di complessità, ed è il formato usato per rendere persistenti le mappe codice in Visual Studio. Usa semplice codice XML per descrivere grafici diretti ciclici e aciclici. Un grafico diretto è un set di nodi connessi da collegamenti o bordi. I nodi e i collegamenti possono essere utilizzati per rappresentare strutture di rete, ad esempio elementi in un progetto software.

Si noti che alcune versioni di Visual Studio supportano solo un subset di funzionalità DGML, vedere [supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Quando si modifica un file con estensione dgml, IntelliSense consente di identificare gli attributi disponibili per ogni elemento e i relativi valori. Per specificare il colore in un attributo, utilizzare nomi dei colori comuni, come "Blue", o valori ARGB esadecimali, come "#ffa0b1c3." In DGML viene utilizzato un piccolo subset di formati di definizione dei colori WPF (Windows Presentation Foundation). Per altre informazioni, vedere [classe Colors](/dotnet/api/system.windows.media.colors?view=netframework-4.8).

## <a name="DGML"></a>Sintassi DGML

Nella tabella seguente sono descritti i tipi di elementi usati in DGML:

- `<DirectedGraph></DirectedGraph>`

   Questo elemento è l'elemento radice di un documento mappa codice (.dgml). Tutti gli altri elementi DGML sono inclusi nell'ambito di questo elemento.

   Nell'elenco seguente vengono descritti gli attributi facoltativi che è possibile includere:

   `Background`: colore dello sfondo della mappa

   `BackgroundImage`: il percorso di un file di immagine da utilizzare come sfondo della mappa.

   `GraphDirection`: quando la mappa è impostata su layout struttura ad albero (`Sugiyama`), disporre i nodi in modo che la maggior parte dei collegamenti scorrano nella direzione specificata: `TopToBottom`, `BottomToTop`, `LeftToRight`o `RightToLeft`. Vedere [modificare il layout della mappa](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout`: impostare la mappa sui seguenti layout: `None`, `Sugiyama` (layout struttura ad albero), `ForceDirected` (cluster rapidi) o `DependencyMatrix`. Vedere [modificare il layout della mappa](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance`-quando la mappa viene impostata sul layout di struttura ad albero o su un layout di cluster veloce, Mostra solo i nodi che sono un numero specificato (1-7) di collegamenti tra i nodi selezionati. Vedere [modificare il layout della mappa](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   Esempio:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   Questo elemento facoltativo contiene un elenco di elementi `<Node/>` che definiscono i nodi nella mappa. Per altre informazioni, vedere l'elemento `<Node/>`.

  > [!NOTE]
  > Quando si fa riferimento a un nodo non definito in un elemento `<Link/>`, la mappa crea automaticamente un elemento `<Node/>`.

   Esempio:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   Questo elemento definisce un singolo nodo. Esso viene visualizzato nell'elenco di elementi `<Nodes><Nodes/>`.

   L'elemento deve includere gli attributi seguenti:

   `Id`: il nome univoco del nodo e il valore predefinito dell'attributo `Label`, se non è specificato alcun attributo `Label` separato. Questo nome deve corrispondere all'attributo `Source` o `Target` del collegamento a cui fa riferimento.

   Nell'elenco seguente vengono descritti alcuni degli attributi facoltativi che è possibile includere:

   `Label`: il nome visualizzato del nodo.

   Attributi di stile. Vedere [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`: il nome di una categoria che identifica gli elementi che condividono questo attributo. Per altre informazioni, vedere l'elemento `<Category/>`.

   `Property`: il nome di una proprietà che identifica gli elementi con lo stesso valore della proprietà. Per altre informazioni, vedere l'elemento `<Property/>`.

   `Group`- Se il nodo contiene altri nodi, impostare questo attributo su `Expanded` o su `Collapsed`, per visualizzare o nascondere il relativo contenuto. Deve essere presente un elemento `<Link/>` che include l'attributo `Category="Contains"` e specifica il nodo padre come nodo di origine e il nodo figlio come nodo di destinazione. Vedere [elementi di codice del gruppo](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility`: impostare questo attributo su `Visible`, `Hidden`o `Collapsed`. Vengono usati `System.Windows.Visibility`. Vedere [nascondere o visualizzare nodi e collegamenti](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` - Impostare questo attributo per collegare un nodo a un documento o a un URL. Vedere [collegare documenti o URL a elementi di codice e collegamenti](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

   Esempio:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   Questo elemento contiene l'elenco di elementi `<Link>` che definiscono i collegamenti tra i nodi. Per altre informazioni, vedere l'elemento `<Link/>`.

   Esempio:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   Questo elemento definisce un singolo collegamento che connette un nodo di origine a un nodo di destinazione. Esso viene visualizzato nell'elenco di elementi `<Links></Links>`.

  > [!NOTE]
  > Se questa mappa fa riferimento a un nodo non definito, il documento grafico crea automaticamente un nodo con gli attributi specificati, se presenti.

   L'elemento deve includere gli attributi seguenti:

   `Source`: il nodo di origine del collegamento

   `Target` - Nodo di destinazione del collegamento

   Nell'elenco seguente vengono descritti alcuni degli attributi facoltativi che è possibile includere:

   `Label`: il nome visualizzato del collegamento

   Attributi di stile. Vedere [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`: il nome di una categoria che identifica gli elementi che condividono questo attributo. Per altre informazioni, vedere l'elemento `<Category/>`.

   `Property`: il nome di una proprietà che identifica gli elementi con lo stesso valore della proprietà. Per altre informazioni, vedere l'elemento `<Property/>`.

   Esempio:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   Questo elemento contiene l'elenco di elementi `<Category/>`. Per altre informazioni, vedere l'elemento `<Category/>`.

   Esempio:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   Questo elemento definisce un attributo `Category`, utilizzato per identificare gli elementi che condividono questo attributo. Un attributo `Category` può essere usato per organizzare gli elementi della mappa, fornire attributi condivisi tramite ereditarietà o definire metadati aggiuntivi.

   L'elemento deve includere gli attributi seguenti:

   `Id`- Nome univoco della categoria e valore predefinito dell'attributo `Label`, se non viene specificato alcun attributo `Label` distinto.

   Nell'elenco seguente vengono descritti alcuni degli attributi facoltativi che è possibile includere:

   `Label`- Nome descrittivo per la categoria.

   `BasedOn`: la categoria padre dalla quale eredita l'`<Category/>` dell'elemento corrente.

   Nell'esempio per questo elemento la categoria `FailedTest` eredita l'attributo `Stroke` dalla categoria `PassedTest`. Vedere "per creare categorie gerarchiche" in [personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Le categorie forniscono inoltre il comportamento di base dei modelli che controlla l'aspetto di nodi e collegamenti quando vengono visualizzati in una mappa. Vedere [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Esempio:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   Questo elemento contiene l'elenco di elementi `<Property/>`. Per altre informazioni, vedere l'elemento `<Property/>`.

   Esempio:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   Questo elemento definisce un attributo `Property` che è possibile usare per assegnare un valore a qualsiasi attributo o elemento DGML, incluse categorie e altre proprietà.

   L'elemento deve includere gli attributi seguenti:

  - `Id`: il nome univoco della proprietà e il valore predefinito dell'attributo `Label`, se non è specificato alcun attributo `Label` separato.

  - `DataType`: il tipo di dati archiviati dalla proprietà

    Se si desidera che la proprietà venga visualizzata nella finestra **Proprietà** , utilizzare la proprietà `Label` per specificare il nome visualizzato della proprietà.

    Vedere [assegnare categorie a elementi di codice e collegamenti](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

    Esempio:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="AddAlias"></a>Alias per i percorsi di uso comune

Sostituendo i percorsi d'uso comune con alias è possibile ridurre le dimensioni del file con estensione dgml e il tempo necessario per caricare o salvare il file. Per creare un alias, aggiungere una sezione `<Paths></Paths>` alla fine del file con estensione dgml. In questa sezione aggiungere un elemento `<Path/>` per definire un alias per il percorso:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

Per fare riferimento all'alias da un elemento nel file con estensione dgml, racchiudere il `Id` dell'elemento \<path/> con un segno di dollaro ($) e le parentesi (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
