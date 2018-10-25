---
title: Esplorazione e aggiornamento di un modello nel codice del programma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 930d7ededf4a54aaf75516c59001eaccf38c210c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896768"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Esplorare e aggiornare i modelli nel codice del programma

È possibile scrivere codice per creare ed eliminare gli elementi del modello, impostare le relative proprietà e creare ed eliminare collegamenti tra elementi. Tutte le modifiche dovute all'interno di una transazione. Se gli elementi vengono visualizzati in un diagramma, il diagramma verrà "risolto" automaticamente alla fine della transazione.

##  <a name="example"></a> Una definizione DSL dell'esempio
 Questa è la parte principale di Dsldefinition per gli esempi in questo argomento:

 ![Diagramma di definizione DSL &#45; modello di albero genealogico](../modeling/media/familyt_person.png)

 Questo modello è un'istanza di questo DSL:

 ![Modello dell'albero della famiglia Tudor](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>I riferimenti e spazi dei nomi
 Per eseguire il codice in questo argomento, è necessario fare riferimento:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Questo spazio dei nomi verrà usato dal codice:

 `using Microsoft.VisualStudio.Modeling;`

 Inoltre, se si sta scrivendo il codice in un progetto diverso da quello in cui è definito il linguaggio DSL, è necessario importare l'assembly compilato dal progetto Dsl.

##  <a name="navigation"></a> Passare il modello

### <a name="properties"></a>Proprietà
 Proprietà di dominio definite nella definizione DSL diventano le proprietà che è possibile accedere nel codice del programma:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Se si desidera impostare una proprietà, è necessario farlo in un [transazione](#transaction):

 `henry.Name = "Henry VIII";`

 Se nella definizione DSL, una proprietà **genere** viene **Calculated**, non è possibile impostare. Per altre informazioni, vedere [calcolate e le proprietà di archiviazione personalizzate](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Relazioni
 Relazioni di dominio definite nella definizione DSL più coppie di proprietà, uno della classe a ogni estremità della relazione. I nomi delle proprietà vengono visualizzate nel diagramma DslDefinition come etichette in ruoli su ogni lato della relazione. A seconda della molteplicità del ruolo, il tipo della proprietà è la classe a altra estremità della relazione o una raccolta di tale classe.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Le proprietà angoli opposti di una relazione sono sempre reciproco. Quando un collegamento viene creato o eliminato, vengono aggiornate le proprietà del ruolo in entrambi gli elementi. L'espressione seguente (che usa le estensioni di `System.Linq`) è sempre true per la relazione ParentsHaveChildren nell'esempio:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Una relazione è anche rappresentata da un elemento del modello chiamato un' *collegamento*, che è un'istanza del tipo di relazione di dominio. Un collegamento ha sempre l'elemento di una sola origine e una destinazione. L'elemento di origine e l'elemento di destinazione può essere lo stesso.

 È possibile accedere a un collegamento e le relative proprietà:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Per impostazione predefinita, non più di un'istanza di una relazione è consentita collegare qualsiasi coppia di elementi del modello. Ma se nella definizione DSL, il `Allow Duplicates` flag è true per la relazione, quindi potrebbero esserci più di un collegamento, è necessario usare `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Esistono anche altri metodi per l'accesso ai collegamenti. Ad esempio:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Ruoli nascosti.** Se nella definizione DSL **proprietà generato** viene **false** per un ruolo specifico, nessuna proprietà viene quindi generata corrispondente a tale ruolo. Tuttavia, è ancora possibile accedere ai collegamenti e attraversa i collegamenti usando i metodi della relazione:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 L'esempio di uso più frequente è la <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relazione che collega un elemento del modello per la forma che li visualizza in un diagramma:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>La Directory dell'elemento
 È possibile accedere a tutti gli elementi nell'archivio di utilizzando la directory dell'elemento:

 `store.ElementDirectory.AllElements`

 Sono disponibili anche metodi per la ricerca di elementi, ad esempio il seguente:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

##  <a name="metadata"></a> L'accesso a informazioni sulle classi
 È possibile ottenere informazioni sulle classi di relazioni e altri aspetti della definizione DSL. Ad esempio:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Le classi predecessore di elementi del modello sono i seguenti:

-   ModelElement - tutti gli elementi e relazioni sono ModelElements

-   ElementLink - tutte le relazioni sono ElementLinks

##  <a name="transaction"></a> Eseguire le modifiche all'interno di una transazione
 Ogni volta che il codice del programma modifica ad alcun elemento di Store, è necessario farlo in una transazione. Questo vale per tutti gli elementi del modello, relazioni, forme, diagrammi e le relative proprietà. Per altre informazioni, vedere <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Il metodo più pratico di gestione di una transazione è con un `using` istruzione racchiusa tra una `try...catch` istruzione:

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

 È possibile apportare qualsiasi numero di modifiche all'interno di una transazione. È possibile aprire nuove transazioni all'interno di una transazione attiva.

 Per rendere permanenti le modifiche, è consigliabile `Commit` la transazione prima di eliminarlo. Se si verifica un'eccezione non rilevata all'interno della transazione, la Store verrà reimpostato sullo stato precedente le modifiche.

##  <a name="elements"></a> Creazione di elementi del modello
 Questo esempio viene aggiunto un elemento a un modello esistente:

```
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

 In questo esempio vengono illustrati questi punti essenziali sulla creazione di un elemento:

- Creare il nuovo elemento in una partizione specifica del Store. Per gli elementi del modello e le relazioni, ma non le forme, si tratta in genere la partizione predefinita.

- Rendere la destinazione di una relazione di incorporamento. In DslDefinition di questo esempio, ogni persona deve essere la destinazione della relazione FamilyTreeHasPeople di incorporamento. A tale scopo, è possibile impostare la proprietà di ruolo FamilyTreeModel dell'oggetto persona o aggiunge la persona che alla proprietà del ruolo utenti dell'oggetto FamilyTreeModel.

- Impostare le proprietà di un nuovo elemento, in particolare la proprietà per il quale `IsName` è impostata su true nel DslDefinition. Questo flag contrassegna la proprietà che consentono di identificare l'elemento in modo univoco all'interno di relativo proprietario. In questo caso, la proprietà del nome con flag.

- La definizione DSL di questo DSL debba sono stata caricata nel Store. Se si sta scrivendo un'estensione, ad esempio un comando di menu, in genere sarà già presente. In altri casi, è possibile in modo esplicito, caricare il modello di Store o usare <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> per caricarlo. Per altre informazioni, vedere [procedura: aprire un modello da File nel codice programma](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Quando si crea un elemento in questo modo, viene creata automaticamente una forma (se il DSL ha un diagramma). Viene visualizzato in una posizione assegnata automaticamente, con forma predefinita, colori e altre funzionalità. Se si desidera controllare dove e come viene visualizzata la forma associata, vedere [creazione di un elemento e la relativa forma](#merge).

##  <a name="links"></a> Creazione di collegamenti di relazione
 Sono presenti due relazioni definite nell'esempio di definizione DSL. Ogni relazione definisce un *proprietà del ruolo* sulla classe a ogni estremità della relazione.

 Esistono tre modi in cui è possibile creare un'istanza di una relazione. Ognuno di questi tre metodi ha lo stesso effetto:

- Impostare la proprietà dell'assegnatario del ruolo di origine. Ad esempio:

  -   `familyTree.People.Add(edward);`

  -   `edward.Parents.Add(henry);`

- Impostare la proprietà dell'assegnatario del ruolo di destinazione. Ad esempio:

  -   `edward.familyTreeModel = familyTree;`

       La molteplicità di questo ruolo è `1..1`, pertanto viene assegnato il valore.

  -   `henry.Children.Add(edward);`

       La molteplicità di questo ruolo è `0..*`, pertanto è aggiungere alla raccolta.

- Costruire un'istanza della relazione in modo esplicito. Ad esempio:

  -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Quest'ultimo metodo è utile se si desidera impostare proprietà per la relazione stessa.

  Quando si crea un elemento in questo modo, viene creato automaticamente un connettore nel diagramma, ma dispone di una forma predefinite, colori e altre funzionalità. Per controllare come viene creato il connettore associato, vedere [creazione di un elemento e la relativa forma](#merge).

##  <a name="deleteelements"></a> L'eliminazione di elementi
 Eliminare un elemento chiamando `Delete()`:

 `henry.Delete();`

 Questa operazione eliminerà anche:

- Collegamenti di relazione da e verso l'elemento. Ad esempio, `edward.Parents` non conterrà più `henry`.

- Gli elementi in ruoli per il quale il `PropagatesDelete` flag è true. Ad esempio, la forma che visualizza l'elemento verrà eliminata.

  Per impostazione predefinita, ogni relazione di incorporamento è `PropagatesDelete` true al ruolo di destinazione. L'eliminazione `henry` non elimina il `familyTree`, ma `familyTree.Delete()` eliminerebbe tutti il `Persons`. Per altre informazioni, vedere [personalizzazione del comportamento di eliminazione](../modeling/customizing-deletion-behavior.md).

  Per impostazione predefinita, `PropagatesDelete` non vale per i ruoli delle relazioni di riferimento.

  È possibile che le regole di eliminazione omettere propagazioni degli specifici quando si elimina un oggetto. Ciò è utile se si intende sostituire un elemento per un altro. Fornire il GUID di uno o più ruoli per i quali l'eliminazione non deve essere propagata. È possibile ottenere il GUID della classe di relazione:

  `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

  (Questo particolare esempio avrebbe alcun effetto, poiché `PropagatesDelete` viene `false` per i ruoli del `ParentsHaveChildren` relazione.)

  In alcuni casi, l'eliminazione sia impedita dall'esistenza di un blocco, sull'elemento o su un elemento da eliminare dalla propagazione. È possibile usare `element.CanDelete()` per verificare se l'elemento può essere eliminato.

##  <a name="deletelinks"></a> L'eliminazione di collegamenti di relazione
 È possibile eliminare un relazione di collegamento tramite la rimozione di un elemento da una proprietà di ruolo:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 È anche possibile eliminare il collegamento, in modo esplicito:

 `edwardHenryLink.Delete();`

 Questi tre metodi tutti hanno lo stesso effetto. È sufficiente usare uno di essi.

 Se il ruolo ha molteplicità 1 0..1 o 1, è possibile impostarlo `null`, o a un altro valore:

 `edward.FamilyTreeModel = null;` oppure:

 `edward.FamilyTreeModel = anotherFamilyTree;`

##  <a name="reorder"></a> Riordinamento i collegamenti di una relazione
 I collegamenti di una particolare relazione originato o destinata a un elemento del modello specifico dispone di una sequenza specifica. Vengono visualizzati nell'ordine in cui sono stati aggiunti. Ad esempio, l'istruzione genererà sempre gli elementi figlio nello stesso ordine:

 `foreach (Person child in henry.Children) ...`

 È possibile modificare l'ordine dei collegamenti:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

##  <a name="locks"></a> Blocchi
 È possibile prevenire le modifiche apportate da un blocco. Su singoli elementi nelle partizioni e nell'archivio, è possono impostare i blocchi. Se uno di questi livelli include un blocco che impedisce il tipo di modifica che si desidera apportare, quando si tenta di, potrebbe essere generata un'eccezione. È possibile individuare se i blocchi vengono configurati mediante elemento. GetLocks(), ovvero un metodo di estensione che viene definito nello spazio dei nomi <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Per altre informazioni, vedere [che definisce un criterio di blocco per creare segmenti di sola lettura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

##  <a name="copy"></a> Copia e Incolla
 È possibile copiare gli elementi o i gruppi di elementi da un <xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Gli elementi vengono archiviati come un gruppo di elementi serializzati.

 È possibile unire gli elementi da un oggetto IDataObject in un modello:

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` grado di accettare uno una `PresentationElement` o un `ModelElement`. Se è necessario assegnargli un `PresentationElement`, è inoltre possibile specificare una posizione nel diagramma di destinazione come terzo parametro.

##  <a name="diagrams"></a> Esplorazione e aggiornamento di diagrammi
 In un linguaggio DSL, elemento del modello di dominio, che rappresenta un concetto, ad esempio una persona o un brano, è separato dall'elemento shape, che rappresenta ciò che è visualizzato nel diagramma. L'elemento del modello di dominio archivia le proprietà importanti e le relazioni dei concetti. L'elemento della forma archivia le dimensioni, posizione e colore della visualizzazione dell'oggetto del diagramma e il layout dei relativi componenti.

### <a name="presentation-elements"></a>Elementi di presentazione
 ![Diagramma classi di tipi di forma di base e di elemento](../modeling/media/dslshapesandelements.png)

 Nella definizione DSL, ogni elemento che specifica crea una classe derivata da una delle seguenti classi standard.

|Tipo di elemento|Classe base|
|-|-|
|Classe di dominio|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Relazione di dominio|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Forma|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Connettore|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagramma|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 In genere, un elemento in un diagramma rappresenta un elemento del modello. In genere (ma non sempre), un <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> rappresenta un'istanza della classe di dominio e un <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> rappresenta un'istanza di relazione di dominio. Il <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relazione collega una forma di nodo o un collegamento all'elemento del modello che rappresenta.

 Tutte le forme di nodo o collegamento appartiene a un diagramma. Una forma collegamento binario connette due forme di nodo.

 Le forme possono avere forme figlio in due set. Una forma nel `NestedChildShapes` set è limitato al delimitatore del padre. Una forma nel `RelativeChildShapes` elenco può apparire all'esterno o in parte oltre i limiti dell'elemento padre, ad esempio un'etichetta o una porta. Un diagramma non ha alcun `RelativeChildShapes` e nessun `Parent`.

###  <a name="views"></a> Lo spostamento tra elementi e forme
 Gli elementi del modello di dominio e gli elementi forma sono correlati tramite la <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relazione.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 La stessa relazione collega le relazioni per i connettori nel diagramma:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Questa relazione, la radice del modello contiene anche collegamenti al diagramma:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Per ottenere l'elemento del modello rappresentato da una forma, usare:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Spostarsi all'interno del diagramma
 Non è in genere consigliabile per spostarsi tra le forme e connettori nel diagramma. È preferibile esplorare le relazioni nel modello, lo spostamento tra le forme e connettori solo quando è necessario lavorare sull'aspetto del diagramma. Questi metodi collegano le forme a ogni estremità connettori:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Molte forme sono composti; essi sono costituiti da una forma padre e uno o più livelli di elementi figlio. Forme che sono posizionate in rispetto a altra forma vengono detti essere relativi *figli*. Quando si sposta alla forma padre, spostano gli elementi figlio con esso.

 *Gli elementi figlio relativi* può trovarsi all'esterno del riquadro delimitatore della forma padre. *Annidati* elementi figlio vengono visualizzati esclusivamente all'interno dei limiti dell'elemento padre.

 Per ottenere il set superiore delle forme in un diagramma, usare:

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

###  <a name="shapeProperties"></a> Proprietà delle forme e connettori
 Nella maggior parte dei casi, non è necessario apportare modifiche esplicite alle forme. Dopo aver modificato gli elementi del modello, le regole "correggo" aggiornano le forme e connettori. Per altre informazioni, vedere [procedura: rispondere a e la propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

 Tuttavia, è utile apportare alcune modifiche espliciti alle forme di proprietà che sono indipendenti tra gli elementi del modello. Ad esempio, è possibile modificare queste proprietà:

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -Determina l'altezza e la larghezza della forma.

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -posizione rispetto alla forma padre o del diagramma

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -il set di penne e pennelli utilizzati per disegnare la forma o connettore

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -rende invisibile la forma

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -rende visibile dopo la forma un `Hide()`

###  <a name="merge"></a> Creazione di un elemento e la relativa forma

Quando si crea un elemento e crea un collegamento nell'albero delle relazioni di incorporamento, una forma viene automaticamente creata e associata. Questa operazione viene eseguita dalle regole "della correzione" eseguite alla fine della transazione. Tuttavia, la forma verrà visualizzata in una posizione assegnata automaticamente e la relativa forma, colori e altre funzionalità saranno disponibili valori predefiniti. Per controllare come viene creata la forma, è possibile usare la funzione di tipo merge. È necessario innanzitutto aggiungere gli elementi da aggiungere in un oggetto ElementGroup e quindi unire il gruppo nel diagramma.

Questo metodo:

-   Imposta il nome, se è stata assegnata una proprietà come nome dell'elemento.

-   Osserva le direttive di unione specificata nella definizione DSL.

Questo esempio crea una forma in corrispondenza della posizione del mouse, quando l'utente fa doppio clic sul diagramma. Nella definizione DSL per questo esempio, il `FillColor` proprietà di `ExampleShape` è stato esposto.

```
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

 Se si specifica più di una forma, impostare la relativa posizione usando la `AbsoluteBounds`.

 È anche possibile impostare il colore e altre proprietà esposta dei connettori con questo metodo.

### <a name="use-transactions"></a>Utilizzare le transazioni
 Forme, connettori e i diagrammi sono sottotipi di <xref:Microsoft.VisualStudio.Modeling.ModelElement> e di Store in tempo reale. È pertanto necessario apportare modifiche a tali solo all'interno di una transazione. Per altre informazioni, vedere [procedura: usare transazioni per aggiornare il modello](../modeling/how-to-use-transactions-to-update-the-model.md).

##  <a name="docdata"></a> Visualizzazione del documento e i dati del documento
 ![Diagramma classi di tipi di diagramma standard](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Partizioni di Store
 Quando viene caricato un modello, il diagramma associato viene caricato nello stesso momento. In genere, il modello viene caricato in Store.DefaultPartition e il contenuto del diagramma viene caricato in un'altra partizione. In genere, il contenuto di ogni partizione viene caricato e salvato in un file separato.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)
- [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)
- [Procedura: Usare le transazioni per aggiornare il modello](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)
