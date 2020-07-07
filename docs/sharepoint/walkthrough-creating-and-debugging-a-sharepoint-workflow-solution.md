---
title: Creare & soluzione di flusso di lavoro di SharePoint
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65af3cbfc799a90d640579f8eed0e051fd5888f0
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014616"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Procedura dettagliata: creare ed eseguire il debug di una soluzione flusso di lavoro SharePoint
  In questa procedura dettagliata viene illustrato come creare un modello di flusso di lavoro sequenziale di base. Il flusso di lavoro controlla una proprietà di una raccolta documenti condivisa per determinare se un documento è stato rivisto. Se il documento è stato esaminato, il flusso di lavoro viene completato.

 Vengono illustrate le attività seguenti:

- Creazione di un progetto di flusso di lavoro sequenziale di definizione elenco di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Creazione di attività del flusso di lavoro.

- Gestione degli eventi di attività del flusso di lavoro.

> [!NOTE]
> Sebbene in questa procedura dettagliata venga utilizzato un progetto flusso di lavoro sequenziale, il processo è identico per un progetto flusso di lavoro macchina a Stati.
>
> Inoltre, il computer potrebbe mostrare nomi o percorsi diversi per alcuni degli elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Aggiungere proprietà alla raccolta documenti condivisi di SharePoint
 Per tenere traccia dello stato di revisione dei documenti nella raccolta **documenti condivisi** , si creeranno tre nuove proprietà per i documenti condivisi nel sito di SharePoint: `Status` , `Assignee` e `Review Comments` . Queste proprietà vengono definite nella raccolta **documenti condivisi** .

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Per aggiungere proprietà alla raccolta documenti condivisi di SharePoint

1. Aprire un sito di SharePoint, ad esempio http:// \<system name> /SitePages/Home.aspx, in una Web browser.

2. Sulla barra QuickLaunch scegliere **Documenticondivisi**.

3. Scegliere **libreria** nella barra multifunzione **strumenti libreria** , quindi scegliere il pulsante **Crea colonna** sulla barra multifunzione per creare una nuova colonna.

4. Denominare lo **stato del documento**di colonna, impostarne il tipo su **scelta (menu da scegliere)**, specificare le tre scelte seguenti, quindi scegliere il pulsante **OK** :

    - **Revisione necessaria**

    - **Revisione completata**

    - **Modifiche richieste**

5. Creare altre due colonne e denominarle **assegnatali** ed **esaminare i commenti**. Impostare il tipo di colonna assegnatario come una singola riga di testo e il tipo di colonna Revisione commenti come più righe di testo.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Consente di modificare i documenti senza richiedere un'estrazione
 È più semplice testare il modello di flusso di lavoro quando è possibile modificare i documenti senza doverli estrarre. Nella procedura seguente viene configurato il sito di SharePoint per abilitarlo.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Per consentire la modifica dei documenti senza estrarli

1. Sulla barra QuickLaunch scegliere il collegamento **documenti condivisi** .

2. Sulla barra multifunzione **strumenti libreria** scegliere la scheda **libreria** , quindi scegliere il pulsante **Impostazioni libreria** per visualizzare la pagina **Impostazioni raccolta documenti** .

3. Nella sezione **Impostazioni generali** scegliere il collegamento **impostazioni di controllo delle versioni** per visualizzare la pagina impostazioni di controllo delle **versioni** .

4. Verificare che l'impostazione per **Richiedi documenti da estrarre prima di poter modificare** è **No**. In caso contrario, impostarlo su **No** , quindi scegliere il pulsante **OK** .

5. Chiudere il browser.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Creazione di un progetto flusso di lavoro sequenziale di SharePoint
 Un flusso di lavoro sequenziale è un set di passaggi eseguiti in ordine fino al completamento dell'ultima attività. In questa procedura viene creato un flusso di lavoro sequenziale che verrà applicato all'elenco dei documenti condivisi. La creazione guidata flusso di lavoro consente di associare il flusso di lavoro alla definizione del sito o alla definizione dell'elenco e consente di determinare quando il flusso di lavoro verrà avviato.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Per creare un progetto di flusso di lavoro sequenziale di SharePoint

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto** per visualizzare la finestra di dialogo **nuovo progetto** .

3. Espandere il nodo **SharePoint** sotto **Visual C#** o **Visual Basic**, quindi scegliere il nodo **2010** .

4. Nel riquadro **modelli** scegliere il modello di **progetto SharePoint 2010** .

5. Nella casella **nome** immettere **MySharePointWorkflow** , quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

6. Nella pagina **specificare il sito e il livello di sicurezza per il debug** scegliere il pulsante di opzione **Distribuisci come soluzione farm** , quindi scegliere il pulsante **fine** per accettare il livello di attendibilità e il sito predefinito.

     Questo passaggio consente di impostare il livello di attendibilità della soluzione come soluzione farm, l'unica opzione disponibile per i progetti di flusso di lavoro. Per ulteriori informazioni, vedere [considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).

