---
title: Definire un comando di menu in un diagramma di modellazione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 00cb466fc9859bc36734ee3c42a23190632f39a2
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590652"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Definire un comando di menu in un diagramma di modellazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [definire un comando di menu in un diagramma di modellazione](https://docs.microsoft.com/visualstudio/modeling/define-a-menu-command-on-a-modeling-diagram).  
  
In Visual Studio è possibile definire altre voci di menu nei menu di scelta rapida di un diagramma UML. È possibile controllare se il comando di menu viene visualizzato ed è abilitato nel menu di scelta rapida di tutti gli elementi del diagramma ed è possibile scrivere codice che viene eseguito quando l'utente sceglie la voce di menu. È possibile creare un pacchetto di queste estensioni in un progetto[VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)(Visual Studio Integration Extension) e distribuirlo ad altri utenti di Visual Studio.  
  
## <a name="requirements"></a>Requisiti  
 Visualizzare [requisiti](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="defining-the-menu-command"></a>Definizione del comando di menu  
 Per creare un comando di menu per una finestra di progettazione UML, è necessario creare una classe che definisca il comportamento del comando e incorporare la classe in un'estensione VSIX (Visual Studio Integration Extension). L'estensione VSIX funge da contenitore che può installare il comando. Esistono due metodi alternativi per definire un comando di menu:  
  
-   **Creare un comando di menu nella relativa estensione VSIX usando un modello di progetto.** Questo è il metodo più rapido. Usarlo se non si vuole combinare i comandi di menu con altri tipi di estensione, ad esempio estensioni di convalida, elementi della casella degli strumenti personalizzati o gestori di movimento.  
  
-   **Creare un comando di menu separata e progetti VSIX.** Usare questo metodo per combinare diversi tipi di estensione nella stessa estensione VSIX. Ad esempio, se il comando di menu prevede che il modello rispetti dei vincoli specifici, è possibile incorporarlo nella stessa estensione VSIX come metodo di convalida.  
  
#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Per creare un comando di menu nella relativa estensione VSIX  
  
1.  Nella finestra di dialogo **Nuovo progetto** selezionare **Estensione comando**in **Progetti di modellazione**.  
  
2.  Aprire il file **.cs** nel nuovo progetto e modificare la classe `CommandExtension` per poter implementare il comando.  
  
     Per altre informazioni, vedere [Implementazione del comando di menu](#Implementing).  
  
3.  È possibile aggiungere altri comandi a questo progetto definendo nuove classi.  
  
4.  Testare il comando di menu premendo F5. Per altre informazioni, vedere [Esecuzione del comando di menu](#Executing).  
  
5.  Installare il comando di menu in un altro computer copiando il file **bin\\\*\\\*VSIX** che viene compilato dal progetto. Per altre informazioni, vedere [Installazione e disinstallazione di un'estensione](#Installing).  
  
 Ecco la procedura alternativa:  
  
#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Per creare un comando di menu in un progetto di libreria di classi (DLL) separato  
  
1.  Creare un progetto di libreria di classi in una soluzione di Visual Studio nuova o esistente.  
  
    1.  Nel menu **File** , scegliere **Nuovo**, **Progetto**.  
  
    2.  In **Modelli installati**selezionare **Visual C#** o **Visual Basic**. Nella colonna centrale scegliere **Libreria di classi**.  
  
    3.  Impostare **Soluzione** per indicare se si desidera creare una nuova soluzione o aggiungere un componente a una soluzione VSIX che è già stata aperta.  
  
    4.  Specificare il nome e il percorso del progetto e fare clic su OK.  
  
2.  Aggiungere i riferimenti seguenti al progetto.  
  
    |Riferimento|Operazioni consentite|  
    |---------------|--------------------------------|  
    |System.ComponentModel.Composition|Definire i componenti usando [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).|  
    |Microsoft.VisualStudio.Uml.Interfaces|Leggere e modificare le proprietà degli elementi del modello.|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Creare elementi del modello, modificare forme nei diagrammi.|  
    |Microsoft.VisualStudio.Modeling.Sdk.[versione]|Definire i gestori eventi del modello.<br /><br /> Incapsulare la serie di modifiche nel modello. Per altre informazioni, vedere [aggiornamenti di modelli di collegamento UML tramite transazioni](../modeling/link-uml-model-updates-by-using-transactions.md).|  
    |Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versione]<br /><br /> (non è sempre obbligatorio)|Accedere ad altri elementi del diagramma per i gestori di movimento.|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> Obbligatorio solo per i comandi nei diagrammi livello. Per altre informazioni, vedere [estendere i diagrammi livello](../modeling/extend-layer-diagrams.md).|Definire i comandi in un diagramma livello.|  
  
3.  Aggiungere un file di classe al progetto e impostarne il contenuto sul codice seguente.  
  
    > [!NOTE]
    >  Modificare in base alle proprie preferenze lo spazio dei nomi, il nome della classe e il valore restituito da `Text` .  
    >   
    >  Se si definiscono più comandi, questi vengono visualizzati nel menu in ordine alfabetico in base ai nomi delle classi.  
  
    ```  
    using System.ComponentModel.Composition;     
    using System.Linq;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
    using Microsoft.VisualStudio.Uml.Classes;   
        // ADD other UML namespaces if required  
  
    namespace UMLmenu1 // CHANGE  
    {  
      // DELETE any of these attributes if the command  
      // should not appear in some types of diagram.  
      [ClassDesignerExtension]  
      [ActivityDesignerExtension]  
      [ComponentDesignerExtension]  
      [SequenceDesignerExtension]  
      [UseCaseDesignerExtension]   
      // [LayerDesignerExtension]  
  
      // All menu commands must export ICommandExtension:  
      [Export (typeof(ICommandExtension))]  
      // CHANGE class name – determines order of appearance on menu:  
      public class Menu1 : ICommandExtension  
      {  
        [Import]  
        public IDiagramContext DiagramContext { get; set; }  
  
        public void QueryStatus(IMenuCommand command)  
        { // Set command.Visible or command.Enabled to false  
          // to disable the menu command.  
          command.Visible = command.Enabled = true;  
        }  
  
        public string Text  
        {  
          get { return "MENU COMMAND LABEL"; }  
        }  
  
        public void Execute(IMenuCommand command)  
        {  
          // A selection of starting points:  
          IDiagram diagram = this.DiagramContext.CurrentDiagram;  
          foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
          { IElement element = shape.Element; }  
          IModelStore modelStore = diagram.ModelStore;  
          IModel model = modelStore.Root;  
          foreach (IElement element in modelStore.AllInstances<IClass>())   
          { }  
        }  
      }  
    }  
    ```  
  
     Per altre informazioni su cosa inserire nei metodi, vedere [Implementazione del comando di menu](#Implementing).  
  
 È necessario aggiungere il comando di menu a un progetto VSIX, che funge da contenitore per l'installazione del comando. Se si desidera, è possibile includere altri componenti nello stesso progetto VSIX.  
  
#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Per aggiungere un comando di menu a un progetto VSIX  
  
1.  Questa procedura non è necessaria se i comandi di menu sono stati creati con la relativa estensione VSIX.  
  
2.  Creare un progetto VSIX, a meno che la soluzione non ne contenga già uno.  
  
    1.  In **Esplora soluzioni**scegliere **Aggiungi**dal menu di scelta rapida della soluzione e quindi fare clic su **Nuovo progetto**.  
  
    2.  In **Modelli installati**espandere **Visual C#** o **Visual Basic**, quindi scegliere **Extensibility**. Nella colonna centrale scegliere **Progetto VSIX**.  
  
3.  In Esplora soluzioni scegliere **Imposta come progetto di avvio**dal menu di scelta rapida del progetto VSIX.  
  
4.  Aprire **source.extension.vsixmanifest**.  
  
    1.  Nella scheda **Metadati** impostare un nome per il progetto VSIX.  
  
    2.  Nella scheda **Destinazioni di installazione** impostare le versioni di Visual Studio come destinazioni.  
  
    3.  Nella scheda **Asset** scegliere **Nuovo**e nella finestra di dialogo impostare le opzioni seguenti:  
  
         **Tipo** = **Componente MEF**  
  
         **Origine** = **Progetto nella soluzione corrente**  
  
         **Progetto** = *Progetto di libreria di classi*  
  
##  <a name="Implementing"></a> Implementazione del comando di Menu  
 La classe del comando di menu implementa i metodi obbligatori per <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>.  
  
|||  
|-|-|  
|`string Text { get; }`|Restituisce l'etichetta della voce di menu.|  
|`void QueryStatus(IMenuCommand command);`|Chiamato quando l'utente fa clic con il pulsante destro del mouse nel diagramma.<br /><br /> Questo metodo non dovrebbe modificare il modello.<br /><br /> Usare `DiagramContext.CurrentDiagram.SelectedShapes` per determinare se si vuole visualizzare e abilitare il comando.<br /><br /> Impostare:<br /><br /> -   `command.Visible` per `true` se il comando deve apparire nel menu quando l'utente fa clic nel diagramma<br />-   `command.Enabled` per `true` se l'utente può scegliere il comando nel menu di scelta<br />-   `command.Text` Per impostare in modo dinamico l'etichetta del menu|  
|`void Execute (IMenuCommand command);`|Chiamato quando l'utente fa clic sulla voce di menu, se è visibile e abilitata.|  
  
### <a name="accessing-the-model-in-code"></a>Accesso al modello nel codice  
 Includendo nella classe del comando di menu la dichiarazione seguente:  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  
  
 ...  
  
 La dichiarazione di `IDiagramContext` consente di scrivere nei metodi il codice per l'accesso al diagramma, alla selezione corrente e al modello:  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}  
```  
  
### <a name="navigating-and-updating-the-model"></a>Esplorazione e aggiornamento del modello  
 Gli elementi del modello UML sono tutti disponibili tramite l'API. Dalla selezione corrente o dalla radice del modello, è possibile accedere a tutti gli altri elementi. Per altre informazioni, vedere [esplorare il modello UML](../modeling/navigate-the-uml-model.md) e [programmazione con l'API UML](../modeling/programming-with-the-uml-api.md).  
  
 Se è necessario gestire un diagramma di sequenza, vedere anche [diagrammi di sequenza UML modificare usando l'API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 L'API consente anche di modificare le proprietà degli elementi, eliminare elementi e relazioni e creare nuovi elementi e relazioni.  
  
 Per impostazione predefinita, ogni modifica apportata al metodo Execute verrà eseguita in una transazione separata. L'utente potrà annullare ogni singola modifica. Se si desidera raggruppare le modifiche in una singola transazione, usare una <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> come descritto in [aggiornamenti di modelli di collegamento UML tramite transazioni](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
### <a name="use-the-ui-thread-for-updates"></a>Usare il thread dell'interfaccia utente per gli aggiornamenti  
 In alcuni casi può essere utile eseguire gli aggiornamenti al modello da un thread in background. Ad esempio, se il comando carica dati da una risorsa lenta, è possibile eseguire il caricamento in un thread in background in modo che l'utente possa visualizzare le modifiche mentre sono in corso e, se necessario, annullare l'operazione.  
  
 Tuttavia, è necessario sapere che l'archivio modelli non è thread-safe. È consigliabile usare sempre il thread dell'interfaccia utente per eseguire gli aggiornamenti e, se possibile, impedire all'utente di apportare modifiche mentre è in corso l'operazione in background. Per un esempio, vedere [aggiornare un modello UML da un thread in background](../modeling/update-a-uml-model-from-a-background-thread.md).  
  
##  <a name="Executing"></a> L'esecuzione del comando di Menu  
 A scopo di test, eseguire il comando in modalità di debug.  
  
#### <a name="to-test-the-menu-command"></a>Per testare il comando di menu  
  
1.  Premere **F5**o scegliere **Avvia debug** dal menu **Debug**.  
  
     Viene avviata un'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     **Risoluzione dei problemi**: se un nuovo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] non avviato:  
  
    -   Se si hanno più progetti, assicurarsi che il progetto VSIX sia impostato come progetto di avvio della soluzione.  
  
    -   In Esplora soluzioni scegliere **Proprietà**dal menu di scelta rapida del progetto di avvio o dell'unico progetto. Nell'editor delle proprietà del progetto selezionare la scheda **Debug** . Assicurarsi che la stringa nel **Avvia programma esterno** campo sia il percorso completo di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], in genere:  
  
         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2.  Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aprire o creare un progetto di modellazione e aprire o creare un diagramma di modellazione. Usare un diagramma appartenente a uno dei tipi elencati negli attributi della classe del comando di menu.  
  
3.  Aprire il menu di scelta rapida in qualsiasi punto del diagramma. Il comando dovrebbe essere visualizzato nel menu.  
  
     **Risoluzione dei problemi**: se il comando non appare nel menu, verificare che:  
  
    -   Il progetto del comando di menu sia elencato come componente MEF nella scheda **Asset** in **source.extensions.manifest** nel progetto VSIX.  
  
    -   I parametri degli attributi `Import` ed `Export` siano validi.  
  
    -   Il `QueryStatus` metodo non imposta il `command`.`Enabled` o `Visible` su `false`.  
  
    -   Il tipo di diagramma del modello in uso (classe UML, sequenza e così via) sia elencato come uno degli attributi della classe del comando di menu `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` e così via.  
  
##  <a name="Installing"></a> Installazione e disinstallazione di un'estensione  
 È possibile installare un'estensione di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sia nel proprio computer che in altri computer.  
  
#### <a name="to-install-an-extension"></a>Per installare un'estensione  
  
1.  Nel computer trovare il file **.vsix** compilato dal progetto VSIX.  
  
    1.  In **Esplora soluzioni**scegliere **Apri cartella in Esplora risorse**dal menu di scelta rapida del progetto VSIX.  
  
    2.  Individuare il file **bin\\\*\\**_YourProject_**VSIX**  
  
2.  Copiare il file **.vsix** nel computer di destinazione in cui si vuole installare l'estensione. Può trattarsi del computer in uso o di un altro computer.  
  
     Nel computer di destinazione deve essere una delle edizioni di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] indicata nel **vsixmanifest**.  
  
3.  Nel computer di destinazione aprire il file **.vsix** , ad esempio facendovi doppio clic.  
  
     **Visual Studio Extension Installer** si apre e installa l'estensione.  
  
4.  Avviare o riavviare [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Per disinstallare un'estensione  
  
1.  Nel menu **Strumenti** scegliere **Estensioni e aggiornamenti**.  
  
2.  Espandere **Estensioni installate**.  
  
3.  Selezionare l'estensione e quindi scegliere **Disinstalla**.  
  
 Raramente, un'estensione errata non viene caricata e crea un report nella finestra degli errori, ma non viene visualizzata in Gestione estensioni. In tal caso, è possibile rimuovere l'estensione eliminando il file da:  
  
 *% LocalAppData %* **\Local\Microsoft\VisualStudio\\\Extensions [versione]**  
  
##  <a name="MenuExample"></a> Esempio  
 L'esempio seguente mostra il codice per un comando di menu che scambierà i nomi di due elementi in un diagramma classi. Questo codice deve essere compilato in un progetto di estensione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e installato come indicato nelle precedenti sezioni.  
  
```  
using System.Collections.Generic; // for IEnumerable  
using System.ComponentModel.Composition;  
  // for [Import], [Export]  
using System.Linq; // for IEnumerable extensions  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
  // for IDiagramContext  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
  // for designer extension attributes  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  // for ShapeElement  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext  
using Microsoft.VisualStudio.Uml.Classes;  
  // for class diagrams, packages  
  
/// <summary>  
/// Extension to swap names of classes in a class diagram.  
/// </summary>  
namespace SwapClassNames  
{  
  // Declare the class as an MEF component:  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  // Add more ExportMetadata attributes to make  
  // the command appear on diagrams of other types.  
  public class NameSwapper : ICommandExtension  
  {  
  // MEF required interfaces:  
  [Import]  
  public IDiagramContext Context { get; set; }  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  /// <param name="command"></param>  
  public void Execute(IMenuCommand command)  
  {  
    // Get selected shapes that are IClassifiers -  
    // IClasses, IInterfaces, IEnumerators.  
    var selectedShapes = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  
  
    // Get model elements displayed by shapes.  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  
  
    // Do the swap in a transaction so that user  
    // cannot undo one change without the other.  
    using (ILinkedUndoTransaction transaction =  
    LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
    string firstName = firstElement.Name;  
    firstElement.Name = lastElement.Name;  
    lastElement.Name = firstName;  
    transaction.Commit();  
    }  
  }  
  
  /// <summary>  
  /// Called by Visual Studio to determine whether  
  /// menu item should be visible and enabled.  
  /// </summary>  
  public void QueryStatus(IMenuCommand command)  
  {   
    int selectedClassifiers = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>().Count();  
    command.Visible = selectedClassifiers > 0;  
    command.Enabled = selectedClassifiers == 2;  
  }  
  
  /// <summary>  
  /// Name of the menu command.  
  /// </summary>  
  public string Text  
  {  
    get { return "Swap Names"; }  
  }  
  }  
  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Definire e installare un'estensione di modellazione](../modeling/define-and-install-a-modeling-extension.md)   
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definire un gestore movimenti in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Definire una classe personalizzata elemento della casella degli strumenti di modellazione](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Modificare i diagrammi di sequenza UML usando l'API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)   
 [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)   
 [Esempio: Comando per allineare le forme in un diagramma UML](http://go.microsoft.com/fwlink/?LinkID=213809)



