---
title: Definire un gestore movimenti in un diagramma di modellazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf749d1073faf4cf22febafce716af36b47c6484
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299302"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Definire un gestore modelli in un diagramma di modellazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile definire i comandi eseguiti quando l'utente trascina o fa doppio clic sugli elementi in un diagramma UML. È possibile creare un pacchetto di queste estensioni in un progetto[VSIX](https://go.microsoft.com/fwlink/?LinkId=160780)(Visual Studio Integration Extension) e distribuirlo ad altri utenti di Visual Studio.

 Se esiste già un comportamento predefinito per il tipo di diagramma e il tipo di elemento che si vuole trascinare, potrebbe non essere possibile aggiungere o modificare questo comportamento.

## <a name="requirements"></a>Requisiti
 Vedere [Requisiti](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-gesture-handler"></a>Creazione di un gestore movimenti
 Per definire un gestore movimenti per una finestra di progettazione UML, è necessario creare una classe che definisca il comportamento del gestore movimenti e incorporare la classe in un'estensione VSIX (Visual Studio Integration Extension). L'estensione VSIX funge da contenitore che può installare il gestore. Esistono due metodi alternativi per definire un gestore movimenti:

- **Creare un gestore movimenti nella relativa estensione VSIX usando un modello di progetto.** Questo è il metodo più rapido. Usarlo se non si vuole combinare il gestore con altri tipi di estensione, ad esempio estensioni di convalida, elementi della Casella degli strumenti personalizzati o comandi di menu.

- **Creare un gestore movimenti e progetti VSIX separati.** Usare questo metodo per combinare diversi tipi di estensione nella stessa estensione VSIX. Ad esempio, se il gestore movimenti richiede che il modello osservi alcuni vincoli specifici, è possibile incorporarlo nella stessa estensione VSIX come metodo di convalida.

#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Per creare un gestore movimenti nella relativa estensione VSIX

1. Nella finestra di dialogo **Nuovo progetto** selezionare **Estensione movimento**in **Progetti di modellazione**.

2. Aprire il file **.cs** nel nuovo progetto e modificare la classe `GestureExtension` per implementare il gestore movimenti.

    Per altre informazioni, vedere [Implementazione del gestore movimenti](#Implementing).

3. Testare il gestore movimenti premendo F5. Per altre informazioni, vedere [Esecuzione del gestore movimenti](#Executing).

4. Installare il gestore movimenti in un altro computer copiando il file **bin\\\*\\\*. vsix** compilato dal progetto. Per altre informazioni, vedere [Installazione e disinstallazione di un'estensione](#Installing).

   Ecco la procedura alternativa:

#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Per creare un progetto di libreria di classi (DLL) separato per il gestore movimenti

1. Creare un progetto Libreria di classi in una nuova soluzione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o in una soluzione esistente.

   1. Dal menu **File** scegliere **Nuovo**, **Progetto**.

   2. In **Modelli installati**espandere **Visual C#** o **Visual Basic**e quindi scegliere **Libreria di classi**nella colonna centrale.

2. Aggiungere i riferimenti seguenti al progetto.

    `Microsoft.VisualStudio.Modeling.Sdk.[version]`

    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`

    `Microsoft.VisualStudio.Uml.Interfaces`

    `System.ComponentModel.Composition`

    `System.Windows.Forms`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer`: è necessario solo se si intende estendere i diagrammi livello. Per altre informazioni, vedere [estendere i diagrammi livello](../modeling/extend-layer-diagrams.md).

3. Aggiungere un file di classe al progetto e impostarne il contenuto sul codice seguente.

   > [!NOTE]
   > Modificare lo spazio dei nomi e il nome della classe nel modo desiderato.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Modeling.Diagrams;
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Modeling;
   using Microsoft.VisualStudio.Uml.Classes;
   // ADD other UML namespaces if required

   namespace MyGestureHandler // CHANGE
   {
     // DELETE any of these attributes if the handler
     // should not work with some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // Gesture handlers must export IGestureExtension:
     [Export(typeof(IGestureExtension))]
     // CHANGE class name
     public class MyGesture1 : IGestureExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       /// <summary>
       /// Called when the user double-clicks on the diagram
       /// </summary>
       /// <param name="targetElement"></param>
       /// <param name="diagramPointEventArgs"></param>
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target shape, if any. Null if the target is the diagram.
         IShape targetIShape = targetElement.CreateIShape();

         // Do something...
       }

       /// <summary>
       /// Called repeatedly when the user drags from anywhere on the screen.
       /// Return value should indicate whether a drop here is allowed.
       /// </summary>
       /// <param name="targetMergeElement">References the element to be dropped on.</param>
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>
       /// <returns></returns>
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target element, if any. Null if the target is the diagram.
         IShape targetIShape = targetMergeElement.CreateIShape();

         // This example allows drag of any UML elements.
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;
       }

       /// <summary>
       /// Execute the action to be performed on the drop.
       /// </summary>
       /// <param name="targetDropElement"></param>
       /// <param name="diagramDragEventArgs"></param>
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.
       }

       /// <summary>
       /// Retrieves UML IElements from drag arguments.
       /// Works for drags from UML diagrams.
       /// </summary>
       private IEnumerable<IElement> GetModelElementsFromDragEvent
               (DiagramDragEventArgs dragEvent)
       {
         //ElementGroupPrototype is the container for
         //dragged and copied elements and toolbox items.
         ElementGroupPrototype prototype =
            dragEvent.Data.
            GetData(typeof(ElementGroupPrototype))
                 as ElementGroupPrototype;
         // Locate the originals in the implementation store.
         IElementDirectory implementationDirectory =
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

         return prototype.ProtoElements.Select(
           prototypeElement =>
           {
             ModelElement element = implementationDirectory
               .FindElement(prototypeElement.ElementId);
             ShapeElement shapeElement = element as ShapeElement;
             if (shapeElement != null)
             {
               // Dragged from a diagram.
               return shapeElement.ModelElement as IElement;
             }
             else
             {
               // Dragged from UML Model Explorer.
               return element as IElement;
             }
           });
       }

     }
   }

   ```

    Per altre informazioni su cosa inserire nei metodi, vedere [Implementazione del gestore movimenti](#Implementing).

   È necessario aggiungere il comando di menu a un progetto VSIX, che funge da contenitore per l'installazione del comando. Se si desidera, è possibile includere altri componenti nello stesso progetto VSIX.

#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Per aggiungere un gestore movimenti separato a un progetto VSIX

1. Questa procedura non è necessaria se il gestore movimenti è stato creato con la relativa estensione VSIX.

2. Creare un progetto VSIX, a meno che la soluzione non ne contenga già uno.

    1. In **Esplora soluzioni**scegliere **Aggiungi**dal menu di scelta rapida della soluzione e quindi fare clic su **Nuovo progetto**.

    2. In **Modelli installati**espandere **Visual C#** o **Visual Basic**, quindi selezionare **Extensibility**. Nella colonna centrale scegliere **Progetto VSIX**.

3. Impostare il progetto VSIX come progetto di avvio della soluzione.

    - In Esplora soluzioni scegliere **Imposta come progetto di avvio**dal menu di scelta rapida del progetto VSIX.

4. In **source.extension.vsixmanifest**aggiungere il progetto della libreria di classi del gestore movimenti come componente MEF:

    1. Nella scheda **Metadati** impostare un nome per il progetto VSIX.

    2. Nella scheda **Destinazioni di installazione** impostare le versioni di Visual Studio come destinazioni.

    3. Nella scheda **Asset** scegliere **Nuovo**e nella finestra di dialogo impostare le opzioni seguenti:

         **Tipo** = **Componente MEF**

         **Origine** = **Progetto nella soluzione corrente**

         **Progetto** = *Progetto di libreria di classi*

## <a name="Executing"></a>Esecuzione del gestore movimenti
 Per scopi di test, eseguire il gestore movimenti in modalità debug.

#### <a name="to-test-the-gesture-handler"></a>Per testare il gestore movimenti

1. Premere **F5**o scegliere **Avvia debug** dal menu **Debug**.

    Viene avviata un'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

    **Risoluzione dei problemi**: se non viene avviata una nuova istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

   - Se si hanno più progetti, assicurarsi che il progetto VSIX sia impostato come progetto di avvio della soluzione.

   - In Esplora soluzioni scegliere Proprietà dal menu di scelta rapida del progetto di avvio o dell'unico progetto. Nell'editor delle proprietà del progetto scegliere la scheda **debug** . Assicurarsi che la stringa nel campo **Avvia programma esterno** sia il percorso completo di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], in genere:

        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]aprire o creare un progetto di modellazione e aprire o creare un diagramma di modellazione. Usare un diagramma appartenente a uno dei tipi elencati negli attributi della classe del gestore movimenti.

3. Fare doppio clic in un punto qualsiasi del diagramma. Dovrebbe essere chiamato il gestore di doppio clic.

4. Trascinare un elemento da Esplora modelli UML nel diagramma. Dovrebbe essere chiamato il gestore di trascinamento.

   **Risoluzione dei problemi**: se il gestore movimenti non funziona, assicurarsi che:

- Il progetto del gestore movimenti sia elencato come componente MEF nella scheda **Asset** in **source.extensions.manifest** nel progetto VSIX.

- I parametri di tutti gli attributi `Import` e `Export` siano validi.

- Il metodo `CanDragDrop` non restituisca `false`.

- Il tipo di diagramma modello in uso (classe UML, sequenza e così via) sia elencato come uno degli attributi della classe del gestore movimenti [ClassDesignerExtension], [SequenceDesignerExtension] e così via.

- Per questo tipo di elemento rilasciato e di destinazione non sia già stata definita alcuna funzionalità incorporata.

## <a name="Implementing"></a>Implementazione del gestore movimenti

### <a name="the-gesture-handler-methods"></a>Metodi del gestore movimenti
 La classe del gestore movimenti implementa ed esporta <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Ecco i metodi che è necessario definire:

|||
|-|-|
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Restituisce `true` per consentire il rilascio in questa destinazione dell'elemento di origine referenziato in `dragEvent` .<br /><br /> Questo metodo non dovrebbe modificare il modello e dovrebbe funzionare rapidamente, perché viene usato per determinare lo stato della freccia quando l'utente sposta il mouse.|
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Aggiorna il modello in base all'oggetto di origine referenziato in `dragEvent`e la destinazione.<br /><br /> Viene chiamato quando l'utente rilascia il mouse dopo il trascinamento.|
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` è la forma su cui l'utente ha fatto doppio clic.|

 È possibile scrivere gestori che accettano non solo UML ma anche un'ampia gamma di altri elementi, tra cui file, nodi in una visualizzazione classi .NET e così via. L'utente può trascinare uno qualsiasi di questi elementi in un diagramma UML, purché venga scritto un metodo `OnDragDrop` in grado di decodificare il formato deserializzato degli elementi. I metodi di decodifica variano da un tipo di elemento all'altro.

 I parametri di questi metodi sono i seguenti:

