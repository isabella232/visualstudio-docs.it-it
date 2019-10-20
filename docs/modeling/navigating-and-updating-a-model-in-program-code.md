---
title: Esplorazione e aggiornamento di un modello nel codice del programma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7273019d837a9cc13f6ffb306946372f11ec1f7f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658354"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Esplorare e aggiornare i modelli nel codice del programma

È possibile scrivere codice per creare ed eliminare elementi del modello, impostarne le proprietà e creare ed eliminare collegamenti tra gli elementi. Tutte le modifiche devono essere apportate all'interno di una transazione. Se gli elementi vengono visualizzati in un diagramma, il diagramma verrà "risolto" automaticamente alla fine della transazione.

## <a name="example"></a>Una definizione DSL di esempio
 Si tratta della parte principale di DslDefinition. DSL per gli esempi in questo argomento:

 ![Modello di albero &#45; genealogico del diagramma di definizione DSL](../modeling/media/familyt_person.png)

 Questo modello è un'istanza di questo linguaggio DSL:

 ![Modello dell'albero della famiglia Tudor](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Riferimenti e spazi dei nomi
 Per eseguire il codice in questo argomento, è necessario fare riferimento a:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Il codice userà questo spazio dei nomi:

 `using Microsoft.VisualStudio.Modeling;`

 Inoltre, se si scrive il codice in un progetto diverso da quello in cui è definito il linguaggio DSL, è necessario importare l'assembly compilato dal progetto DSL.

## <a name="navigation"></a>Esplorazione del modello

### <a name="properties"></a>Proprietà
 Le proprietà del dominio definite nella definizione DSL diventano proprietà a cui è possibile accedere nel codice del programma:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Se si desidera impostare una proprietà, è necessario eseguire questa operazione all'interno di una [transazione](#transaction):

 `henry.Name = "Henry VIII";`

 Se nella definizione DSL viene **calcolato**il **tipo** di una proprietà, non è possibile impostarlo. Per altre informazioni, vedere [proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Relazioni
 Le relazioni di dominio definite nella definizione DSL diventano coppie di proprietà, una per la classe in ogni entità finale della relazione. I nomi delle proprietà vengono visualizzati nel diagramma di DslDefinition come etichette nei ruoli a ogni lato della relazione. A seconda della molteplicità del ruolo, il tipo della proprietà è la classe nell'altra entità finale della relazione o una raccolta di tale classe.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Le proprietà alle estremità opposte di una relazione sono sempre reciproche. Quando un collegamento viene creato o eliminato, vengono aggiornate le proprietà del ruolo in entrambi gli elementi. L'espressione seguente, che usa le estensioni di `System.Linq`, è sempre true per la relazione ParentsHaveChildren nell'esempio:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Una relazione è anche rappresentata da un elemento del modello denominato *collegamento*, che è un'istanza del tipo di relazione di dominio. Un collegamento dispone sempre di un elemento di origine e di un elemento di destinazione. L'elemento di origine e l'elemento di destinazione possono essere uguali.

 È possibile accedere a un collegamento e alle relative proprietà:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Per impostazione predefinita, non è consentito più di un'istanza di una relazione per collegare qualsiasi coppia di elementi del modello. Tuttavia, se nella definizione DSL, il flag `Allow Duplicates` è true per la relazione, potrebbe essere presente più di un collegamento ed è necessario usare `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Sono disponibili anche altri metodi per accedere ai collegamenti. Esempio:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Ruoli nascosti.** Se nella definizione DSL, **is generate Property** è **false** per un ruolo specifico, non viene generata alcuna proprietà corrispondente a tale ruolo. Tuttavia, è comunque possibile accedere ai collegamenti e attraversare i collegamenti usando i metodi della relazione:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 L'esempio usato più di frequente è la relazione <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>, che collega un elemento del modello alla forma che la Visualizza in un diagramma:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Directory degli elementi
 È possibile accedere a tutti gli elementi nell'archivio usando la directory degli elementi:

 `store.ElementDirectory.AllElements`

 Sono disponibili anche metodi per la ricerca di elementi, come i seguenti:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="metadata"></a>Accesso alle informazioni sulle classi
 È possibile ottenere informazioni sulle classi, le relazioni e altri aspetti della definizione DSL. Esempio:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Di seguito sono riportate le classi predecessori degli elementi del modello:

- ModelElement-tutti gli elementi e le relazioni sono ModelElements

- ElementLink-tutte le relazioni sono ElementLinks

## <a name="transaction"></a>Eseguire modifiche all'interno di una transazione
 Ogni volta che il codice del programma modifica qualsiasi elemento nell'archivio, è necessario eseguire questa operazione all'interno di una transazione. Questo vale per tutti gli elementi del modello, le relazioni, le forme, i diagrammi e le relative proprietà. Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Il metodo più pratico per gestire una transazione è costituito da un'istruzione `using` racchiusa in un'istruzione `try...catch`:

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

 Per rendere permanenti le modifiche, è necessario `Commit` la transazione prima che venga eliminata. Se si verifica un'eccezione non rilevata all'interno della transazione, l'archivio verrà reimpostato sullo stato prima delle modifiche.

## <a name="elements"></a>Creazione di elementi del modello
 In questo esempio viene aggiunto un elemento a un modello esistente:

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

- Creare il nuovo elemento in una partizione specifica dell'archivio. Per gli elementi e le relazioni del modello, ma non le forme, si tratta in genere della partizione predefinita.

- Impostarla come destinazione di una relazione di incorporamento. In DslDefinition di questo esempio, ogni persona deve essere la destinazione della relazione di incorporamento FamilyTreeHasPeople. A tale scopo, è possibile impostare la proprietà del ruolo FamilyTreeModel dell'oggetto Person o aggiungere la persona alla proprietà Role di people dell'oggetto FamilyTreeModel.

- Impostare le proprietà di un nuovo elemento, in particolare la proprietà per la quale `IsName` è true in DslDefinition. Questo flag contrassegna la proprietà che serve per identificare l'elemento in modo univoco all'interno del relativo proprietario. In questo caso, la proprietà Name ha tale flag.

- La definizione DSL di questo DSL deve essere stata caricata nell'archivio. Se si scrive un'estensione, ad esempio un comando di menu, questo sarà in genere già true. In altri casi, è possibile caricare in modo esplicito il modello nell'archivio oppure utilizzare [ModelBus](/previous-versions/ee904639(v=vs.140)) per caricarlo. Per altre informazioni, vedere [procedura: aprire un modello da file nel codice del programma](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Quando si crea un elemento in questo modo, viene creata automaticamente una forma, se il linguaggio DSL dispone di un diagramma. Viene visualizzato in una posizione assegnata automaticamente, con la forma predefinita, il colore e altre funzionalità. Se si desidera controllare dove e come viene visualizzata la forma associata, vedere [creazione di un elemento e della relativa forma](#merge).

## <a name="links"></a>Creazione di collegamenti alle relazioni
 Nella definizione DSL di esempio sono definite due relazioni. Ogni relazione definisce una *Proprietà Role* per la classe in ogni entità finale della relazione.

 È possibile creare un'istanza di una relazione in tre modi. Ognuno di questi tre metodi ha lo stesso effetto:

- Impostare la proprietà dell'assegnatario del ruolo di origine. Esempio:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Impostare la proprietà dell'assegnatario del ruolo di destinazione. Esempio:

  - `edward.familyTreeModel = familyTree;`

       La molteplicità di questo ruolo è `1..1`, quindi viene assegnato il valore.

  - `henry.Children.Add(edward);`

       La molteplicità di questo ruolo è `0..*`, quindi si aggiunge alla raccolta.

- Costruire un'istanza della relazione in modo esplicito. Esempio:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  L'ultimo metodo è utile se si desidera impostare le proprietà nella relazione stessa.

  Quando si crea un elemento in questo modo, viene creato automaticamente un connettore sul diagramma, ma con una forma, un colore e altre funzionalità predefinite. Per controllare la modalità di creazione del connettore associato, vedere [creazione di un elemento e della relativa forma](#merge).

## <a name="deleteelements"></a>Eliminazione di elementi

Eliminare un elemento chiamando `Delete()`:

`henry.Delete();`

Questa operazione eliminerà anche:

- Relazione collega a e dall'elemento. Ad esempio, `edward.Parents` non conterrà più `henry`.

- Elementi nei ruoli per i quali il flag di `PropagatesDelete` è true. Ad esempio, la forma che Visualizza l'elemento verrà eliminata.

Per impostazione predefinita, ogni relazione di incorporamento ha `PropagatesDelete` true nel ruolo di destinazione. L'eliminazione di `henry` non comporta l'eliminazione del `familyTree`, ma `familyTree.Delete()` eliminerà tutti i `Persons`.

Per impostazione predefinita, `PropagatesDelete` non è true per i ruoli delle relazioni di riferimento.

È possibile fare in modo che le regole di eliminazione ometteranno propagazioni specifiche quando si elimina un oggetto. Questa operazione è utile se si sostituisce un elemento per un altro. Fornire il GUID di uno o più ruoli per i quali non è necessario propagare l'eliminazione. Il GUID può essere ottenuto dalla classe di relazione:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(Questo particolare esempio non avrà alcun effetto, perché `PropagatesDelete` viene `false` per i ruoli della relazione `ParentsHaveChildren`).

In alcuni casi, l'eliminazione viene impedita dall'esistenza di un blocco, sull'elemento o su un elemento che verrebbe eliminato dalla propagazione. È possibile utilizzare `element.CanDelete()` per verificare se l'elemento può essere eliminato.

## <a name="deletelinks"></a>Eliminazione di collegamenti alla relazione
 Per eliminare un collegamento alla relazione, è possibile rimuovere un elemento da una proprietà Role:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 È anche possibile eliminare il collegamento in modo esplicito:

 `edwardHenryLink.Delete();`

 Questi tre metodi hanno tutti lo stesso effetto. È sufficiente utilizzarne solo uno.

 Se il ruolo ha una molteplicità 0.. 1 o 1.. 1, è possibile impostarlo su `null` o su un altro valore:

 `edward.FamilyTreeModel = null;`//o:

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="reorder"></a>Riordinamento dei collegamenti di una relazione
 I collegamenti di una determinata relazione originata o destinata a un determinato elemento del modello hanno una sequenza specifica. Vengono visualizzati nell'ordine in cui sono stati aggiunti. Questa istruzione, ad esempio, restituirà sempre gli elementi figlio nello stesso ordine:

 `foreach (Person child in henry.Children) ...`

 È possibile modificare l'ordine dei collegamenti:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a>Serrature
 Le modifiche potrebbero essere impedite da un blocco. I blocchi possono essere impostati sui singoli elementi, sulle partizioni e sull'archivio. Se uno di questi livelli ha un blocco che impedisce il tipo di modifica che si desidera apportare, è possibile che venga generata un'eccezione quando si tenta di eseguire questa operazione. È possibile individuare se i blocchi vengono impostati tramite l'elemento. GetLocks (), che è un metodo di estensione definito nello spazio dei nomi <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Per ulteriori informazioni, vedere [definizione di un criterio di blocco per creare segmenti di sola lettura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy"></a>Copia e incolla
 È possibile copiare elementi o gruppi di elementi in un <xref:System.Windows.Forms.IDataObject>:

```csharp
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Gli elementi vengono archiviati come gruppo di elementi serializzati.

 È possibile unire elementi da un IDataObject in un modello:

```csharp
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` possibile accettare un `PresentationElement` o un `ModelElement`. Se si assegna una `PresentationElement`, è anche possibile specificare una posizione nel diagramma di destinazione come terzo parametro.

## <a name="diagrams"></a>Esplorazione e aggiornamento di diagrammi
 In un linguaggio DSL, l'elemento del modello di dominio, che rappresenta un concetto come Person o Song, è separato dall'elemento Shape, che rappresenta quello visualizzato nel diagramma. L'elemento del modello di dominio archivia le proprietà e le relazioni importanti dei concetti. L'elemento Shape archivia le dimensioni, la posizione e il colore della visualizzazione dell'oggetto nel diagramma e il layout delle parti componente.

### <a name="presentation-elements"></a>Elementi di presentazione
 ![Diagramma classi di tipi di forma di base e di elemento](../modeling/media/dslshapesandelements.png)

 Nella definizione DSL ogni elemento specificato Crea una classe derivata da una delle classi standard seguenti.

|Tipo di elemento|Classe base|
|-|-|
|Classe di dominio|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Relazione di dominio|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Forma|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Connettore|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagramma|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Un elemento in un diagramma rappresenta in genere un elemento del modello. In genere (ma non sempre), una <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> rappresenta un'istanza della classe di dominio e una <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> rappresenta un'istanza della relazione di dominio. La relazione <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> collega un nodo o una forma collegamento all'elemento del modello che rappresenta.

 Ogni nodo o forma di collegamento appartiene a un diagramma. Una forma collegamento binario connette due forme nodo.

 Le forme possono avere forme figlio in due set. Una forma nel set di `NestedChildShapes` è confinata al rettangolo di delimitazione del padre. Una forma nell'elenco di `RelativeChildShapes` può apparire all'esterno o in parte all'esterno dei limiti dell'elemento padre, ad esempio un'etichetta o una porta. Un diagramma non contiene `RelativeChildShapes` e nessun `Parent`.

### <a name="views"></a>Spostamento tra forme ed elementi
 Gli elementi del modello di dominio e gli elementi Shape sono correlati dalla relazione di <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 La stessa relazione collega le relazioni con i connettori nel diagramma:

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

### <a name="navigating-around-the-diagram"></a>Spostamento intorno al diagramma
 In generale, non è consigliabile spostarsi tra le forme e i connettori nel diagramma. È preferibile spostarsi tra le relazioni nel modello, spostandosi tra le forme e i connettori solo quando è necessario lavorare sull'aspetto del diagramma. Questi metodi collegano i connettori alle forme a ogni estremità:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Molte forme sono composti. sono costituiti da una forma padre e da uno o più livelli di elementi figlio. Le forme posizionate in relazione a un'altra forma sono dette *elementi figlio*. Quando la forma padre viene spostata, gli elementi figlio lo spostano.

 Gli *elementi figlio relativi* possono apparire all'esterno del rettangolo di delimitazione della forma padre. Gli elementi figlio *annidati* vengono visualizzati rigorosamente all'interno dei limiti dell'elemento padre.

 Per ottenere il set superiore di forme in un diagramma, usare:

 `Diagram.NestedChildShapes`

 Le classi predecessori delle forme e dei connettori sono:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

### <a name="shapeProperties"></a>Proprietà delle forme e dei connettori
 Nella maggior parte dei casi, non è necessario apportare modifiche esplicite alle forme. Dopo aver modificato gli elementi del modello, le regole "Correggi" aggiornano le forme e i connettori. Per ulteriori informazioni, vedere [risposta a e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

 Tuttavia, è utile apportare alcune modifiche esplicite alle forme nelle proprietà indipendenti dagli elementi del modello. Ad esempio, è possibile modificare queste proprietà:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>: determina l'altezza e la larghezza della forma.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-position rispetto alla forma o al diagramma padre

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>: set di penne e pennelli utilizzati per disegnare la forma o il connettore

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>: rende invisibile la forma

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>: rende visibile la forma dopo una `Hide()`

### <a name="merge"></a>Creazione di un elemento e della relativa forma

Quando si crea un elemento e lo si collega all'albero delle relazioni di incorporamento, viene automaticamente creata e associata una forma. Questa operazione viene eseguita dalle regole di correzione eseguite alla fine della transazione. Tuttavia, la forma verrà visualizzata in una posizione assegnata automaticamente e la relativa forma, il colore e altre funzionalità includeranno valori predefiniti. Per controllare la modalità di creazione della forma, è possibile utilizzare la funzione Merge. È innanzitutto necessario aggiungere gli elementi che si desidera aggiungere in un ElementGroup, quindi unire il gruppo nel diagramma.

Questo metodo:

- Imposta il nome, se è stata assegnata una proprietà come nome dell'elemento.

- Osserva qualsiasi direttiva di Unione degli elementi specificata nella definizione DSL.

In questo esempio viene creata una forma sulla posizione del mouse quando l'utente fa doppio clic sul diagramma. Nella definizione DSL per questo esempio è stata esposta la proprietà `FillColor` di `ExampleShape`.

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

 Se si specifica più di una forma, impostarne le posizioni relative usando il `AbsoluteBounds`.

 È anche possibile impostare il colore e altre proprietà esposte dei connettori usando questo metodo.

### <a name="use-transactions"></a>USA transazioni
 Forme, connettori e diagrammi sono sottotipi di <xref:Microsoft.VisualStudio.Modeling.ModelElement> e Live nell'archivio. È pertanto necessario apportare modifiche a tali elementi solo all'interno di una transazione. Per altre informazioni, vedere [procedura: usare le transazioni per aggiornare il modello](../modeling/how-to-use-transactions-to-update-the-model.md).

## <a name="docdata"></a>Visualizzazione documento e dati documento
 ![Diagramma classi di tipi di diagramma standard](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Archivia partizioni
 Quando viene caricato un modello, il diagramma associato viene caricato nello stesso momento. In genere, il modello viene caricato in Store. DefaultPartition e il contenuto del diagramma viene caricato in un'altra partizione. In genere, il contenuto di ogni partizione viene caricato e salvato in un file separato.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)
- [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)
- [Procedura: Usare le transazioni per aggiornare il modello](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)