7. In **Esplora soluzioni**scegliere il nodo del progetto, quindi nella barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

8. In **Visual C#** o **Visual Basic**espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

9. Nel riquadro **modelli** scegliere il modello **flusso di lavoro sequenziale (solo soluzione farm)** , quindi scegliere il pulsante **Aggiungi** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

10. Nella pagina **specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito (**MySharePointWorkflow-Workflow1**). Mantieni il valore del tipo di modello di flusso di lavoro predefinito, **List Workflow**, quindi scegli il pulsante **Avanti** .

11. Per **associare automaticamente il flusso di lavoro in una sessione di debug in Visual Studio** , scegliere il pulsante **Avanti** per accettare tutte le impostazioni predefinite.

     Questo passaggio associa automaticamente il flusso di lavoro alla raccolta documenti condivisi.

12. Nella pagina **specificare le condizioni per l'avvio del flusso di lavoro** lasciare le opzioni predefinite selezionate nella sezione **come si desidera avviare il flusso di lavoro?** e scegliere il pulsante **fine** .

     Questa pagina consente di specificare all'avvio del flusso di lavoro. Per impostazione predefinita, il flusso di lavoro viene avviato quando un utente lo avvia manualmente in SharePoint o quando viene creato un elemento a cui è associato il flusso di lavoro.

## <a name="create-workflow-activities"></a>Creazione di attività del flusso di lavoro
 I flussi di lavoro contengono una o più *attività* che rappresentano le azioni da eseguire. Usare Progettazione flussi di lavoro per disporre le attività per un flusso di lavoro. In questa procedura, si aggiungeranno due attività al flusso di lavoro: HandleExternalEventActivity e OnWorkFlowItemChanged. Queste attività monitorano lo stato di revisione dei documenti nell'elenco **documenti condivisi**

#### <a name="to-create-workflow-activities"></a>Per creare attività del flusso di lavoro

1. Il flusso di lavoro deve essere visualizzato nella finestra di progettazione del flusso di lavoro. In caso contrario, aprire **Workflow1.cs** o **Workflow1. vb** in **Esplora soluzioni**.

2. Nella finestra di progettazione scegliere l'attività **onWorkflowActivated1** .

3. Nella finestra **Proprietà** immettere **onWorkflowActivated** accanto alla proprietà **richiamata** , quindi premere il tasto INVIO.

     Viene aperto l'editor di codice e viene aggiunto un metodo del gestore eventi denominato onWorkflowActivated al file di codice Workflow1.

4. Tornare alla finestra di progettazione del flusso di lavoro, aprire la casella degli strumenti e quindi espandere il nodo **Windows Workflow v 3.0** .

5. Nel nodo **Windows Workflow v 3.0** della **casella degli strumenti**eseguire uno dei seguenti set di passaggi:

    1. Aprire il menu di scelta rapida per l'attività **while** , quindi scegliere **copia**. Nella finestra di progettazione del flusso di lavoro aprire il menu di scelta rapida per la riga sotto l'attività **onWorkflowActivated1** , quindi scegliere **Incolla**.

    2. Trascinare l'attività **while** dalla **casella degli strumenti** alla finestra di progettazione del flusso di lavoro e connettere l'attività alla riga sotto l'attività **onWorkflowActivated1** .

6. Scegliere l'attività **WhileActivity1** .

7. Nella finestra **Proprietà** impostare **condizione** su codice.

8. Espandere la proprietà **Condition** , immettere **isWorkflowPending** accanto alla proprietà **condizione** figlio, quindi premere il tasto INVIO.

     Viene aperto l'editor di codice e viene aggiunto un metodo denominato isWorkflowPending al file di codice Workflow1.

9. Tornare alla finestra di progettazione del flusso di lavoro, aprire la casella degli strumenti e quindi espandere il nodo **flusso di lavoro di SharePoint** .

10. Nel nodo **flusso di lavoro SharePoint** della **casella degli strumenti**eseguire uno dei seguenti set di passaggi:

    - Aprire il menu di scelta rapida per l'attività **OnWorkflowItemChanged** , quindi scegliere **copia**. Nella finestra di progettazione del flusso di lavoro aprire il menu di scelta rapida per la riga all'interno dell'attività **WhileActivity1** , quindi scegliere **Incolla**.

    - Trascinare l'attività **OnWorkflowItemChanged** dalla **casella degli strumenti** alla finestra di progettazione del flusso di lavoro e connettere l'attività alla riga nell'attività **WhileActivity1** .

11. Scegliere l'attività **onWorkflowItemChanged1** .

12. Nella finestra **Proprietà** impostare le proprietà come illustrato nella tabella seguente.

    |Proprietà|valore|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**Chiamata**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>Gestisci eventi attività
 Infine, controllare lo stato del documento da ogni attività. Se il documento è stato rivisto, il flusso di lavoro è terminato.

#### <a name="to-handle-activity-events"></a>Per gestire gli eventi di attività

