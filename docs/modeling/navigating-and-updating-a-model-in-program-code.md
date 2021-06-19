---
title: Esplorazione e aggiornamento di un modello nel codice del programma
description: Informazioni su come scrivere codice per creare ed eliminare elementi del modello, impostarne le proprietà e creare ed eliminare collegamenti tra gli elementi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b34c51744c6bab1c6021a006f7ec9b4da0f4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390971"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Esplorare e aggiornare i modelli nel codice del programma

È possibile scrivere codice per creare ed eliminare elementi del modello, impostarne le proprietà e creare ed eliminare collegamenti tra gli elementi. Tutte le modifiche devono essere apportate all'interno di una transazione. Se gli elementi vengono visualizzati in un diagramma, il diagramma verrà "corretto" automaticamente alla fine della transazione.

## <a name="an-example-dsl-definition"></a><a name="example"></a> Definizione DSL di esempio
 Questa è la parte principale di DslDefinition.dsl per gli esempi in questo argomento:

 ![Diagramma delle definizioni DSL &#45; modello ad albero di famiglia](../modeling/media/familyt_person.png)

 Questo modello è un'istanza di questo DSL:

 ![Modello dell'albero della famiglia Tudor](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Riferimenti e spazi dei nomi
 Per eseguire il codice in questo argomento, è necessario fare riferimento a:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Il codice userà questo spazio dei nomi:

 `using Microsoft.VisualStudio.Modeling;`

 Inoltre, se si scrive il codice in un progetto diverso da quello in cui è definito il DSL, è necessario importare l'assembly compilato dal progetto Dsl.

## <a name="navigating-the-model"></a><a name="navigation"></a> Esplorazione del modello

### <a name="properties"></a>Proprietà
 Le proprietà di dominio definite nella definizione DSL diventano proprietà a cui è possibile accedere nel codice programma:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Se si desidera impostare una proprietà, è necessario eseguire questa operazione all'interno di una [transazione](#transaction):

 `henry.Name = "Henry VIII";`

 Se nella definizione DSL il tipo di una proprietà **è** **Calculated,** non è possibile impostarlo. Per altre informazioni, vedere [Proprietà di archiviazione calcolate e personalizzate.](../modeling/calculated-and-custom-storage-properties.md)

### <a name="relationships"></a>Relazioni
 Le relazioni di dominio definite nella definizione DSL diventano coppie di proprietà, una per la classe a ogni estremità della relazione. I nomi delle proprietà vengono visualizzati nel diagramma DslDefinition come etichette sui ruoli in ogni lato della relazione. A seconda della molteplicità del ruolo, il tipo della proprietà è la classe all'altra estremità della relazione o una raccolta di tale classe.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Le proprietà alle estremità opposte di una relazione sono sempre reciproche. Quando viene creato o eliminato un collegamento, le proprietà del ruolo in entrambi gli elementi vengono aggiornate. L'espressione seguente (che usa le estensioni `System.Linq` di ) è sempre true per la relazione ParentsHaveChildren nell'esempio:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Una relazione è rappresentata anche da un elemento del modello denominato *collegamento*, che è un'istanza del tipo di relazione di dominio. Un collegamento ha sempre un elemento di origine e un elemento di destinazione. L'elemento di origine e l'elemento di destinazione possono essere gli stessi.

 È possibile accedere a un collegamento e alle relative proprietà:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Per impostazione predefinita, non è consentito collegare più di un'istanza di una relazione a qualsiasi coppia di elementi del modello. Tuttavia, se nella definizione DSL il flag è true per la relazione, potrebbero essere presenti più collegamenti ed è `Allow Duplicates` necessario usare `GetLinks` :

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Sono disponibili anche altri metodi per l'accesso ai collegamenti. Ad esempio:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Ruoli nascosti.** Se nella definizione DSL Is **Property Generated** è **false** per un ruolo specifico, non viene generata alcuna proprietà corrispondente a tale ruolo. Tuttavia, è comunque possibile accedere ai collegamenti e attraversare i collegamenti usando i metodi della relazione:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 L'esempio usato più di frequente è la relazione , che collega un elemento del <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> modello alla forma che lo visualizza in un diagramma:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Directory dell'elemento
 È possibile accedere a tutti gli elementi nell'archivio usando la directory degli elementi:

 `store.ElementDirectory.AllElements`

 Sono disponibili anche metodi per la ricerca di elementi, ad esempio:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="accessing-class-information"></a><a name="metadata"></a> Accesso alle informazioni sulle classi
 È possibile ottenere informazioni su classi, relazioni e altri aspetti della definizione DSL. Ad esempio:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Le classi predecessore degli elementi del modello sono le seguenti:

- ModelElement: tutti gli elementi e le relazioni sono ModelElement

- ElementLink: tutte le relazioni sono ElementLinks

## <a name="perform-changes-inside-a-transaction"></a><a name="transaction"></a> Eseguire modifiche all'interno di una transazione
 Ogni volta che il codice del programma modifica qualsiasi elemento nell'archivio, deve eseguire questa operazione all'interno di una transazione. Questo vale per tutti gli elementi del modello, le relazioni, le forme, i diagrammi e le relative proprietà. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Il metodo più pratico per gestire una transazione è con `using` un'istruzione racchiusa in `try...catch` un'istruzione :

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 È possibile apportare un numero qualsiasi di modifiche all'interno di una transazione. È possibile aprire nuove transazioni all'interno di una transazione attiva.

 Per rendere permanenti le modifiche, è `Commit` necessario che la transazione venga eliminata. Se si verifica un'eccezione che non viene rilevata all'interno della transazione, l'archivio verrà reimpostato sullo stato precedente alle modifiche.

## <a name="creating-model-elements"></a><a name="elements"></a> Creazione di elementi del modello
 Questo esempio aggiunge un elemento a un modello esistente:

```csharp
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 Questo esempio illustra questi punti essenziali sulla creazione di un elemento:

- Creare il nuovo elemento in una partizione specifica dell'archivio. Per gli elementi del modello e le relazioni, ma non le forme, questa è in genere la partizione predefinita.

- Renderla la destinazione di una relazione di incorporamento. In DslDefinition di questo esempio ogni persona deve essere la destinazione della relazione di incorporamento FamilyTreeHasPeople. A tale scopo, è possibile impostare la proprietà del ruolo FamilyTreeModel dell'oggetto Person o aggiungere person alla proprietà del ruolo People dell'oggetto FamilyTreeModel.

- Impostare le proprietà di un nuovo elemento, in particolare la proprietà per la quale `IsName` è true in DslDefinition. Questo flag contrassegna la proprietà che serve a identificare l'elemento in modo univoco all'interno del proprietario. In questo caso, la proprietà Name ha tale flag.

- La definizione DSL di questo DSL deve essere stata caricata nell'archivio. Se si scrive un'estensione, ad esempio un comando di menu, questa operazione in genere è già vera. In altri casi, è possibile caricare in modo esplicito il modello nello Store o usare [ModelBus](/previous-versions/ee904639(v=vs.140)) per caricarlo. Per altre informazioni, vedere [Procedura: Aprire un modello da file nel codice programma.](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Quando si crea un elemento in questo modo, viene creata automaticamente una forma (se il DSL ha un diagramma). Viene visualizzato in una posizione assegnata automaticamente, con forma, colore e altre caratteristiche predefinite. Per controllare dove e come viene visualizzata la forma associata, vedere [Creazione di un elemento e della relativa forma.](#merge)

## <a name="creating-relationship-links"></a><a name="links"></a> Creazione di collegamenti di relazione
 Nella definizione DSL di esempio sono definite due relazioni. Ogni relazione definisce una *proprietà role* nella classe a ogni estremità della relazione.

 Esistono tre modi per creare un'istanza di una relazione. Ognuno di questi tre metodi ha lo stesso effetto:

- Impostare la proprietà del lettore del ruolo di origine. Ad esempio:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Impostare la proprietà del ruolo lettore di destinazione. Ad esempio:

  - `edward.familyTreeModel = familyTree;`

       La molteplicità di questo ruolo è `1..1` , quindi viene assegnato il valore .

  - `henry.Children.Add(edward);`

       La molteplicità di questo ruolo è `0..*` , quindi si aggiunge alla raccolta .

- Costruire un'istanza della relazione in modo esplicito. Ad esempio:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  L'ultimo metodo è utile se si desidera impostare proprietà sulla relazione stessa.

  Quando si crea un elemento in questo modo, viene creato automaticamente un connettore nel diagramma, ma ha una forma, un colore e altre caratteristiche predefinite. Per controllare la modalità di creazione del connettore associato, vedere [Creazione di un elemento e della relativa forma.](#merge)

## <a name="deleting-elements"></a><a name="deleteelements"></a> Eliminazione di elementi

Eliminare un elemento chiamando `Delete()` :

`henry.Delete();`

Questa operazione eliminerà anche:

- La relazione si collega a e dall'elemento . Ad esempio, `edward.Parents` non conterrà più `henry` .

- Elementi nei ruoli per i quali il `PropagatesDelete` flag è true. Ad esempio, la forma che visualizza l'elemento verrà eliminata.

Per impostazione predefinita, ogni relazione di incorporamento `PropagatesDelete` ha true nel ruolo di destinazione. `henry`L'eliminazione non elimina , ma elimina tutti gli oggetti `familyTree` `familyTree.Delete()` `Persons` .

Per impostazione predefinita, `PropagatesDelete` non è true per i ruoli delle relazioni di riferimento.

È possibile fare in modo che le regole di eliminazione omettono propagazioni specifiche quando si elimina un oggetto. Ciò è utile se si sostituisce un elemento per un altro. Specificare il GUID di uno o più ruoli per i quali l'eliminazione non deve essere propagata. Il GUID può essere ottenuto dalla classe di relazione:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

Questo particolare esempio non avrebbe alcun effetto, perché `PropagatesDelete` è per i ruoli della `false` `ParentsHaveChildren` relazione.

In alcuni casi, l'eliminazione viene impedita dall'esistenza di un blocco, nell'elemento o in un elemento che verrebbe eliminato dalla propagazione. È possibile usare `element.CanDelete()` per verificare se l'elemento può essere eliminato.

## <a name="deleting-relationship-links"></a><a name="deletelinks"></a> Eliminazione di collegamenti di relazione
 È possibile eliminare un collegamento di relazione rimuovendo un elemento da una proprietà del ruolo:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 È anche possibile eliminare il collegamento in modo esplicito:

 `edwardHenryLink.Delete();`

 Questi tre metodi hanno tutti lo stesso effetto. È necessario usare solo uno di essi.

 Se il ruolo ha la molteplicità 0..1 o 1..1, è possibile impostarlo su `null` o su un altro valore:

 `edward.FamilyTreeModel = null;` O:

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a> Riordino dei collegamenti di una relazione
 I collegamenti di una relazione specifica di origine o di destinazione di un particolare elemento del modello hanno una sequenza specifica. Vengono visualizzati nell'ordine in cui sono stati aggiunti. Ad esempio, questa istruzione restituisce sempre gli elementi figlio nello stesso ordine:

 `foreach (Person child in henry.Children) ...`

 È possibile modificare l'ordine dei collegamenti:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a><a name="locks"></a> Serrature
 Le modifiche potrebbero essere impedite da un blocco. I blocchi possono essere impostati su singoli elementi, partizioni e nell'archivio. Se uno di questi livelli ha un blocco che impedisce il tipo di modifica che si vuole apportare, è possibile che venga generata un'eccezione quando si tenta di eseguire questa operazione. È possibile scoprire se i blocchi vengono impostati usando l'elemento . GetLocks(), ovvero un metodo di estensione definito nello spazio dei nomi <xref:Microsoft.VisualStudio.Modeling.Immutability> .

 Per altre informazioni, vedere [Definizione di un criterio di blocco per creare Read-Only segmenti](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy-and-paste"></a><a name="copy"></a> Copiare e incollare
 È possibile copiare elementi o gruppi di elementi in <xref:System.Windows.Forms.IDataObject> :

```csharp
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Gli elementi vengono archiviati come gruppo di elementi serializzati.

 È possibile unire elementi da un oggetto IDataObject in un modello:

```csharp
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` può accettare o `PresentationElement` `ModelElement` . Se si assegna un , è anche possibile specificare una `PresentationElement` posizione nel diagramma di destinazione come terzo parametro.

## <a name="navigating-and-updating-diagrams"></a><a name="diagrams"></a> Esplorazione e aggiornamento dei diagrammi
 In un DSL, l'elemento del modello di dominio, che rappresenta un concetto come Person o Song, è separato dall'elemento shape, che rappresenta ciò che si vede nel diagramma. L'elemento del modello di dominio archivia le proprietà e le relazioni importanti dei concetti. L'elemento shape archivia le dimensioni, la posizione e il colore della visualizzazione dell'oggetto nel diagramma e il layout delle relative parti componenti.

### <a name="presentation-elements"></a>Elementi di presentazione
 ![Diagramma classi di tipi di forma di base e di elemento](../modeling/media/dslshapesandelements.png)

 Nella definizione DSL ogni elemento specificato crea una classe derivata da una delle classi standard seguenti.

|Tipo di elemento|Classe base|
|-|-|
|Classe di dominio|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Relazione di dominio|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Con forme|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Connettore|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagramma|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Un elemento in un diagramma rappresenta in genere un elemento del modello. In genere (ma non sempre), un rappresenta <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> un'istanza della classe di dominio e un oggetto rappresenta <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> un'istanza di relazione di dominio. La <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relazione collega un nodo o una forma di collegamento all'elemento del modello che rappresenta.

 Ogni forma nodo o collegamento appartiene a un diagramma. Una forma di collegamento binario connette due forme nodo.

 Le forme possono avere forme figlio in due set. Una forma nel `NestedChildShapes` set è limitata al rettangolo di selezione del relativo elemento padre. Una forma nell'elenco può essere visualizzata all'esterno o in parte all'esterno dei limiti dell'elemento padre, ad esempio `RelativeChildShapes` un'etichetta o una porta. Un diagramma non dispone `RelativeChildShapes` di e `Parent` .

### <a name="navigating-between-shapes-and-elements"></a><a name="views"></a> Spostamento tra forme ed elementi
 Gli elementi del modello di dominio e gli elementi di forma sono correlati dalla <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relazione.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 La stessa relazione collega le relazioni ai connettori nel diagramma:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Questa relazione collega anche la radice del modello al diagramma:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Per ottenere l'elemento del modello rappresentato da una forma, usare:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Esplorazione del diagramma
 In generale non è consigliabile spostarsi tra forme e connettori nel diagramma. È meglio spostarsi tra le relazioni nel modello, spostandosi tra le forme e i connettori solo quando è necessario lavorare sull'aspetto del diagramma. Questi metodi collegano i connettori alle forme a ogni estremità:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Molte forme sono composte. sono costituito da una forma padre e da uno o più livelli di elementi figlio. Le forme posizionate rispetto a un'altra forma sono di tipo *figlio.* Quando la forma padre viene spostata, gli elementi figlio si spostano con essa.

 *Gli elementi figlio* relativi possono essere visualizzati all'esterno del rettangolo di selezione della forma padre. *Gli* elementi figlio annidati vengono visualizzati esclusivamente all'interno dei limiti dell'elemento padre.

 Per ottenere il primo set di forme in un diagramma, usare:

 `Diagram.NestedChildShapes`

 Le classi predecessore di forme e connettori sono:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

### <a name="properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a> Proprietà di forme e connettori
 Nella maggior parte dei casi, non è necessario apportare modifiche esplicite alle forme. Dopo aver modificato gli elementi del modello, le regole di correzione aggiornano le forme e i connettori. Per altre informazioni, vedere [Risposta e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

 Tuttavia, è utile apportare alcune modifiche esplicite alle forme nelle proprietà indipendenti degli elementi del modello. Ad esempio, è possibile modificare queste proprietà:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> : determina l'altezza e la larghezza della forma.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> - posizione relativa alla forma o al diagramma padre

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> : set di penna e pennelli usati per disegnare la forma o il connettore

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> - rende invisibile la forma

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> : rende visibile la forma dopo un `Hide()`

### <a name="creating-an-element-and-its-shape"></a><a name="merge"></a> Creazione di un elemento e della relativa forma

Quando si crea un elemento e lo si collega all'albero delle relazioni di incorporamento, viene creata e associata automaticamente una forma. Questa operazione viene eseguita dalle regole di "correzione" che vengono eseguite alla fine della transazione. Tuttavia, la forma verrà visualizzata in una posizione assegnata automaticamente e la forma, il colore e altre caratteristiche avranno valori predefiniti. Per controllare la modalità di creazione della forma, è possibile usare la funzione di unione. È innanzitutto necessario aggiungere gli elementi da aggiungere a un elemento ElementGroup e quindi unire il gruppo nel diagramma.

Questo metodo:

- Imposta il nome, se è stata assegnata una proprietà come nome dell'elemento.

- Osserva tutte le direttive di unione degli elementi specificate nella definizione DSL.

Questo esempio crea una forma nella posizione del mouse, quando l'utente fa doppio clic sul diagramma. Nella definizione DSL per questo esempio è stata `FillColor` esposta `ExampleShape` la proprietà di .

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}
```

 Se si specificano più forme, impostarne le posizioni relative usando `AbsoluteBounds` .

 È anche possibile impostare il colore e altre proprietà esposte dei connettori usando questo metodo.

### <a name="use-transactions"></a>Usare le transazioni
 Forme, connettori e diagrammi sono sottotipi di <xref:Microsoft.VisualStudio.Modeling.ModelElement> e sono presenti nello Store. È pertanto necessario apportare modifiche solo all'interno di una transazione. Per altre informazioni, [vedere Procedura: Usare transazioni per aggiornare il modello.](../modeling/how-to-use-transactions-to-update-the-model.md)

## <a name="document-view-and-document-data"></a><a name="docdata"></a> Visualizzazione documento e dati del documento
 ![Diagramma classi di tipi di diagramma standard](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Archiviare partizioni
 Quando viene caricato un modello, il diagramma di accompagnamento viene caricato contemporaneamente. In genere, il modello viene caricato in Store.DefaultPartition e il contenuto del diagramma viene caricato in un'altra partizione. In genere, il contenuto di ogni partizione viene caricato e salvato in un file separato.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)
- [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)
- [Procedura: utilizzare le transazioni per aggiornare il modello](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)
