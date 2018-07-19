---
title: 'Procedura dettagliata: Creazione e debug di una soluzione del flusso di lavoro di SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6035b8ceb693434e2e8bc652b91ee31ceb3ebe02
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118939"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Procedura dettagliata: Creare ed eseguire il debug di una soluzione del flusso di lavoro di SharePoint
  Questa procedura dettagliata viene illustrato come creare un modello di base del flusso di lavoro sequenziale. Il flusso di lavoro controlla una proprietà di una raccolta documenti condivisa per determinare se un documento è stato rivisto. Se il documento è stato rivisto, il flusso di lavoro termina.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un progetto di flusso di lavoro sequenziale di definizione elenco di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Creazione di attività del flusso di lavoro.  
  
-   La gestione degli eventi di attività del flusso di lavoro.  
  
> [!NOTE]  
>  Sebbene questa procedura dettagliata Usa un progetto di flusso di lavoro sequenziale, il processo è identico per un progetto flusso di lavoro macchina a stati.  
>   
>  Inoltre, il computer potrebbe mostrare nomi diversi o percorsi di alcuni utente di Visual Studio gli elementi dell'interfaccia nelle istruzioni seguenti. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint. Per altre informazioni, vedere [i requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Aggiungere proprietà alla raccolta di documenti condivisi di SharePoint
 Tenere traccia dello stato di revisione di documenti nel **documenti condivisi** libreria, si creerà tre nuove proprietà per i documenti condivisi nel sito SharePoint: `Status`, `Assignee`, e `Review Comments`. Tali proprietà in sono definite le **documenti condivisi** libreria.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Per aggiungere proprietà a condivisi di SharePoint raccolta documenti  
  
1.  Aprire un sito di SharePoint, ad esempio http://\<nome sistema > / /SitePages/Home.aspx, in un Web browser.  
  
2.  Nella barra Avvio veloce, scegliere **SharedDocuments**.  
  
3.  Scegliere **Library** nel **Strumenti raccolta** della barra multifunzione e quindi scegliere il **Crea colonna** pulsante della barra multifunzione per creare una nuova colonna.  
  
4.  Assegnare un nome di colonna **Document Status**, impostarne il tipo **scelta (menu)** specificare tre opzioni seguenti e quindi scegliere il **OK** pulsante:  
  
    -   **Verifica necessaria**  
  
    -   **Revisione completata**  
  
    -   **Modifiche richieste**  
  
5.  Creare altre due colonne e denominarli **assegnatario** e **commenti alla revisione**. Impostare il tipo di colonna Assignee come una singola riga di testo e il tipo di colonna commenti alla revisione più righe di testo.  
  
## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Abilitare i documenti da modificare senza richiedere il check-out
 È più semplice testare il modello di flusso di lavoro quando è possibile modificare i documenti senza la necessità di estrarli. Nella procedura successiva, si configura il sito di SharePoint per abilitare questa funzionalità.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Per abilitare i documenti da modificare senza estrarli  
  
1.  Nella barra Avvio veloce scegliere il **documenti condivisi** collegamento.  
  
2.  Nel **Strumenti raccolta** sulla barra multifunzione, scegliere il **libreria** scheda e quindi scegliere il **impostazioni libreria** pulsante per visualizzare il **leimpostazionidellaraccoltadocumenti** pagina.  
  
3.  Nel **impostazioni generali** keychains il **le impostazioni di controllo delle versioni** link per visualizzare il **impostazioni di controllo delle versioni** pagina.  
  
4.  Verificare che l'impostazione **richiedono i documenti da estrarre prima che possano essere modificati** viene **No**. In caso contrario, modificarla in modo che **No** e quindi scegliere il **OK** pulsante.  
  
