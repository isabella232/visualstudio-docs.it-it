---
title: Visualizzare un modello UML nei diagrammi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b43d4353e325bb81a29fe39106ac13e1ddcf96a9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849478"
---
# <a name="display-a-uml-model-on-diagrams"></a>Visualizzare un modello UML nei diagrammi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nel codice programma per un'estensione a Visual Studio, è possibile controllare come vengono visualizzati gli elementi modello nei diagrammi. Per individuare le versioni di Visual Studio che supportano i modelli UML, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

In questo argomento:
- [Per visualizzare un elemento in un diagramma](#Display)

- [Accesso alle forme che rappresentano un elemento](#GetShapes)

- [Ridimensionamento e ridimensionamento delle forme](#Moving)

- [Per rimuovere una forma da un diagramma](#Removing)

- [Apertura e creazione di diagrammi](#Opening)

- [Esempio: comando per allineare le forme](#AlignCommand)

## <a name="Display"></a>Per visualizzare un elemento in un diagramma
 Quando si crea un elemento come un caso di utilizzo o un'azione, l'utente può visualizzarlo in Esplora modelli UML, ma non viene sempre automaticamente visualizzato in un diagramma. In alcuni casi è necessario scrivere codice per visualizzarlo. Nella tabella seguente sono riepilogate le alternative.

|Tipo di elemento|Esempio:|Per visualizzarlo, il codice deve|
|---------------------|-----------------|-------------------------------------|
|Classificatore|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Creare forme associate nei diagrammi specificati. È possibile creare un numero qualsiasi di forme per ogni classificatore.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Impostare `parentShape` su `null` per una forma di livello superiore del diagramma.<br /><br /> Per visualizzare una forma all'interno di un'altra:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);` **Nota:** se si esegue la visualizzazione all'interno di una transazione **ILinkedUndo** , il metodo a volte non restituisce alcun `IShape`. La forma viene tuttavia creata correttamente ed è accessibile mediante `IElement.Shapes().`|
|Elemento figlio del classificatore|Attributo, Operazione,<br /><br /> Parte, Porta|Automatico: non è richiesto alcun codice.<br /><br /> Viene visualizzato come parte dell'elemento padre.|
|Comportamento di|Interazione (sequenza)<br /><br /> Attività|Associare il comportamento a un diagramma appropriato.<br /><br /> Ogni comportamento può essere associato a più diagrammi alla volta.<br /><br /> Ad esempio:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|
|Elemento figlio del comportamento|Linee di vita, messaggi, azioni, nodi oggetto|Automatico: non è richiesto alcun codice.<br /><br /> Viene visualizzato se l'elemento padre è associato a un diagramma.|
|Relationship|Associazione, generalizzazione, flusso, dipendenza|Automatico: non è richiesto alcun codice.<br /><br /> Viene visualizzato in ogni diagramma in cui vengono visualizzate entrambe le estremità.|

## <a name="GetShapes"></a>Accesso alle forme che rappresentano un elemento
 La forma che rappresenta un elemento appartiene ai tipi:

 `IShape`

 `IShape<` *ElementType* `>`

 dove *elementType* è un tipo dell'elemento del modello, ad esempio `IClass` o `IUseCase`.

|||
|-|-|
|`anElement.Shapes ()`|Tutti gli `IShapes` che rappresentano questo elemento in diagrammi aperti.|
|`anElement.Shapes(aDiagram)`|Tutti gli `IShapes` che rappresentano questo elemento in particolare diagramma.|
|`anIShape.GetElement()`|`IElement` che rappresenta la forma. Normalmente si eseguirebbe il cast a una sottoclasse di IElement.|
|`anIShape.Diagram`|L'oggetto `IDiagram` che contiene il cursore.|
|`anIShape.ParentShape`|La forma che contiene `anIShape`. Ad esempio, una forma porta è contenuta all'interno di una forma componente.|
|`anIShape.ChildShapes`|Le forme contenute all'interno di un `IShape` o `IDiagram`.|
|`anIShape.GetChildShapes<IUseCase>()`|Le forme contenute all'interno di un `IShape` o `IDiagram` che rappresentano gli elementi del tipo specificato, ad esempio `IUseCase`.|
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Eseguire il cast di un `IShape` generico a un oggetto `IShape<IElement>` fortemente tipizzato.|
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Eseguire il cast di una forma dal tipo di una forma con parametri a un altro.|

## <a name="Moving"></a>Ridimensionamento e ridimensionamento delle forme

|||
|-|-|
|`anIShape.Move(x, y, [width], [height])`|Spostare o ridimensionare una forma.|
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Attivare la finestra e scorrere il diagramma in modo che tutte le forme specificate siano visibili. Le forme devono essere tutte nel diagramma. Se `zoomToFit` è true, il diagramma verrà ridimensionato se necessario in modo che tutte le forme siano visibili.|

 Per un esempio, vedere [definizione di un comando di allineamento](#AlignCommand).

## <a name="Removing"></a>Per rimuovere una forma da un diagramma
 È possibile eliminare forme di alcuni tipi di elemento senza eliminare l'elemento.

|Elemento modello|Per rimuovere la forma|
|-------------------|-------------------------|
|Un classificatore: classe, interfaccia, enumerazione, attore, caso di utilizzo o componente|`shape.Delete();`|
|Un comportamento: interazione o attività|È possibile eliminare il diagramma dal progetto. Usare `IDiagram.FileName` per ottenere il percorso.<br /><br /> Questa operazione non elimina il comportamento dal modello.|
|Qualsiasi altra forma|Non è possibile eliminare altre forme in modo esplicito da un diagramma. La forma scomparirà automaticamente se l'elemento viene eliminato dal modello o se la forma padre viene rimossa dal diagramma.|

## <a name="Opening"></a>Apertura e creazione di diagrammi

### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Per accedere al diagramma corrente dell'utente da un comando o un'estensione di movimento
 Dichiarare questa proprietà importata nella classe:

 `[Import]`

 `IDiagramContext Context { get; set; }`

 In un metodo accedere al diagramma:

 `IClassDiagram classDiagram =`

 `Context.CurrentDiagram as IClassDiagram;`

> [!NOTE]
> Un'istanza di `IDiagram` (e i relativi sottotipi, ad esempio `IClassDiagram`) è valido solo all'interno del comando che si sta elaborando. Non è consigliabile mantenere un oggetto `IDiagram` in una variabile persistente mentre il controllo viene restituito all'utente.

 Per altre informazioni, vedere [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

### <a name="to-obtain-a-list-of-open-diagrams"></a>Per ottenere un elenco di diagrammi aperti
 Un elenco dei diagrammi attualmente aperti nel progetto:

```
Context.CurrentDiagram.ModelStore.Diagrams()
```

## <a name="to-access-the-diagrams-in-a-project"></a>Per accedere ai diagrammi in un progetto
 L'API [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] può essere usata per aprire e creare diagrammi e progetti di modellazione.

 Si noti il cast da `EnvDTE.ProjectItem` a `IDiagramContext`.

```

      using EnvDTE; // Visual Studio API
...
[Import]
public IServiceProvider ServiceProvider { get; set; }
...
// Get Visual Studio API
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;
// Get current Visual Studio project
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
// Open and process every diagram in the project.
foreach (ProjectItem item in project.ProjectItems)
{
  // Cast ProjectItem to IDiagramContext
  IDiagramContext context = item as IDiagramContext;
  if (context == null)
  {
     // This is not a diagram file.
     continue;
  }
  // Open the file and give the window the focus.
  if (!item.IsOpen)
  {
      item.Open().Activate();
  }
  // Get the diagram.
  IDiagram diagram = context.CurrentDiagram;
  // Deal with specific diagram types.
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;
  if (seqDiagram != null)
  { ... } } }
```

 Le istanze di `IDiagram` e i relativi sottotipi non sono validi dopo la restituzione del controllo a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 È anche possibile ottenere l'archivio modelli da un progetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:

```

      Project project = ...;
IModelStore modelStore = (project as IModelingProject).Store;
```

## <a name="AlignCommand"></a>Esempio: comando per allineare le forme
 Il codice seguente implementa un comando di menu che allinea accuratamente le forme. L'utente deve inserire innanzitutto due o più forme con allineamento approssimativo, verticalmente o orizzontalmente. Il comando di allineamento può essere quindi usato per allineare i centri.

 Per rendere disponibile il comando, aggiungere questo codice a un progetto di comando di menu e quindi distribuire l'estensione risultante agli utenti. Per altre informazioni, vedere [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace AlignCommand
{
  // Implements a command to align shapes in a UML class diagram.
  // The user first selects shapes that are roughly aligned either vertically or horizontally.
  // This command will straighten them up.

  // Place this file in a menu command extension project.
  // See https://msdn.microsoft.com/library/ee329481.aspx

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension] // TODO: Add other diagram types if needed
  class CommandExtension : ICommandExtension
  {
    /// <summary>
    /// See https://msdn.microsoft.com/library/ee329481.aspx
    /// </summary>
    [Import]
    IDiagramContext context { get; set; }

    /// <summary>
    /// Transaction context.
    /// See https://msdn.microsoft.com/library/ee330926.aspx
    /// </summary>
    [Import]
    ILinkedUndoContext linkedUndo { get; set; }

    /// <summary>
    /// Called when the user selects the command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      Align(context.CurrentDiagram.SelectedShapes);
    }

    /// <summary>
    /// Called when the user right-clicks on the diagram.
    /// Determines whether the command is enabled.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;
      // Make it visible if there are shapes selected:
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);

      // Make it enabled if there are two or more shapes that are roughly in line:
      command.Enabled = currentSelection.Count() > 1
        && (HorizontalAlignCenter(currentSelection) > 0.0
        || VerticalAlignCenter(currentSelection) > 0.0);

    }

    /// <summary>
    /// Title of the menu command.
    /// </summary>
    public string Text
    {
      get { return "Align Shapes"; }
    }

    /// <summary>
    /// Find a horizontal line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)
    {
      double Y = -1.0;
      double top = 0.0, bottom = shapes.First().Bottom();
      foreach (IShape shape in shapes)
      {
        top = Math.Max(top, shape.Top());
        bottom = Math.Min(bottom, shape.Bottom());
      }
      if (bottom > top) Y = (bottom + top) / 2.0;
      return Y;
    }

    /// <summary>
    /// Find a vertical line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)
    {
      double X = -1.0;
      double left = 0.0, right = shapes.First().Right();
      foreach (IShape shape in shapes)
      {
        left = Math.Max(left, shape.Left());
        right = Math.Min(right, shape.Right());
      }
      if (right > left) X = (right + left) / 2.0;
      return X;
    }

    /// <summary>
    /// Line up those shapes that are roughly aligned.
    /// </summary>
    /// <param name="shapes"></param>
    private void Align(IEnumerable<IShape> shapes)
    {
      if (shapes.Count() > 1)
      {
        // The shapes must all overlap either horizontally or vertically.
        // Find a horizontal line that is covered by all the shapes:
        double Y = HorizontalAlignCenter(shapes);
        if (Y > 0.0) // Negative if they don't overlap.
        {
          // Adjust all the shape positions in one transaction:
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
          {
            foreach (IShape shape in shapes)
            {
              shape.AlignYCenter(Y);
            }
            t.Commit();
          }
        }
        else
        {
          // Find a vertical line that is covered by all the shapes:
          double X = VerticalAlignCenter(shapes);
          if (X > 0.0) // Negative if they don't overlap.
          {
            // Adjust all the shape positions in one transaction:
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
            {
              foreach (IShape shape in shapes)
              {
                shape.AlignXCenter(X);
              }
              t.Commit();
            }
          }
        }
      }
    }
  }

  /// <summary>
  /// Convenience extensions for IShape.
  /// </summary>
  public static class IShapeExtension
  {
    public static double Bottom(this IShape shape)
    {
      return shape.YPosition + shape.Height;
    }

    public static double Top(this IShape shape)
    {
      return shape.YPosition;
    }

    public static double Left(this IShape shape)
    {
      return shape.XPosition;
    }

    public static double Right(this IShape shape)
    {
      return shape.XPosition + shape.Width;
    }

    public static void AlignYCenter(this IShape shape, double Y)
    {
      shape.Move(shape.XPosition, Y - shape.YCenter());
    }

    public static void AlignXCenter(this IShape shape, double X)
    {
      shape.Move(X - shape.XCenter(), shape.YPosition);
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double YCenter(this IShape shape)
    {
        return shape.Height / 2.0;
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double XCenter(this IShape shape)
    {
        return shape.Width / 2.0;
    }
  }
}

```

## <a name="see-also"></a>Vedere anche
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md) [esplorare il modello UML](../modeling/navigate-the-uml-model.md) [esempio: allineare le forme in un esempio di comando di menu Diagramma](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) [: creazione di elementi, forme e stereotipi](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)