1. In *Workflow1.cs* o *Workflow1. vb*aggiungere il campo seguente all'inizio della `Workflow1` classe. Questo campo viene utilizzato in un'attività per determinare se il flusso di lavoro è terminato.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Aggiungere il metodo seguente alla classe `Workflow1`. Questo metodo controlla il valore della `Document Status` proprietà dell'elenco documenti per determinare se il documento è stato rivisto. Se la `Document Status` proprietà è impostata su `Review Complete` , il `checkStatus` metodo imposta il `workflowPending` campo su **false** per indicare che il flusso di lavoro è pronto per il completamento.

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

3. Aggiungere il codice seguente ai `onWorkflowActivated` metodi e `onWorkflowItemChanged` per chiamare il `checkStatus` metodo. Quando il flusso di lavoro viene avviato, il `onWorkflowActivated` metodo chiama il `checkStatus` metodo per determinare se il documento è già stato esaminato. Se non è stato esaminato, il flusso di lavoro continua. Quando il documento viene salvato, il `onWorkflowItemChanged` metodo chiama `checkStatus` di nuovo il metodo per determinare se il documento è stato rivisto. Mentre il `workflowPending` campo è impostato su **true**, il flusso di lavoro continua a essere eseguito.

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

4. Aggiungere il codice seguente al `isWorkflowPending` metodo per verificare lo stato della `workflowPending` Proprietà. Ogni volta che il documento viene salvato, l'attività **WhileActivity1** chiama il `isWorkflowPending` metodo. Questo metodo esamina la <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> proprietà dell' <xref:System.Workflow.Activities.ConditionalEventArgs> oggetto per determinare se l'attività **WhileActivity1** deve continuare o essere terminata. Se la proprietà è impostata su **true**, l'attività continua. In caso contrario, l'attività termina e il flusso di lavoro viene completato.

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

5. Salvare il progetto.

## <a name="test-the-sharepoint-workflow-template"></a>Testare il modello di flusso di lavoro di SharePoint
 Quando si avvia il debugger, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] distribuisce il modello di flusso di lavoro nel server SharePoint e associa il flusso di lavoro all'elenco dei **documenti condivisi** . Per testare il flusso di lavoro, avviare un'istanza del flusso di lavoro da un documento nell'elenco **documenti condivisi** .

#### <a name="to-test-the-sharepoint-workflow-template"></a>Per testare il modello di flusso di lavoro di SharePoint

1. In *Workflow1.cs* o *Workflow1. vb*, impostare un punto di interruzione accanto al metodo **onWorkflowActivated** .

2. Premere il tasto **F5** per compilare ed eseguire la soluzione.

     Viene visualizzato il sito di SharePoint.

3. Nel riquadro di spostamento in SharePoint scegliere il collegamento **documenti condivisi** .

4. Nella pagina **documenti condivisi** scegliere il collegamento **documenti** nella scheda **strumenti libreria** , quindi scegliere il pulsante **Carica documento** .

5. Nella finestra di dialogo **Carica documento** scegliere il pulsante **Sfoglia** , scegliere un file di documento, scegliere il pulsante **Apri** , quindi scegliere il pulsante **OK** .

     Il documento selezionato verrà caricato nell'elenco **documenti condivisi** e verrà avviato il flusso di lavoro.

6. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , verificare che il debugger venga arrestato in corrispondenza del punto di interruzione accanto al `onWorkflowActivated` metodo.

7. Premere il tasto **F5** per continuare l'esecuzione.

8. È possibile modificare le impostazioni per il documento, ma lasciare i valori predefiniti per ora scegliendo il pulsante **Salva** .

     Verrà ripristinata la pagina **documenti condivisi** del sito Web di SharePoint predefinito.

9. Nella pagina **documenti condivisi** verificare che il valore sotto la colonna **MySharePointWorkflow-Workflow1** sia impostato su **in corso**. Indica che il flusso di lavoro è in corso e che il documento è in attesa di revisione.

10. Nella pagina **documenti condivisi** scegliere il documento, scegliere la freccia visualizzata, quindi scegliere la voce di menu **modifica proprietà** .

11. Impostare **stato documento** su **Verifica completata**, quindi scegliere il pulsante **Salva** .

     Verrà ripristinata la pagina **documenti condivisi** del sito Web di SharePoint predefinito.

12. Nella pagina **documenti condivisi** verificare che il valore sotto la colonna **stato documento** sia impostato su **Revisione completata**. Aggiornare la pagina **documenti condivisi** e verificare che il valore sotto la colonna **MySharePointWorkflow-Workflow1** sia impostato su **completato**. Indica che il flusso di lavoro è terminato e che il documento è stato rivisto.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni su come creare modelli di flusso di lavoro, vedere questi argomenti:

- Per ulteriori informazioni sulle attività del flusso di lavoro di SharePoint, vedere [attività flusso di lavoro per SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

- Per ulteriori informazioni sulle attività di Windows Workflow Foundation, vedere [spazio dei nomi System. Workflow. Activities](/dotnet/api/system.windows.media.color).

## <a name="see-also"></a>Vedere anche
- [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
