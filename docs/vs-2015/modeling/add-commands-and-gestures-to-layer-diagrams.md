---
title: Aggiungere comandi e movimenti a diagrammi livello | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom commands
- layer diagrams, adding custom gestures
ms.assetid: ac9c417b-0b40-4a90-86f5-ee3cbdce030b
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7b0c54975cdd5bc86f77dddbd5ca1a56c1896394
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655322"
---
# <a name="add-commands-and-gestures-to-layer-diagrams"></a>Aggiunta di comandi e movimenti a diagrammi livello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile definire comandi del menu di scelta rapida e gestori movimenti nei diagrammi livello in Visual Studio. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) che è possibile distribuire ad altri utenti di Visual Studio.

 Se si vuole, è possibile definire gestori comandi e movimenti diversi nello stesso progetto di Visual Studio. È anche possibile combinare più progetti di questo tipo in un progetto VSIX. Ad esempio, è possibile definire un unico progetto VSIX che include comandi di livello, un linguaggio specifico di dominio e comandi per i diagrammi UML.

> [!NOTE]
> È anche possibile personalizzare la convalida dell'architettura, in cui il codice sorgente dell'utente viene confrontato con diagrammi livello. È consigliabile definire la convalida dell'architettura in un progetto di Visual Studio separato. È possibile aggiungerlo allo stesso progetto VSIX come per le altre estensioni. Per altre informazioni, vedere [aggiungere la convalida dell'architettura personalizzata ai diagrammi livello](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Requisiti
 Vedere [Requisiti](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Definizione di un comando o movimento in un nuovo progetto VSIX
 Il modo più rapido per creare un'estensione è usare il modello di progetto. In questo modo il codice e il manifesto VSIX vengono inseriti nello stesso progetto.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>Per definire un'estensione tramite un modello di progetto

1. Creare un progetto in una nuova soluzione usando il comando **Nuovo progetto** del menu **File** .

2. Nella finestra di dialogo **Nuovo progetto** , in **Progetti di modellazione**, selezionare **Estensione di comando progettazione livelli** o **Estensione di movimento progettazione livelli**.

    Il modello crea un progetto che contiene un piccolo esempio funzionante.

3. Per testare l'estensione, premere **CTRL+F5** o **F5**.

    Viene avviata un'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . In questa istanza creare un diagramma livello. L'estensione di comando o di movimento dovrebbe funzionare in questo diagramma.

4. Chiudere l'istanza sperimentale e modificare il codice di esempio. Per altre informazioni, vedere [esplorare e aggiornare i modelli di livello nel codice programma](../modeling/navigate-and-update-layer-models-in-program-code.md).

5. È possibile aggiungere più gestori comandi o movimenti allo stesso progetto. Per altre informazioni, vedere una delle sezioni seguenti:

    [Definizione di un comando di menu](#command)

    [Definizione di un gestore movimenti](#gesture)

6. Per installare l'estensione nell'istanza principale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]o in un altro computer, trovare il file **.vsix** in *bin\\*. Copiare il file nel computer in cui si vuole installare l'estensione e fare doppio clic sul file stesso. Per disinstallare l'estensione, usare l'opzione **Estensioni e aggiornamenti** del menu **Strumenti** .

## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Aggiunta di un comando o movimento a un progetto VSIX separato
 Se si vuole creare un progetto VSIX contenente comandi, validator dei livelli e altre estensioni, è consigliabile creare un unico progetto per definire l'estensione VSIX e progetti separati per i gestori. Per informazioni sugli altri tipi di estensione di modellazione, vedere [estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md).

#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Per aggiungere estensioni del livello a un progetto VSIX separato

1. Creare un progetto di libreria di classi in una soluzione di Visual Studio nuova o esistente. Nella finestra di dialogo **Nuovo progetto** fare clic su **Visual C#** e quindi su **Libreria di classi**. Questo progetto conterrà le classi del gestore comandi o movimenti.

    > [!NOTE]
    > È possibile definire più classi dei gestori comandi o movimenti in una stessa libreria di classi, ma è consigliabile definire le classi per la convalida dei livelli in una libreria di classi distinta.

2. Identificare o creare un progetto VSIX nella soluzione. Un progetto VSIX contiene un file denominato **source.extension.vsixmanifest**. Per aggiungere un progetto VSIX:

    1. Nella finestra di dialogo **Nuovo progetto** espandere **Visual C#**, fare clic su **Extensibility**e quindi fare clic su **Progetto VSIX**.

    2. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto VSIX e scegliere **Imposta come progetto di avvio**.

    3. Fare clic su **Seleziona versioni** e assicurarsi che sia selezionato **Visual Studio** .

3. In **source.extension.vsixmanifest**, in **Asset**, aggiungere il progetto di gestore comandi o movimenti come componente MEF.

    1. Nella scheda **Asset**scegliere **Nuovo**.

    2. In **Tipo**selezionare **Microsoft.VisualStudio.MefComponent**.

    3. In **Origine**selezionare **Progetto nella soluzione corrente** e selezionare il nome del progetto del gestore comandi o movimenti.

    4. Salvare il file.

4. Tornare al progetto del gestore comandi o movimenti e aggiungere i riferimenti seguenti al progetto.

|**Riferimento**|**Operazioni consentite**|
|-------------------|------------------------------------|
|Programmi\Microsoft Visual Studio [versione]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Creare e modificare livelli|
|Microsoft.VisualStudio.Uml.Interfaces|Creare e modificare livelli|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Modificare forme nei diagrammi|
|System.ComponentModel.Composition|Definire i componenti mediante Managed Extensibility Framework (MEF).|
|Microsoft.VisualStudio.Modeling.Sdk.[versione]|Definire le estensioni di modellazione|
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versione]|Aggiornare forme e diagrammi|

1. Modificare il file di classe nel progetto di libreria di classi C# contenente il codice per l'estensione. Per altre informazioni, vedere una delle sezioni seguenti:

     [Definizione di un comando di menu](#command)

     [Definizione di un gestore movimenti](#gesture)

     Vedere anche [esplorare e aggiornare i modelli di livello nel codice programma](../modeling/navigate-and-update-layer-models-in-program-code.md).

2. Per testare la funzionalità, premere CTRL+F5 o F5. Viene aperta un'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . In questa istanza creare o aprire un diagramma livello.

3. Per installare il progetto VSIX nell'istanza principale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]o in un altro computer, trovare il file **.vsix** nella directory **bin** del progetto VSIX. Copiare il file nel computer in cui si vuole installare il progetto VSIX. Fare doppio clic sul file VSIX in Esplora risorse (Esplora file in Windows 8).

     Per disinstallare l'estensione, usare l'opzione **Estensioni e aggiornamenti** del menu **Strumenti** .

## <a name="defining-a-menu-command"></a><a name="command"></a> Definizione di un comando di menu
 È possibile aggiungere altre definizioni dei comandi di menu a un progetto di comandi o movimenti esistente. Ogni comando viene definito da una classe che ha le caratteristiche seguenti:

- La classe viene dichiarata nel modo seguente:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- Lo spazio dei nomi e il nome della classe sono irrilevanti.

- I metodi che implementano `ICommandExtension` sono i seguenti:

  - `string Text {get;}` : etichetta visualizzata nel menu.

  - `void QueryStatus(IMenuCommand command)` : viene chiamato quando l'utente fa clic con il pulsante destro del mouse sul diagramma e determina se il comando deve essere visibile e abilitato per la selezione corrente dell'utente.

  - `void Execute(IMenuCommand command)` : viene chiamato quando l'utente seleziona il comando.

- Per determinare la selezione corrente, è possibile importare `IDiagramContext`:

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

  Per altre informazioni, vedere [esplorare e aggiornare i modelli di livello nel codice programma](../modeling/navigate-and-update-layer-models-in-program-code.md).

  Per aggiungere un nuovo comando, creare un nuovo file di codice che contiene l'esempio riportato di seguito. Quindi, testarlo e modificarlo.

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for Layer diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> Definizione di un gestore movimenti
 Un gestore movimenti risponde quando l'utente trascina elementi nel diagramma livello e quando l'utente fa doppio clic in un punto qualsiasi del diagramma.

 È possibile aggiungere al progetto VSIX del gestore comandi o movimenti esistente un file di codice che definisce un gestore movimenti:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;
namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

 Per quanto riguarda i gestori movimenti tenere presente quanto segue:

- I membri di `IGestureExtension` sono:

   **OnDoubleClick** : viene chiamato quando l'utente fa doppio clic in qualsiasi punto del diagramma.

   **CanDragDrop** : viene chiamato ripetutamente quando l'utente sposta il mouse durante il trascinamento di un elemento nel diagramma. Deve operare rapidamente.

   **OnDragDrop** : viene chiamato quando l'utente rilascia un elemento nel diagramma.

- Il primo argomento per ogni metodo è un `IShape`, da cui è possibile ottenere l'elemento del livello. Ad esempio:

  ```
  public void OnDragDrop(IShape target, IDataObject data)
  {
      ILayerElement element = target.GetLayerElement();
      if (element is ILayer)
      {
          // ...
      }
  }
  ```

- I gestori per alcuni tipi di elemento trascinato sono già definiti. Ad esempio, l'utente può trascinare elementi da Esplora soluzioni in un diagramma livello. Non è possibile definire un gestore del trascinamento per questi tipi di elemento. In questi casi, i metodi `DragDrop` non verranno richiamati.

  Per ulteriori informazioni su come decodificare altri elementi quando vengono trascinati nel diagramma, vedere [definire un gestore movimenti in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="see-also"></a>Vedere anche
 [Esplorare e aggiornare i modelli di livello nel codice del programma](../modeling/navigate-and-update-layer-models-in-program-code.md) [aggiungere la convalida dell'architettura personalizzata ai diagrammi livello](../modeling/add-custom-architecture-validation-to-layer-diagrams.md) [definire e installare un'estensione di modellazione](../modeling/define-and-install-a-modeling-extension.md)