- `ShapeElement target` Forma o diagramma in cui l'utente ha trascinato un elemento.

    `ShapeElement` è una classe nell'implementazione sottostante gli strumenti di modellazione UML. Per ridurre il rischio di porre il modello UML e i diagrammi in uno stato non coerente, evitare di usare i metodi di questa classe direttamente. Eseguire invece il wrapping dell'elemento in un `IShape`e quindi usare i metodi descritti in [visualizzare un modello UML nei diagrammi](../modeling/display-a-uml-model-on-diagrams.md).

  - Per ottenere un oggetto `IShape`:

      ```
      IShape targetIShape = target.CreateIShape(target);
      ```

  - Per ottenere l'elemento del modello di destinazione per l'operazione di trascinamento o di doppio clic:

      ```
      IElement target = targetIShape.Element;
      ```

      È possibile eseguire il cast di questo elemento in un tipo di elemento più specifico.

  - Per ottenere l'archivio modelli UML che contiene il modello UML:

      ```
      IModelStore modelStore =
        targetIShape.Element.GetModelStore(); 
      ```

  - Per ottenere l'accesso all'host e al provider di servizi:

      ```
      target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE
      ```

- `DiagramDragEventArgs eventArgs` Questo parametro contiene il formato serializzato dell'oggetto di origine di un'operazione di trascinamento:

    ```
    System.Windows.Forms.IDataObject data = eventArgs.Data;
    ```

     È possibile trascinare elementi di molti tipi diversi in un diagramma, da parti diverse di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]o dal desktop di Windows. Tipi di elemento diversi vengono codificati diversamente in `IDataObject`. Per estrarre gli elementi da questo oggetto, fare riferimento alla documentazione per il tipo appropriato di oggetto.

     Se l'oggetto di origine è un elemento UML trascinato da Esplora modelli UML o da un altro diagramma UML, fare riferimento a [ottenere gli elementi del modello UML da IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

