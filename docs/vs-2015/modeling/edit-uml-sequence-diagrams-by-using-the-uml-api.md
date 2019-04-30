---
title: Modificare i diagrammi di sequenza UML usando l'API UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML activity diagrams, programming
ms.assetid: 8cdd0203-85ef-4c62-9abc-da4cb26fa504
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c619ae6efd1de48319bf9c0398ee8ab4e3cd57ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442965"
---
# <a name="edit-uml-sequence-diagrams-by-using-the-uml-api"></a>Modificare i diagrammi di sequenza UML usando l'API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un'interazione è una sequenza di messaggi tra un set di linee di vita. Un'interazione viene visualizzata in un diagramma di sequenza UML.  
  
 Per informazioni dettagliate sull'API, vedere <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>.  
  
 Per un'introduzione più generale alla scrittura di comandi e gestori movimento per i diagrammi UML, vedere [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
## <a name="basic-code"></a>Codice di base  
  
### <a name="namespace-imports"></a>Importazioni di spazi dei nomi  
 È necessario includere le seguenti istruzioni `using`:  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
   // for basic UML types such as IPackage  
using Microsoft.VisualStudio.Uml.Interactions;  
   // for interaction types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // to create elements and use additional functions  
```  
  
 Se si creano comandi di menu e gestori movimenti, sarà inoltre necessario:  
  
```  
using System.ComponentModel.Composition;   
   // for Import and Export  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   // for ICommandExtension  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   // for diagrams and context  