5.  Chiudere il browser.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Creare un progetto di flusso di lavoro sequenziale di SharePoint
 Flusso di lavoro sequenza è una serie di passaggi eseguiti in ordine fino al termine dell'ultima attività. In questa procedura, viene creato un flusso di lavoro sequenza che verrà applicate al nostro elenco di documenti condivisi. La procedura guidata del flusso di lavoro consente di associare il flusso di lavoro con la definizione di sito o la definizione di elenco e consente di determinare quando verrà avviato il flusso di lavoro.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Per creare un progetto di flusso di lavoro sequenziale di SharePoint  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu, scegliere **File** > **New** > **progetto** per visualizzare il **nuovo progetto** nella finestra di dialogo.  
  
3.  Espandere la **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.  
  
4.  Nel **modelli** riquadro, scegliere il **progetto SharePoint 2010** modello.  
  
5.  Nel **Name** casella, immettere **MySharePointWorkflow** e quindi scegliere il **OK** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzata.  
  
6.  Nel **specificare il livello di sito e la sicurezza per il debug** pagina, scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante per accettare il sito di livello e predefinito trust.  
  
     Questo passaggio consente di impostare il livello di attendibilità per la soluzione come soluzione farm, l'unica opzione disponibile per i progetti di flusso di lavoro. Per altre informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Nelle **Esplora soluzioni**, scegliere il nodo del progetto e quindi nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento**.  
  
8.  In presenza di una **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.  
  
9. Nel **modelli** riquadro, scegliere il **flusso di lavoro sequenziale (solo soluzione Farm)** modello e quindi scegliere il **Add** pulsante.  
  
     Il **Personalizzazione guidata SharePoint** viene visualizzata.  
  
10. Nel **specificare il nome del flusso di lavoro per il debug** pagina, accettare il nome predefinito (**MySharePointWorkflow - Workflow1**). Mantenere il valore a tipo di modello del flusso di lavoro predefinito, **flusso di lavoro elenco**, quindi scegliere il **successivo** pulsante.  
  
11. Nel **preferisci Visual Studio per associare automaticamente il flusso di lavoro in una sessione di debug?** pagina, scegliere il **successivo** pulsante per accettare tutte le impostazioni predefinite.  
  
     Questo passaggio associa automaticamente il flusso di lavoro con la libreria di documenti condivisi.  
  
12. Nel **specificano le condizioni per la modalità di avvio del flusso di lavoro** pagina, lasciare selezionate nelle opzioni predefinite il **modo in cui si desidera avviare il flusso di lavoro?** sezione e scegliere il **fine** pulsante.  
  
     Questa pagina consente di specificare quando viene avviato il flusso di lavoro. Per impostazione predefinita, il flusso di lavoro si avvia quando un utente avvia manualmente in SharePoint o quando viene creato un elemento a cui è associato il flusso di lavoro.  
  
## <a name="create-workflow-activities"></a>Creare le attività del flusso di lavoro
 I flussi di lavoro contengono uno o più *attività* che rappresentano le azioni da eseguire. Usare la finestra di progettazione del flusso di lavoro per organizzare le attività per un flusso di lavoro. In questa procedura, si aggiungeranno due attività nel flusso di lavoro: HandleExternalEvent e OnWorkFlowItemChanged. Queste attività consentono di monitorare lo stato di revisione di documenti nel **documenti condivisi** elenco  
  
#### <a name="to-create-workflow-activities"></a>Per creare le attività del flusso di lavoro  
  
1.  Il flusso di lavoro deve essere visualizzato nella finestra di progettazione del flusso di lavoro. In caso contrario, aprire **Workflow1.cs** oppure **Workflow1.vb** nelle **Esplora**.  
  
2.  Nella finestra di progettazione, scegliere il **OnWorkflowActivated1** attività.  
  
3.  Nel **delle proprietà** finestra, immettere **onWorkflowActivated** accanto al **Invoked** proprietà e quindi premere INVIO.  
  
     Si apre l'Editor di codice e un metodo del gestore eventi denominato onWorkflowActivated viene aggiunto al file di codice Workflow1.  
  
4.  Tornare alla finestra di progettazione del flusso di lavoro, aprire la casella degli strumenti e quindi espandere la **Windows Workflow v3.0** nodo.  
  
