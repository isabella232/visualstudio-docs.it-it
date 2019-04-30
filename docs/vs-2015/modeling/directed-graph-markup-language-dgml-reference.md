---
title: Indirizzati riferimento Graph Markup Language (DGML) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: cc3e4ae7-60fa-4e22-9227-98020b480b73
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0de96057326a9e4b6a64865ef34972d5542aff30
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442995"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Riferimento di Directed Graph Markup Language (DGML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Directed Graph Markup Language (DGML) descrive le informazioni usate per la visualizzazione e per eseguire l'analisi di complessità, ed è il formato usato per rendere persistenti le mappe codice in Visual Studio. Usa semplice codice XML per descrivere grafici diretti ciclici e aciclici. Un grafico diretto è un set di nodi connessi da collegamenti o bordi. I nodi e i collegamenti possono essere utilizzati per rappresentare strutture di rete, ad esempio elementi in un progetto software.  
  
 Si noti che alcune versioni di Visual Studio supportano solo un subset delle funzionalità DGML; vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
> Quando si modifica un file con estensione dgml, IntelliSense consente di identificare gli attributi disponibili per ogni elemento e i relativi valori. Per specificare il colore in un attributo, utilizzare nomi dei colori comuni, come "Blue", o valori ARGB esadecimali, come "#ffa0b1c3." In DGML viene utilizzato un piccolo subset di formati di definizione dei colori WPF (Windows Presentation Foundation). Per altre informazioni, vedere [classe Colors](http://go.microsoft.com/fwlink/?LinkId=182345).  
  
## <a name="DGML"></a> Sintassi DGML  
 Nella tabella seguente sono descritti i tipi di elementi usati in DGML:  
  
- `<DirectedGraph></DirectedGraph>`  
  
   Questo elemento è l'elemento radice di un documento mappa codice (.dgml). Tutti gli altri elementi DGML sono inclusi nell'ambito di questo elemento.  
  
   Nell'elenco seguente vengono descritti gli attributi facoltativi che è possibile includere:  
  
   `Background` - Colore dello sfondo della mappa  
  
   `BackgroundImage` - Percorso di un file di immagine da usare come sfondo della mappa.  
  
   `GraphDirection`- Quando la mappa viene impostata sul layout struttura ad albero (`Sugiyama`), i nodi vengono disposti in modo che la maggior parte dei collegamenti vada nella direzione specificata: `TopToBottom`, `BottomToTop`, `LeftToRight` o `RightToLeft`. Visualizzare [modificare il layout della mappa](../modeling/browse-and-rearrange-code-maps.md#Selecting).  
  
   `Layout` - Impostare la mappa su uno dei layout seguenti: `None`, `Sugiyama` (layout struttura ad albero), `ForceDirected` (raggruppamenti veloci) o `DependencyMatrix`. Visualizzare [modificare il layout della mappa](../modeling/browse-and-rearrange-code-maps.md#Selecting).  
  
   `NeighborhoodDistance`- Quando la mappa viene impostata sul layout struttura ad albero o raggruppamenti veloci, vengono visualizzati solo i nodi la cui distanza dai nodi selezionati corrisponde a un numero di collegamenti specificato (1-7). Visualizzare [modificare il layout della mappa](../modeling/browse-and-rearrange-code-maps.md#Selecting).  
  
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
  
   `Id`- Nome univoco del nodo e valore predefinito dell'attributo `Label`, se non viene specificato alcun attributo `Label` distinto. Questo nome deve corrispondere all'attributo `Source` o `Target` del collegamento a cui fa riferimento.  
  
   Nell'elenco seguente vengono descritti alcuni degli attributi facoltativi che è possibile includere:  
  
   `Label` -Il nome visualizzato del nodo.  
  
   Attributi di stile. Vedere [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
   `Category` - Nome di una categoria che identifica gli elementi che condividono questo attributo. Per altre informazioni, vedere l'elemento `<Category/>`.  
  
   `Property`- Nome di una proprietà che identifica gli elementi che hanno lo stesso valore della proprietà. Per altre informazioni, vedere l'elemento `<Property/>`.  
  
   `Group`- Se il nodo contiene altri nodi, impostare questo attributo su `Expanded` o su `Collapsed`, per visualizzare o nascondere il relativo contenuto. Deve essere presente un elemento `<Link/>` che include l'attributo `Category="Contains"` e specifica il nodo padre come nodo di origine e il nodo figlio come nodo di destinazione. Visualizzare [raggruppare gli elementi di codice](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).  
  
   `Visibility` - Impostare questo attributo su `Visible`, `Hidden` o `Collapsed`. Vengono usati `System.Windows.Visibility`. Visualizzare [nascondere o mostrare nodi e collegamenti](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).  
  
   `Reference` - Impostare questo attributo per collegare un nodo a un documento o a un URL. Visualizzare [collegare documenti o URL a elementi di codice e collegamenti](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).  
  
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
  
   `Source` - Nodo di origine del collegamento  
  
   `Target` - Nodo di destinazione del collegamento  
  
   Nell'elenco seguente vengono descritti alcuni degli attributi facoltativi che è possibile includere:  
  
   `Label` - Nome visualizzato del collegamento  
  
   Attributi di stile. Vedere [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
   `Category` - Nome di una categoria che identifica gli elementi che condividono questo attributo. Per altre informazioni, vedere l'elemento `<Category/>`.  
  
   `Property`- Nome di una proprietà che identifica gli elementi che hanno lo stesso valore della proprietà. Per altre informazioni, vedere l'elemento `<Property/>`.  
  
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
  
   `BasedOn` - Categoria padre da cui eredita l'oggetto `<Category/>` dell'elemento corrente.  
  
   Nell'esempio per questo elemento la categoria `FailedTest` eredita l'attributo `Stroke` dalla categoria `PassedTest`. Vedere la sezione "per creare categorie gerarchiche" in [personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
   Le categorie forniscono inoltre il comportamento di base dei modelli che controlla l'aspetto di nodi e collegamenti quando vengono visualizzati in una mappa. Vedere [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
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
  
  - `Id`- Nome univoco della proprietà e valore predefinito dell'attributo `Label`, se non viene specificato alcun attributo `Label` distinto.  
  
  - `DataType` - Tipo di dati archiviati dalla proprietà  
  
    Se si desidera che la proprietà venga visualizzata nel **delle proprietà** finestra, usare il `Label` proprietà per specificare nome visualizzato della proprietà.  
  
    Visualizzare [assegnare categorie a elementi di codice e collegamenti](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).  
  
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
  
### <a name="AddAlias"></a> Alias per i percorsi di uso comune  
 Sostituendo i percorsi d'uso comune con alias è possibile ridurre le dimensioni del file con estensione dgml e il tempo necessario per caricare o salvare il file. Per creare un alias, aggiungere una sezione `<Paths></Paths>` alla fine del file con estensione dgml. In questa sezione aggiungere un elemento `<Path/>` per definire un alias per il percorso:  
  
```xml  
<Paths>  
   <Path Id="MyPathAlias" Value="C:\...\..." />  
</Paths>  
```  
  
 Per fare riferimento l'alias da un elemento nel file con estensione dgml, racchiudere il `Id` del \<Path / > elemento con un segno di dollaro ($) e parentesi (()):  
  
```xml  
<Nodes>  
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />  
</Nodes>  
<Properties>  
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />  
</Properties>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)   
 [Usare le mappe codice per il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
