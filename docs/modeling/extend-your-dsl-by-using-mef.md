---
title: Estendere il DSL mediante MEF
description: Informazioni su come è possibile estendere il linguaggio specifico di dominio (DSL) usando il Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 324037010e642ab4e96f6efea5da0f232c9bd530
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935066"
---
# <a name="extend-your-dsl-by-using-mef"></a>Estendere il DSL mediante MEF

È possibile estendere il linguaggio specifico di dominio (DSL) usando Managed Extensibility Framework (MEF). L'utente o altri sviluppatori saranno in grado di scrivere estensioni per il linguaggio DSL senza modificare la definizione DSL e il codice programma. Tali estensioni includono comandi di menu, gestori di trascinamento della selezione e convalida. Gli utenti saranno in grado di installare il linguaggio DSL e, facoltativamente, di installare le estensioni.

Inoltre, quando si Abilita MEF nel linguaggio DSL, può essere più facile scrivere alcune delle funzionalità del linguaggio DSL, anche se tutte sono compilate insieme al linguaggio DSL.

Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Per abilitare l'estensione del linguaggio DSL mediante MEF

1. Creare una nuova cartella denominata **MefExtension in** all'interno del progetto **DslPackage** . Aggiungere i file seguenti:

     Nome file: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Impostare il GUID in questo file in modo che corrisponda al GUID CommandSetId definito in DslPackage\GeneratedCode\Constants.tt

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    Nome file: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    Nome file: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    Nome file: `ValidationExtensionRegistrar.tt`

    Se si aggiunge questo file, è necessario abilitare la convalida nel linguaggio DSL usando almeno una delle opzioni in **EditorValidation** in DSL Explorer.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Nome file: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. Creare una nuova cartella denominata **MefExtension in** all'interno del progetto **DSL** . Aggiungere i file seguenti:

     Nome file: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    Nome file: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    Nome file: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. Aggiungere la riga seguente al file esistente denominato **DslPackage\Commands.vsct**:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Inserire la riga dopo la `<Include>` direttiva esistente.

4. Aprire *DslDefinition. DSL*.

5. In DSL Explorer selezionare **editor \Validation**.

6. Nella Finestra Proprietà verificare che almeno una delle proprietà denominate **usi** sia `true` .

7. Nella barra degli strumenti **Esplora soluzioni** fare clic su **trasforma tutti i modelli**.

     I file secondari vengono visualizzati sotto ciascuno dei file aggiunti.

8. Compilare ed eseguire la soluzione per verificare che sia ancora funzionante.

Il linguaggio DSL è ora abilitato per MEF. È possibile scrivere comandi di menu, gestori di movimenti e vincoli di convalida come estensioni MEF. È possibile scrivere queste estensioni nella soluzione DSL insieme ad altro codice personalizzato. Inoltre, l'utente o altri sviluppatori possono scrivere estensioni di Visual Studio separate che estendono il linguaggio DSL.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Creare un'estensione per un linguaggio DSL abilitato per MEF

Se si ha accesso a un linguaggio DSL abilitato per MEF creato dall'utente o da un altro utente, è possibile scrivere estensioni. È possibile utilizzare le estensioni per aggiungere comandi di menu, gestori di movimenti o vincoli di convalida. Per creare queste estensioni, usare una soluzione Visual Studio Extension (VSIX). La soluzione è costituita da due parti: un progetto di libreria di classi che compila l'assembly di codice e un progetto VSIX per il pacchetto dell'assembly.

### <a name="to-create-a-dsl-extension-vsix"></a>Per creare un'estensione DSL VSIX

1. Creare un nuovo progetto **Libreria di classi**.

2. Nel nuovo progetto aggiungere un riferimento all'assembly del linguaggio DSL.

   - Questo assembly ha in genere un nome che termina con ".Dsl.dll".

   - Se si ha accesso al progetto DSL, è possibile trovare il file di assembly nel **\\ \\ \* contenitore DSL** directory

   - Se si ha accesso al file VSIX DSL, è possibile trovare l'assembly modificando l'estensione del nome file del file VSIX in ". zip". Decomprimere il file zip.

3. Aggiungere i riferimenti agli assembly .NET seguenti:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Creare un nuovo progetto **progetto VSIX** .

5. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto VSIX e scegliere **Imposta come progetto di avvio**.

6. Nel nuovo progetto aprire **source. Extension. vsixmanifest**.

7. Fare clic su **Aggiungi contenuto**. Nella finestra di dialogo impostare **tipo di contenuto** su **componente MEF** e **progetto di origine** sul progetto libreria di classi.

8. Aggiungere un riferimento VSIX al linguaggio DSL.

   1. In **source. Extension. vsixmanifest** fare clic su **Aggiungi riferimento**

   2. Nella finestra di dialogo fare clic su **Aggiungi payload** , quindi individuare il file VSIX del linguaggio DSL. Il file VSIX è compilato nella soluzione DSL, in **DslPackage \\ bin \\ \***.

       Ciò consente agli utenti di installare il linguaggio DSL e l'estensione nello stesso momento. Se l'utente ha già installato il linguaggio DSL, verrà installata solo l'estensione.

9. Esaminare e aggiornare gli altri campi di **source. Extension. vsixmanifest**. Fare clic su **Seleziona edizioni** e verificare che siano impostate le edizioni di Visual Studio corrette.

10. Aggiungere codice al progetto libreria di classi. Usare gli esempi nella sezione successiva come guida.

     È possibile aggiungere qualsiasi numero di classi di comandi, movimenti e di convalida.

11. Per testare l'estensione, premere **F5**. Nell'istanza sperimentale di Visual Studio creare o aprire un file di esempio del linguaggio DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Scrittura di estensioni MEF per DSLs

È possibile scrivere estensioni nel progetto di codice assembly di una soluzione di estensione DSL separata. È anche possibile usare MEF nel progetto DslPackage, come un modo pratico per scrivere comandi, movimenti e codice di convalida come parte del linguaggio DSL.

### <a name="menu-commands"></a>Comandi di menu

Per scrivere un comando di menu, definire una classe che implementi <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> e prefissi la classe con l'attributo definito nel linguaggio DSL, denominato *dslutente* `CommandExtension` . È possibile scrivere più di una classe di comandi di menu.

`QueryStatus()` viene chiamato ogni volta che l'utente fa clic con il pulsante destro del mouse sul diagramma. Deve controllare la selezione corrente e impostare `command.Enabled` per indicare quando il comando è applicabile.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>Gestori movimenti

Un gestore movimenti può gestire gli oggetti trascinati nel diagramma da qualsiasi posizione, all'interno o all'esterno di Visual Studio. L'esempio seguente consente all'utente di trascinare i file da Esplora risorse nel diagramma. Crea elementi che contengono i nomi dei file.

È possibile scrivere gestori per gestire i trascinamenti da altri modelli DSL e modelli UML. Per altre informazioni, vedere [procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md).

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>Vincoli di convalida

I metodi di convalida sono contrassegnati dall' `ValidationExtension` attributo generato dal DSL e anche da <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . Il metodo può essere visualizzato in qualsiasi classe non contrassegnata da un attributo.

Per ulteriori informazioni, vedere [convalida in un linguaggio Domain-Specific](../modeling/validation-in-a-domain-specific-language.md).

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>Vedi anche

- [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Procedura: Aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)
