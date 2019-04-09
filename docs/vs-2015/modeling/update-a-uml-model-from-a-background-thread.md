---
title: Aggiornare un modello UML da un thread in background | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd0707ec7838ffb2dcebc8a176c79810f2614133
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969371"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Aggiornare un modello UML da un thread in background
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A volte può essere utile apportare modifiche a un modello in un thread in background. Ad esempio, se si stanno caricando informazioni da una risorsa esterna lenta, è possibile usare un thread in background per controllare gli aggiornamenti. In questo modo, l'utente può visualizzare ogni aggiornamento non appena si verifica.  
  
 È tuttavia necessario tenere presente che l'archivio UML non è thread-safe. Ecco alcune precauzioni importanti:  
  
-   Ogni aggiornamento a un modello o a un diagramma deve essere eseguito nel thread dell'interfaccia utente.  Il thread in background deve usare <xref:System.Windows.Forms.Control.Invoke%2A> o `Dispatcher.`<xref:System.Windows.Threading.Dispatcher.Invoke%2A> per fare in modo che il thread dell'interfaccia utente esegua gli aggiornamenti effettivi.  
  
-   Se si raggruppa una serie di modifiche in un'unica transazione, è consigliabile impedire all'utente di modificare il modello mentre la transazione è in corso. In caso contrario, qualsiasi modifica apportata dall'utente diventerà parte della stessa transazione. È possibile impedire all'utente di apportare modifiche visualizzando una finestra di dialogo modale. Eventualmente, è possibile visualizzare un pulsante Annulla nella finestra di dialogo. L'utente può visualizzare le modifiche man mano che si verificano.  
  
## <a name="example"></a>Esempio  
 Questo esempio usa un thread in background per apportare diverse modifiche a un modello. Viene usata una finestra di dialogo per escludere l'utente mentre il thread è in esecuzione. In questo semplice esempio non viene fornito un pulsante Annulla nella finestra di dialogo. Questa funzionalità può tuttavia essere aggiunta facilmente.  
  
#### <a name="to-run-the-example"></a>Per eseguire l'esempio  
  
1. Creare un gestore comando in un progetto C#, come descritto in [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
2. Verificare che il progetto includa riferimenti a questi assembly:  
  
   -   Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.[versione]  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versione]  
  
   -   Microsoft.VisualStudio.Uml.Interfaces  
  
   -   System.ComponentModel.Composition  
  
   -   System.Windows.Forms  
  
3. Aggiungere al progetto un form di Windows denominato **ProgressForm**. Dovrà visualizzare un messaggio che indica che sono in corso gli aggiornamenti. Non è necessario che includa altri controlli.  
  
4. Aggiungere un file C# contenente il codice illustrato dopo il passaggio 7.  
  
5. Compilare ed eseguire il progetto.  
  
    Verrà avviata una nuova istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in modalità sperimentale.  
  
6. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] creare o aprire un diagramma classi UML.  
  
7. Fare doppio clic in qualsiasi punto nel diagramma classi UML e quindi fare clic su **aggiunta di diverse classi UML**.  
  
   Nel diagramma verranno visualizzate diverse nuove caselle delle classi, una dopo l'altra a intervalli di mezzo secondo.  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.ComponentModel.Composition;  
using System.Threading;  
using System.Windows.Forms;  
  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.Uml.Classes;  
  
namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class UmlClassAdderCommand : ICommandExtension  
  {  
  
    [Import]  
    IDiagramContext context { get; set; }  
  
    [Import]  
    ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called when the user runs the command.  
    public void Execute(IMenuCommand command)  
    {  
      // The form that will exclude the user.  
      ProgressForm form = new ProgressForm();  
  
      // System.ComponentModel.BackgroundWorker is a  
      // convenient way to run a background thread.  
      BackgroundWorker worker = new BackgroundWorker();  
      worker.WorkerSupportsCancellation = true;  
  
      worker.DoWork += delegate(object sender, DoWorkEventArgs args)  
      {  
        // This block will be executed in a background thread.  
  
        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;  
        IModelStore store = diagram.ModelStore;  
        const int CLASSES_TO_CREATE = 15;  
  
        // Group all the changes together.  
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))  
        {  
          for (int i = 1; i < CLASSES_TO_CREATE; i++)  
          {  
            if (worker.CancellationPending)   
               return; // No commit - undo all.  
  
            // Create model elements using the UI thread by using  
            // the Invoke method on the progress form. Always   
            // modify the model and diagrams from a UI thread.  
            form.Invoke((MethodInvoker)(delegate  
            {  
              IClass newClass = store.Root.CreateClass();  
              newClass.Name = string.Format("NewClass{0}", i);  
              diagram.Display(newClass);  
            }));  
  
            // Sleep briefly so that we can watch the updates.  
            Thread.Sleep(500);  
          }  
  
          // Commit the transaction or it will be rolled back.  
          transaction.Commit();  
        }  
      };  
  
      // Close the form when the thread completes.  
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)  
      {  
        form.Close();  
      };  
  
      // Start the thread before showing the modal progress dialog.  
      worker.RunWorkerAsync();  
  
      // Show the form modally, parented on VS.  
      // Prevents the user from making changes while in progress.  
      form.ShowDialog();  
    }  
  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
  
    public string Text  
    {  
      get { return "Add several classes"; }  
    }  
  }  
}  
```  
  
#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Per consentire all'utente di annullare il thread nell'esempio  
  
1.  Aggiungere un pulsante Annulla alla finestra di stato.  
  
2.  Aggiungere il codice seguente alla finestra di stato:  
  
     `public event MethodInvoker Cancel;`  
  
     `private void CancelButton_Click(object sender, EventArgs e)`  
  
     `{`  
  
     `Cancel();`  
  
     `}`  
  
3.  Nel metodo Execute() inserire questa riga dopo la costruzione del form:  
  
     `form.Cancel += delegate() { worker.CancelAsync(); };`  
  
### <a name="other-methods-of-accessing-the-ui-thread"></a>Altri metodi di accesso al thread dell'interfaccia utente  
 Se non si vuole creare una finestra di dialogo, è possibile accedere al controllo che visualizza il diagramma:  
  
 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`  
  
 Per eseguire operazioni nel thread dell'interfaccia utente, è possibile usare `uiThreadHolder.Invoke()`.  
  
## <a name="see-also"></a>Vedere anche  
 [Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definire un gestore modelli in un diagramma di modellazione](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