```  
  
 Per altre informazioni, vedere [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="getting-the-context"></a>Recupero del contesto  
 Se si sta modificando un'interazione come parte di un comando o di un gestore movimenti in un diagramma di sequenza, è possibile ottenere un riferimento al contesto. Ad esempio:  
  
```  
[SequenceDesignerExtension]  
[Export(typeof(ICommandExtension))]    
public class MySequenceDiagramCommand : ICommandExtension  
{  
    [Import]  
    public IDiagramContext Context { get; set; }  
    public void QueryStatus (IMenuCommand command)  
    {  
      ISequenceDiagram sequenceDiagram =   
          Context.CurrentDiagram as ISequenceDiagram;  
         ...  
```  
  
### <a name="generated-and-uml-sequence-diagrams"></a>Diagrammi di sequenza UML e generati  
 Esistono due tipi di diagrammi di sequenza: quelli creati manualmente in un progetto di modellazione UML e quelli generati dal codice programma. Usare la proprietà `UmlMode` per individuare il proprio diagramma di sequenza.  
  
> [!NOTE]
> Questa proprietà restituisce false solo per i diagrammi di sequenza generati dal codice con Visual Studio 2013 e versioni precedenti. Sono inclusi i diagrammi di sequenza generati dal codice di cui è stata eseguita la migrazione dalla versione 2013 e precedenti. Questa versione di Visual Studio non supporta la generazione di nuovi diagrammi di sequenza.  
  
 Ad esempio, per creare un comando di menu visibile solo nei diagrammi di sequenza UML, il metodo `QueryStatus()` può includere l'istruzione seguente:  
  
```  
command.Enabled = command.Visible =   
      sequenceDiagram != null && sequenceDiagram.UmlMode;  
```  
  
 In un diagramma di sequenza generato, le linee di vita, i messaggi e gli altri elementi sono quasi uguali a quelli di un diagramma di sequenza UML. In un modello UML, l'archivio modelli ha una radice, che è il modello proprietario di tutti gli altri elementi, ma nell'archivio modelli esiste un'interazione generata contenente una radice null:  
  
```  
IModel rootModel = sequenceDiagram.ModelStore.Root;  
    // !sequenceDiagram.UmlMode == (rootModel == null)  
```  
  
## <a name="to-create-and-display-an-interaction"></a>Per creare e visualizzare un'interazione  
 Creare l'interazione come figlio di un pacchetto o di un modello.  
  
 Ad esempio, se si sta sviluppando un comando che potrebbe essere eseguito in un diagramma di sequenza vuoto, per prima cosa è sempre opportuno controllare se l'interazione esiste.  
  
```  
public void Execute (IMenuCommand command)  
{  
    ISequenceDiagram sequenceDiagram =   
         Context.CurrentDiagram as ISequenceDiagram;  
    if (sequenceDiagram == null) return;  
    // Get the diagram's interaction:  
    IInteraction interaction = sequenceDiagram.Interaction;  
    // A new sequence diagram might have no interaction:  
    if (interaction == null)  
    {  
       // Get the home package or model of the diagram:  
       IPackage parentPackage = sequenceDiagram.GetObject<IPackage>();  
       interaction = parentPackage.CreateInteraction();  
       // Display the interaction on the sequence diagram:  
       sequenceDiagram.Bind(interaction);  
    }   
```  
  
## <a name="updating-an-interaction-and-its-layout"></a>Aggiornamento di un'interazione e del layout  
 Quando si aggiorna un'interazione, terminare sempre l'operazione aggiornando il layout con uno dei metodi seguenti:  
  
- `ISequenceDiagram.UpdateShapePositions()` regola le posizioni delle forme che recentemente sono state inserite o spostate e delle forme adiacenti.  
  
- `ISequenceDiagram.Layout([SequenceDiagramLayoutKinds])` ridisegna l'intero diagramma. È possibile usare il parametro per specificare il riposizionamento delle linee di vita, dei messaggi o di entrambi.  
  
  Ciò è particolarmente importante quando si inseriscono nuovi elementi o si spostano elementi esistenti, che occuperanno le posizioni corrette nel diagramma solo dopo avere eseguito una di queste operazioni. È sufficiente chiamare una di queste operazioni una volta alla fine di una serie di modifiche.  
  
  Per evitare di confondere l'utente che esegue un annullamento dopo il comando, usare `ILinkedUndoTransaction` per racchiudere le modifiche e le operazioni `Layout()` o `UpdateShapePositions()` finali. Ad esempio:  
  
```  
using (ILinkedUndoTransaction transaction = LinkedUndoContext.BeginTransaction("create loop"))  
{  
  Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop, messages);  
  Diagram.UpdateShapePositions();  
  transaction.Commit();  
}  
```  
  
 Per usare `ILinkedUndoTransaction`, è necessario creare questa dichiarazione nella classe:  
  
```  
[Import] ILinkedUndoContext LinkedUndoContext { get; set; }  
```  
  
 Per altre informazioni, vedere [aggiornamenti di modelli di collegamento UML tramite transazioni](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
## <a name="building-an-interaction"></a>Compilazione di un'interazione  
  
### <a name="to-create-lifelines"></a>Per creare linee di vita  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
```  
  
 Una linea di vita rappresenta un elemento collegabile, ovvero un'istanza di un tipo. Ad esempio, se l'interazione viene usata per mostrare come un componente delega i messaggi in arrivo alle parti interne, le linee di vita possono rappresentare le porte e le parti del componente:  
  
```  
foreach (IConnectableElement part in   
            component.Parts  
           .Concat<IConnectableElement>(component.OwnedPorts))  
{  
   ILifeline lifeline = interaction.CreateLifeline();  
   lifeline.Represents = part;  
}  
```  
  
 In alternativa, se l'interazione mostra un set arbitrario di oggetti, è possibile creare una proprietà o un altro `IConnectableElement` nell'interazione stessa:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
IProperty property1 = interaction.CreateProperty();  
property1.Type = model.CreateInterface();  
property1.Type.Name = "Type 1";  
lifeline.Represents = property1;  
```  
  
 Come ulteriore alternativa, è possibile impostare il nome e il tipo di una linea di vita senza collegarla a un elemento collegabile:  
  
```  
ILifeline lifeline = interaction.CreateLifeline();  
lifeline.Name = "c1";  
lifeline.SetInstanceType("Customer");  
System.Diagnostics.Debug.Assert(  
           lifeline.GetDisplayName() == "c1:Customer"  );  
```  
  
### <a name="to-create-messages"></a>Per creare messaggi  
 Per creare un messaggio, è necessario identificare i punti di inserimento sulle linee di vita di origine e di destinazione. Ad esempio:  
  
```  
interaction.CreateMessage( sourceInsertionPoint,   
                           targetInsertionPoint,   
                           MessageKind.Complete,   
                           MessageSort.ASynchCall)  
```  
  
 Per creare un messaggio con un'origine non definita o una destinazione non definita:  
  
```  
interaction.CreateLostFoundMessage(MessageKind.Found, insertionPoint);  
```  
  
 Esistono diversi messaggi che è possibile usare per identificare i punti di inserimento in tutti i punti importanti di una linea di vita:  
  
|Metodo in ILifeline|Da usare per l'inserimento in questo punto|  
|-------------------------|------------------------------------|  
|`FindInsertionPointAtTop()`|La parte iniziale della linea di vita.|  
|`FindInsertionPointAtBottom()`|La parte finale della linea di vita.|  
|`FindInsertionPointAfterMessage`<br /><br /> `(IMessage previous)`|Un punto immediatamente dopo il messaggio specificato.|  
|`FindInsertionPointAfterExecutionSpecification`<br /><br /> `(IExecutionSpecification previous)`|Il punto può essere sulla linea di vita o su un blocco di una specifica di esecuzione padre.|  
|`FindInsertionPointAfterInteractionUse`<br /><br /> `(IInteractionUse previous)`|Un punto che segue un utilizzo interazione.|  
|`FindInsertionPointAfterCombinedFragment`<br /><br /> `(ICombinedFragment previous)`|Un punto che segue un frammento combinato.|  
|`FindInsertionPoint(IExecutionSpecification block)`|La parte superiore di un blocco di esecuzione.|  
|`FindInsertionPoint(IInteractionOperand fragment)`|La parte iniziale di un operando di un frammento combinato.|  
  
 Quando si creano messaggi, evitare di definire un messaggio che intersecherebbe un altro messaggio.  
  
### <a name="to-create-combined-fragments-and-interaction-uses"></a>Per creare frammenti combinati e utilizzi interazione  
 È possibile creare frammenti combinati e utilizzi interazione specificando un punto di inserimento su ogni linea di vita che deve essere coperta dall'elemento. Evitare di specificare un set di punti che intersecherebbero un messaggio o un frammento esistente.  
  
```  
Interaction.CreateCombinedFragment(InteractionOperatorKind.Loop,   
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
Interaction.CreateInteractionUse(  
  Interaction.Lifelines.Select(lifeline => lifeline.FindInsertionPointAtTop()));  
```  
  
 È inoltre possibile creare un frammento combinato che copre un set esistente di messaggi. I messaggi devono essere tutti originati nello stesso blocco di esecuzione o nella stessa linea di vita.  
  
```  
ICombinedFragment cf = Interaction.CreateCombinedFragment(  
  InteractionOperatorKind.Loop,  
  Interaction.Lifelines.First().GetAllOutgoingMessages());  
```  
  
 Un frammento combinato viene sempre creato con un singolo operando. Per creare un nuovo operando, è necessario specificare l'operando esistente che si vuole inserire prima o dopo e se si vuole eseguire l'inserimento prima o dopo di esso:  
  
```  
// Create an additional operand before the first  
cf.CreateInteractionOperand(cf.Operands.First(), false);  
// Create an additional operand after the last:  
cf.CreateInteractionOperand(cf.Operands.Last(), true);  
```  
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
 Le forme non saranno nelle posizioni corrette se le modifiche non vengono completate con un'operazione `UpdateShapePositions()` o `Layout()`.  
  
 La maggior parte degli altri problemi sono causati da punti di inserimento non allineati che obbligheranno i nuovi messaggi o frammenti a intersecare gli altri. I sintomi possono essere la mancata esecuzione delle modifiche o la generazione di un'eccezione. L'eccezione potrebbe venire generata solo dopo l'esecuzione dell'operazione `UpdateShapePositions()` o `Layout()`.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Uml.Interactions?displayProperty=fullName>   
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definire una classe personalizzata elemento della casella degli strumenti di modellazione](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)