5.  Nel **Windows Workflow v3.0** nodo delle **della casella degli strumenti**, effettuare uno dei seguenti set di passaggi:  
  
    1.  Aprire il menu di scelta rapida per il **mentre** attività, quindi scegliere **copia**. Nella finestra di progettazione del flusso di lavoro, aprire il menu di scelta rapida per la riga sotto la **onWorkflowActivated1** attività, quindi scegliere **Incolla**.  
  
    2.  Trascinare il **mentre** attività dalle **della casella degli strumenti** alla finestra di progettazione del flusso di lavoro e connettere l'attività per la riga sotto il **onWorkflowActivated1** attività.  
  
6.  Scegliere il **WhileActivity1** attività.  
  
7.  Nel **delle proprietà** impostare nella finestra **condizione** alla condizione di codice.  
  
8.  Espandere la **Condition** proprietà, immettere **isWorkflowPending** accanto all'elemento figlio **condizione** proprietà e quindi premere INVIO.  
  
     Si apre l'Editor di codice e un metodo denominato isWorkflowPending viene aggiunto al file di codice Workflow1.  
  
9. Tornare alla finestra di progettazione del flusso di lavoro, aprire la casella degli strumenti e quindi espandere la **flusso di lavoro SharePoint** nodo.  
  
10. Nel **flusso di lavoro SharePoint** nodo delle **della casella degli strumenti**, effettuare uno dei seguenti set di passaggi:  
  
    -   Aprire il menu di scelta rapida per il **OnWorkflowItemChanged** attività, quindi scegliere **copia**. Nella finestra di progettazione del flusso di lavoro, aprire il menu di scelta rapida per la riga all'interno di **whileActivity1** attività, quindi scegliere **Incolla**.  
  
    -   Trascinare il **OnWorkflowItemChanged** attività dal **della casella degli strumenti** alla finestra di progettazione del flusso di lavoro e connettere l'attività alla riga all'interno di **whileActivity1** attività.  
  
11. Scegliere il **onWorkflowItemChanged1** attività.  
  
12. Nel **proprietà** finestra, impostare le proprietà come illustrato nella tabella seguente.  
  
    |Proprietà|Valore|  
    |--------------|-----------|  
    |**elemento correlationToken**|**workflowToken**|  
    |**Richiamato**|**onWorkflowItemChanged**|  
  
## <a name="handle-activity-events"></a>Gestire gli eventi di attività
 Infine, controllare lo stato del documento da ogni attività. Se il documento è stato rivisto, il flusso di lavoro è stata completata.  
  
#### <a name="to-handle-activity-events"></a>Per gestire gli eventi di attività  
  
1.  Nelle *Workflow1.cs* oppure *Workflow1.vb*, aggiungere il campo seguente all'inizio del `Workflow1` classe. Questo campo viene usato in un'attività per determinare se il flusso di lavoro è stata completata.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Aggiungere il metodo seguente alla classe `Workflow1`. Questo metodo controlla il valore della `Document Status` proprietà dell'elenco dei documenti per determinare se il documento è stato rivisto. Se il `Document Status` è impostata su `Review Complete`, il `checkStatus` metodo imposta la `workflowPending` campo **false** per indicare che il flusso di lavoro è pronto essere terminato.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Aggiungere il codice seguente per il `onWorkflowActivated` e `onWorkflowItemChanged` metodi per chiamare il `checkStatus` (metodo). Quando viene avviato il flusso di lavoro, il `onWorkflowActivated` chiamate al metodo il `checkStatus` metodo per determinare se il documento è già stato rivisto. Se si è non stato rivisto, il flusso di lavoro continua. Quando il documento viene salvato, la `onWorkflowItemChanged` chiamate al metodo il `checkStatus` metodo nuovamente per determinare se il documento è stato rivisto. Mentre il `workflowPending` campo è impostato su **true**, il flusso di lavoro rimane in esecuzione.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Aggiungere il codice seguente per il `isWorkflowPending` metodo per controllare lo stato del `workflowPending` proprietà. Ogni volta che il documento viene salvato, la **whileActivity1** attività chiama la `isWorkflowPending` (metodo). Questo metodo esamina il <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> proprietà del <xref:System.Workflow.Activities.ConditionalEventArgs> oggetto per determinare se il **WhileActivity1** deve continuare o di fine attività. Se la proprietà è impostata su **true**, l'attività continua. In caso contrario, l'attività viene completata e completa il flusso di lavoro.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Salvare il progetto.  
  
