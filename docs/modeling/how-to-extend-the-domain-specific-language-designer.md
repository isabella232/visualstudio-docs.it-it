---
title: 'Procedura: Estendere la Finestra di progettazione Domain-Specific Language'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: d1cec12a7a97ffa23f2eb75ffd9fc53da8ad2ed1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940706"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Procedura: Estendere la Finestra di progettazione Domain-Specific Language

È possibile creare estensioni nella finestra di progettazione che consente di modificare le definizioni DSL. Tipi di estensione che è possibile apportare includono l'aggiunta di comandi di menu, aggiunta di gestori per trascinano e fare doppio clic sui movimenti e le regole che vengono attivate quando modificare determinati tipi di valori o relazioni. Le estensioni possono essere incluso nel pacchetto come Visual Studio Integration Extension (VSIX) e distribuite agli altri utenti.

Per codice di esempio e altre informazioni su questa funzionalità, vedere Visual Studio [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

## <a name="set-up-the-solution"></a>Configurare la soluzione

Configurare un progetto che contiene il codice dell'estensione e un progetto VSIX che esporta il progetto. La soluzione può contenere altri progetti sono incorporati nella stessa estensione VSIX.

### <a name="to-create-a-dsl-designer-extension-solution"></a>Per creare una soluzione di estensione di progettazione DSL

1.  Creare un nuovo progetto usando il modello di progetto libreria di classi. Nel **nuovo progetto** finestra di dialogo, fare clic su **Visual c#** e quindi nella finestra centrale fare clic su **libreria di classi**.

     Questo progetto conterrà il codice delle estensioni.

2.  Creare un nuovo progetto usando il modello di progetto VSIX. Nel **nuovo progetto** finestra di dialogo espandere **Visual c#**, fare clic su **estendibilità**e quindi nella finestra centrale selezionare **progetto VSIX**.

     Selezionare **Aggiungi a soluzione**.

     Vsixmanifest viene aperto nell'editor del manifesto VSIX.

3.  Sopra il campo del contenuto, fare clic su **Aggiungi contenuto**.

4.  Nel **Aggiungi contenuto** della finestra di dialogo set **selezionare un tipo di contenuto** al **componente MEF**e impostare **progetto** al progetto libreria di classi.

5.  Fare clic su **Seleziona versioni** e assicurarsi che **Visual Studio Enterprise** sia selezionata.

6.  Assicurarsi che il progetto VSIX sia il progetto di avvio della soluzione.

7.  Nel progetto libreria di classi, aggiungere riferimenti agli assembly seguenti:

     Microsoft.VisualStudio.CoreUtility

     Microsoft.VisualStudio.Modeling.Sdk.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.Drawing

     System.Drawing.Design

     System.Windows.Forms

## <a name="test-and-deployment"></a>Test e distribuzione

Per testare qualsiasi delle estensioni in questo argomento, compilare ed eseguire la soluzione. Viene aperta un'istanza sperimentale di Visual Studio. In questo caso, aprire una soluzione DSL. Modificare il diagramma DslDefinition. Il comportamento dell'estensione può essere visualizzato.

Per distribuire le estensioni per il principale di Visual Studio e per altri computer, seguire questa procedura:

1.  Trovare il file di installazione di VSIX nel progetto VSIX in bin\\*\*\\\*VSIX

2.  Copiare questo file nel computer di destinazione e quindi in Windows Explorer (o Esplora File), fare doppio clic.

     Verrà aperto Gestione estensioni di Visual Studio per verificare che sia stato installato l'estensione.

Per disinstallare l'estensione, seguire questa procedura:

1.  In Visual Studio sul **degli strumenti** menu, fare clic su **gestore estensioni del**.

2.  Selezionare l'estensione ed eliminarlo.

## <a name="add-a-shortcut-menu-command"></a>Aggiungere un comando di Menu di scelta rapida

Per rendere un comando di menu di scelta rapida vengono visualizzati nell'area di progettazione DSL o nella finestra Esplora DSL, scrivere una classe simile a quello riportato di seguito.

La classe deve implementare `ICommandExtension` e deve avere l'attributo `DslDefinitionModelCommandExtension`.

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handle-mouse-gestures"></a>Gestire i movimenti del Mouse

Il codice è simile al codice del comando di menu.

```csharp
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="respond-to-value-changes"></a>Rispondere alle modifiche ai valori

Questo gestore di è necessario un modello di dominio funzioni correttamente. Offriamo un modello di dominio semplice.

```csharp
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

Il codice seguente implementa un modello semplice. Creare un nuovo GUID per sostituire il segnaposto.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```