### <a name="writing-the-code-of-the-methods"></a>Scrittura del codice dei metodi
 Per altre informazioni sulla scrittura del codice per la lettura e l'aggiornamento del modello, vedere [Programming with the UML API](../modeling/programming-with-the-uml-api.md).

 Per informazioni sull'accesso alle informazioni del modello in un'operazione di trascinamento, vedere [ottenere elementi del modello UML da IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

 Se si tratta di un diagramma di sequenza, vedere anche [modificare i diagrammi di sequenza UML usando l'API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Oltre ai parametri dei metodi, è anche possibile dichiarare una proprietà importata nella classe che fornisca accesso al diagramma e al modello correnti.

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 La dichiarazione di `IDiagramContext` consente di scrivere nei metodi il codice per l'accesso al diagramma, alla selezione corrente e al modello:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

 Per altre informazioni, vedere [esplorare il modello UML](../modeling/navigate-the-uml-model.md).

## <a name="Installing"></a>Installazione e disinstallazione di un'estensione
 È possibile installare un'estensione di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sia nel proprio computer che in altri.

#### <a name="to-install-an-extension"></a>Per installare un'estensione

1. Nel computer trovare il file **.vsix** compilato dal progetto VSIX.

    1. In **Esplora soluzioni**scegliere **Apri cartella in Esplora risorse**dal menu di scelta rapida del progetto VSIX.

    2. Individuare il file **bin\\\*\\** _progettoutente_ **. vsix**

2. Copiare il file **.vsix** nel computer di destinazione in cui si vuole installare l'estensione. Può trattarsi del computer in uso o di un altro computer.

     Nel computer di destinazione deve essere installata una delle edizioni di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] specificate in **source.extension.vsixmanifest**.

3. Nel computer di destinazione aprire il file **.vsix** .

     **Visual Studio Extension Installer** si apre e installa l'estensione.

4. Avviare o riavviare [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Per disinstallare un'estensione

1. Nel menu **Strumenti** scegliere **Estensioni e aggiornamenti**.

2. Espandere **Estensioni installate**.

3. Selezionare l'estensione e quindi scegliere **Disinstalla**.

   Raramente, un'estensione errata non viene caricata e crea un report nella finestra degli errori, ma non viene visualizzata in Gestione estensioni. In tal caso, è possibile rimuovere l'estensione eliminando il file da:

   *% LocalAppData%* **\Local\Microsoft\VisualStudio\\[versione] \Extensions**

## <a name="DragExample"></a> Esempio
 L'esempio seguente mostra come creare linee di vita in un diagramma di sequenza in base alle parti e alle porte di un componente, trascinate da un diagramma dei componenti.

 Per testarlo, premere F5. Viene aperta un'istanza sperimentale di Visual Studio. In questa istanza aprire un modello UML e creare un componente in un diagramma dei componenti. Aggiungere a questo componente alcune interfacce e parti di componente interne. Selezionare le interfacce e le parti. Trascinare quindi le interfacce e le parti in un diagramma di sequenza. Trascinare dal diagramma componente fino alla scheda relativa al diagramma sequenza e quindi al diagramma sequenza. Verrà visualizzata una linea di vita per ogni interfaccia e parte.

 Per altre informazioni sull'associazione di interazioni a diagrammi di sequenza, vedere [modificare diagrammi di sequenza UML usando l'API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Interactions;
using Microsoft.VisualStudio.Uml.CompositeStructures;
using Microsoft.VisualStudio.Uml.Components;

/// <summary>
/// Creates lifelines from component ports and parts.
/// </summary>
[Export(typeof(IGestureExtension))]
[SequenceDesignerExtension]
public class CreateLifelinesFromComponentParts : IGestureExtension
{
  [Import]
  public IDiagramContext Context { get; set; }

  /// <summary>
  /// Called by the modeling framework when
  /// the user drops something on a target.
  /// </summary>
  /// <param name="target">The target shape or diagram </param>
  /// <param name="dragEvent">The item being dragged</param>
  public void OnDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    ISequenceDiagram diagram = Context.CurrentDiagram
            as ISequenceDiagram;
    IInteraction interaction = diagram.Interaction;
    if (interaction == null)
    {
      // Sequence diagram is empty: create an interaction.
      interaction = diagram.ModelStore.Root.CreateInteraction();
      interaction.Name = Context.CurrentDiagram.Name;
      diagram.Bind(interaction);
    }
    foreach (IConnectableElement connectable in
       GetConnectablesFromDrag(dragEvent))
    {
      ILifeline lifeline = interaction.CreateLifeline();
      lifeline.Represents = connectable;
      lifeline.Name = connectable.Name;
    }
  }

  /// <summary>
  /// Called by the modeling framework to determine whether
  /// the user can drop something on a target.
  /// Must not change anything.
  /// </summary>
  /// <param name="target">The target shape or diagram</param>
  /// <param name="dragEvent">The item being dragged</param>
  /// <returns>true if this item can be dropped on this target</returns>
  public bool CanDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);
    return connectables.Count() > 0;
  }

  ///<summary>
  /// Get dragged parts and ports of an IComponent.
  ///</summary>
  private IEnumerable<IConnectableElement>
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)
  {
    foreach (IElement element in
      GetModelElementsFromDragEvent(dragEvent))
    {
      IConnectableElement part = element as IConnectableElement;
      if (part != null)
      {
        yield return part;
      }
    }
  }

  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
          (DiagramDragEventArgs dragEvent)
  {
    //ElementGroupPrototype is the container for
    //dragged and copied elements and toolbox items.
    ElementGroupPrototype prototype =
       dragEvent.Data.
       GetData(typeof(ElementGroupPrototype))
            as ElementGroupPrototype;
    // Locate the originals in the implementation store.
    IElementDirectory implementationDirectory =
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

    return prototype.ProtoElements.Select(
      prototypeElement =>
      {
        ModelElement element = implementationDirectory
          .FindElement(prototypeElement.ElementId);
        ShapeElement shapeElement = element as ShapeElement;
        if (shapeElement != null)
        {
          // Dragged from a diagram.
          return shapeElement.ModelElement as IElement;
        }
        else
        {
          // Dragged from UML Model Explorer.
          return element as IElement;
        }
      });
  }

  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
  {
  }
}

```

 Il codice di `GetModelElementsFromDragEvent()` è descritto in [ottenere gli elementi del modello UML da IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

## <a name="see-also"></a>Vedere anche
 [Definire e installare un'estensione di modellazione](../modeling/define-and-install-a-modeling-extension.md) [estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md) [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md) [programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)