## <a name="test-the-sharepoint-workflow-template"></a>Testare il modello di flusso di lavoro di SharePoint
 Quando si avvia il debugger [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] distribuisce il modello di flusso di lavoro nel server SharePoint e associa il flusso di lavoro con il **documenti condivisi** elenco. Per testare il flusso di lavoro, avviare un'istanza del flusso di lavoro da un documento di **documenti condivisi** elenco.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>Per testare il modello di flusso di lavoro di SharePoint  
  
1.  Nelle *Workflow1.cs* oppure *Workflow1.vb*, impostare un punto di interruzione accanto al **onWorkflowActivated** (metodo).  
  
2.  Scegliere il **F5** chiave per compilare ed eseguire la soluzione.  
  
     Viene visualizzato il sito di SharePoint.  
  
3.  Nel riquadro di spostamento in SharePoint, scegliere il **documenti condivisi** collegamento.  
  
4.  Nel **documenti condivisi** pagina, scegliere il **documenti** sul collegamento di **Strumenti raccolta** scheda e quindi scegliere il **Carica documento** pulsante .  
  
5.  Nel **Carica documento** finestra di dialogo scegliere la **Sfoglia** pulsante scegliere qualsiasi file di documento, scegliere il **Open** pulsante e quindi scegliere il **OK** pulsante.  
  
     Ciò consente di caricare il documento selezionato nel **documenti condivisi** elencare e avvia il flusso di lavoro.  
  
6.  Nelle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], verificare che il debugger si arresta nel punto di interruzione accanto al `onWorkflowActivated` (metodo).  
  
7.  Scegliere il **F5** un tasto per continuare l'esecuzione.  
  
8.  È possibile modificare le impostazioni per il documento, ma lasciarli i valori predefiniti per il momento, scegliere il **salvare** pulsante.  
  
     In questo modo verrà nuovamente visualizzato il **documenti condivisi** pagina del sito Web SharePoint predefinita.  
  
9. Nel **documenti condivisi** verificare che il valore di sotto il **MySharePointWorkflow - Workflow1** colonna è impostata su **In corso**. Ciò indica che il flusso di lavoro è in corso e che il documento è in attesa di revisione.  
  
10. Nel **documenti condivisi** pagina, scegliere il documento, scegliere la freccia visualizzata e quindi sceglie il **Modifica proprietà** voce di menu.  
  
11. Impostare **Document Status** al **Review Complete**e quindi scegliere il **Salva** pulsante.  
  
     In questo modo verrà nuovamente visualizzato il **documenti condivisi** pagina del sito Web SharePoint predefinita.  
  
12. Nel **documenti condivisi** verificare che il valore di sotto il **Document Status** colonna è impostata su **Review Complete**. Aggiorna il **documenti condivisi** pagina e verificare che il valore di sotto il **MySharePointWorkflow - Workflow1** colonna è impostata su **Completed**. Ciò indica che flusso di lavoro viene completato e che il documento è stato rivisto.  
  
## <a name="next-steps"></a>Passaggi successivi
 Altre informazioni su come creare modelli di flusso di lavoro vedere gli argomenti seguenti:  
  
-   Per altre informazioni sulle attività del flusso di lavoro di SharePoint, vedere [attività di flusso di lavoro per SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Per altre informazioni sulle attività di Windows Workflow Foundation, vedere [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Vedere anche
 [Creare soluzioni di flusso di lavoro di SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Progetto SharePoint e i modelli di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Compilare ed eseguire il debug di soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
