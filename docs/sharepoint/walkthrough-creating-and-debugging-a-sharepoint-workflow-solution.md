---
title: Creare una & di debug SharePoint flusso di lavoro
description: In questa procedura dettagliata creare ed eseguire il debug di una soluzione SharePoint flusso di lavoro. Creare un modello di flusso di lavoro sequenziale di base. Creare attività del flusso di lavoro e gestire gli eventi.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e96987734a3414f0e55f75fb221124de79573acd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115486"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Procedura dettagliata: Creare ed eseguire il debug di una soluzione SharePoint flusso di lavoro
  Questa procedura dettagliata illustra come creare un modello di flusso di lavoro sequenziale di base. Il flusso di lavoro controlla una proprietà di una raccolta documenti condivisa per determinare se un documento è stato esaminato. Se il documento è stato esaminato, il flusso di lavoro viene completato.

 Vengono illustrate le attività seguenti:

- Creazione di un SharePoint di flusso di lavoro sequenziale di definizione dell'elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Creazione di attività del flusso di lavoro.

- Gestione degli eventi dell'attività del flusso di lavoro.

> [!NOTE]
> Anche se questa procedura dettagliata usa un progetto flusso di lavoro sequenziale, il processo è identico per un progetto flusso di lavoro macchina a stati.
>
> Inoltre, il computer potrebbe visualizzare nomi o percorsi diversi per alcuni Visual Studio dell'interfaccia utente nelle istruzioni seguenti. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di Microsoft Windows e SharePoint.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Aggiungere proprietà alla raccolta SharePoint documenti condivisi
 Per tenere traccia dello stato di revisione dei documenti nella raccolta Documenti **condivisi,** verranno create tre nuove proprietà per i documenti condivisi nel sito SharePoint: `Status` , e `Assignee` `Review Comments` . Queste proprietà vengono definite nella **raccolta Documenti** condivisi.

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Per aggiungere proprietà alla raccolta SharePoint documenti condivisi

1. Aprire un SharePoint, ad esempio http:// \<system name> /SitePages/Home.aspx, in un Web browser.

2. Nella barra Avvio rapido scegliere **SharedDocuments.**

3. Scegliere **Libreria** sulla barra **multifunzione Strumenti libreria** e quindi fare clic sul pulsante **Crea** colonna sulla barra multifunzione per creare una nuova colonna.

4. Assegnare alla colonna il nome **Stato** documento, impostarne il tipo su **Scelta (menu** tra cui scegliere), specificare le tre opzioni seguenti e quindi scegliere **OK:**

    - **Revisione necessaria**

    - **Revisione completata**

    - **Modifiche richieste**

5. Creare altre due colonne e assegnarle il nome **Assignee** **and Review Comments**. Impostare il tipo di colonna Assegnatare come una singola riga di testo e il tipo di colonna Rivedi commenti come più righe di testo.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Abilitare la modifica dei documenti senza richiedere un'estrazione
 È più semplice testare il modello di flusso di lavoro quando è possibile modificare i documenti senza doverli estrarre. Nella procedura successiva si configura il sito SharePoint per abilitarlo.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Per abilitare la modifica dei documenti senza estrazione

1. Nella barra Avvio rapido scegliere il **collegamento Documenti** condivisi.

2. Nella barra multifunzione **Strumenti raccolta** scegliere la **scheda** Raccolta e quindi scegliere il pulsante Raccolta Impostazioni per visualizzare la pagina Raccolta **Impostazioni** documento. 

3. Nella sezione **Impostazioni** generale scegliere il collegamento Controllo **Impostazioni** per visualizzare la pagina Controllo **Impostazioni** controllo delle versioni.

4. Verificare che l'impostazione per Richiedi l'estrazione dei documenti prima **che possano essere modificati** sia **No**. In caso contrario, impostarlo su **No** e quindi scegliere **OK.**

5. Chiudere il browser.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Creare un progetto SharePoint flusso di lavoro sequenziale
 Un flusso di lavoro sequenziale è un set di passaggi che viene eseguito nell'ordine fino al completamento dell'ultima attività. In questa procedura viene creato un flusso di lavoro sequenziale che verrà applicato all'elenco Documenti condivisi. La procedura guidata del flusso di lavoro consente di associare il flusso di lavoro alla definizione del sito o all'elenco e consente di determinare quando il flusso di lavoro verrà avviato.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Per creare un progetto SharePoint flusso di lavoro sequenziale

1. Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Nella barra dei menu scegliere **File** nuovo Project per visualizzare la finestra  >    >   di **dialogo Project** nuova cartella.

3. Espandere il **SharePoint** in **Visual C#** o **Visual Basic** e quindi scegliere il **nodo 2010.**

4. Nel riquadro **Modelli** scegliere il modello SharePoint **2010 Project** 2010.

5. Nella casella **Nome** immettere **MySharePointWorkflow** e quindi scegliere **OK.**

     Verrà **SharePoint personalizzazione guidata.**

6. Nella pagina **Specificare il sito e** il livello di sicurezza per il debug  scegliere il pulsante di opzione Distribuisci come soluzione **farm** e quindi scegliere il pulsante Fine per accettare il livello di attendibilità e il sito predefinito.

     Questo passaggio imposta il livello di attendibilità per la soluzione come soluzione farm, l'unica opzione disponibile per i progetti flusso di lavoro. Per altre informazioni, vedere [Considerazioni sulle soluzioni in modalità sandbox.](../sharepoint/sandboxed-solution-considerations.md)

7. In **Esplora soluzioni** scegliere il nodo del progetto e quindi nella barra dei menu scegliere Project  >  **Aggiungi nuovo elemento**.

8. In **Visual C#** o **Visual Basic** espandere  il nodo SharePoint e quindi scegliere il **nodo 2010.**

9. Nel riquadro **Modelli** scegliere il modello Flusso di **lavoro sequenziale (solo** soluzione farm) e quindi scegliere **il pulsante** Aggiungi.

     Verrà **SharePoint personalizzazione guidata.**

10. Nella pagina **Specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito (**MySharePointWorkflow - Workflow1**). Mantenere il valore predefinito del tipo di modello di flusso di lavoro, **Elenca flusso di** lavoro , quindi scegliere il **pulsante** Avanti.

11. Nella pagina **Si desidera Visual Studio associare** automaticamente il flusso di lavoro in una sessione di debug? scegliere il **pulsante** Avanti per accettare tutte le impostazioni predefinite.

     Questo passaggio associa automaticamente il flusso di lavoro alla raccolta Documenti condivisi.

12. Nella pagina **Specificare le condizioni per** l'avvio del flusso di lavoro lasciare selezionate le opzioni predefinite nella sezione Come si vuole avviare il flusso di **lavoro?** e scegliere **il pulsante** Fine.

     Questa pagina consente di specificare l'avvio del flusso di lavoro. Per impostazione predefinita, il flusso di lavoro viene avviato quando un utente lo avvia manualmente SharePoint o quando viene creato un elemento a cui è associato il flusso di lavoro.

## <a name="create-workflow-activities"></a>Creare attività del flusso di lavoro
 I flussi di lavoro contengono una *o più attività* che rappresentano le azioni da eseguire. Usare la finestra di progettazione del flusso di lavoro per disporre le attività per un flusso di lavoro. In questa procedura si aggiungeranno due attività al flusso di lavoro: HandleExternalEventActivity e OnWorkFlowItemChanged. Queste attività monitorano lo stato di revisione dei documenti **nell'elenco Documenti** condivisi

#### <a name="to-create-workflow-activities"></a>Per creare attività del flusso di lavoro

1. Il flusso di lavoro deve essere visualizzato nella finestra di progettazione del flusso di lavoro. In caso contrario, aprire **Workflow1.cs** o **Workflow1.vb** **in** Esplora soluzioni .

2. Nella finestra di progettazione scegliere **l'attività OnWorkflowActivated1.**

3. Nella finestra **Proprietà** immettere **onWorkflowActivated** accanto alla **proprietà Invoked** e quindi premere INVIO.

     Verrà aperto l'editor di codice e al file di codice Workflow1 verrà aggiunto un metodo del gestore eventi denominato onWorkflowActivated.

4. Tornare alla finestra di progettazione del flusso di lavoro, aprire la casella degli strumenti e quindi espandere il **Windows flusso di lavoro v3.0.**

5. Nel nodo Windows flusso di lavoro **v3.0 della** **casella** degli strumenti eseguire uno dei seguenti set di passaggi:

    1. Aprire il menu di scelta rapida per **l'attività While** e quindi scegliere **Copia**. Nella finestra di progettazione del flusso di lavoro aprire il menu di scelta rapida per la riga **nell'attività onWorkflowActivated1** e quindi scegliere **Incolla**.

    2. Trascinare **l'attività While** dalla Casella **degli** strumenti alla finestra di progettazione del flusso di lavoro e connettere l'attività alla riga sotto l'attività **onWorkflowActivated1.**

6. Scegliere **l'attività WhileActivity1.**

7. Nella finestra **Proprietà** impostare **Condizione** su Condizione codice.

8. Espandere la **proprietà Condition,** immettere **isWorkflowPending** accanto alla proprietà **Condition** figlio e quindi premere INVIO.

     Viene aperto l'editor di codice e al file di codice Workflow1 viene aggiunto un metodo denominato isWorkflowPending.

9. Tornare alla finestra di progettazione del flusso di lavoro, aprire la casella degli strumenti e quindi espandere il **SharePoint flusso di lavoro.**

10. Nel nodo **SharePoint flusso di** lavoro della casella degli **strumenti** eseguire uno dei seguenti set di passaggi:

    - Aprire il menu di scelta rapida per **l'attività OnWorkflowItemChanged** e quindi scegliere **Copia**. Nella finestra di progettazione del flusso di lavoro aprire il menu di scelta rapida per la riga all'interno dell'attività **whileActivity1** e quindi scegliere **Incolla**.

    - Trascinare **l'attività OnWorkflowItemChanged** dalla **Casella** degli strumenti alla finestra di progettazione del flusso di lavoro e connettere l'attività alla riga all'interno dell'attività **whileActivity1.**

11. Scegliere **l'attività onWorkflowItemChanged1.**

12. Nella finestra **Proprietà** impostare le proprietà come illustrato nella tabella seguente.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Correlationtoken**|**workflowToken**|
    |**Chiamata**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>Gestire gli eventi di attività
 Controllare infine lo stato del documento da ogni attività. Se il documento è stato esaminato, il flusso di lavoro è terminato.

#### <a name="to-handle-activity-events"></a>Per gestire gli eventi di attività

1. In *Workflow1.cs* o *Workflow1.vb* aggiungere il campo seguente all'inizio della `Workflow1` classe . Questo campo viene utilizzato in un'attività per determinare se il flusso di lavoro è stato completato.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Aggiungi alla classe `Workflow1` il metodo seguente. Questo metodo controlla il valore della `Document Status` proprietà dell'elenco Documenti per determinare se il documento è stato esaminato. Se la proprietà è impostata su , il metodo imposta il campo su false per indicare che il flusso di `Document Status` lavoro è pronto per il `Review Complete` `checkStatus` `workflowPending` completamento. 

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

3. Aggiungere il codice seguente ai `onWorkflowActivated` metodi e per chiamare il metodo `onWorkflowItemChanged` `checkStatus` . All'avvio del flusso di lavoro, `onWorkflowActivated` il metodo chiama il metodo per `checkStatus` determinare se il documento è già stato esaminato. Se non è stato esaminato, il flusso di lavoro continua. Quando il documento viene salvato, il `onWorkflowItemChanged` metodo chiama di nuovo il metodo per `checkStatus` determinare se il documento è stato esaminato. Mentre il `workflowPending` campo è impostato su **true**, l'esecuzione del flusso di lavoro continua.

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

4. Aggiungere il codice seguente al `isWorkflowPending` metodo per controllare lo stato della proprietà `workflowPending` . Ogni volta che il documento viene salvato, **l'attività whileActivity1** chiama il `isWorkflowPending` metodo . Questo metodo esamina la proprietà <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> dell'oggetto <xref:System.Workflow.Activities.ConditionalEventArgs> per determinare se l'attività **WhileActivity1** deve continuare o terminare. Se la proprietà è impostata su **true**, l'attività continua. In caso contrario, l'attività viene completata e il flusso di lavoro viene completato.

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

## <a name="test-the-sharepoint-workflow-template"></a>Testare il modello SharePoint flusso di lavoro
 Quando si avvia il debugger, distribuisce il modello di flusso di lavoro nel server SharePoint e associa il flusso di lavoro [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **all'elenco Documenti** condivisi . Per testare il flusso di lavoro, avviare un'istanza del flusso di lavoro da un documento **nell'elenco Documenti** condivisi .

#### <a name="to-test-the-sharepoint-workflow-template"></a>Per testare il modello SharePoint flusso di lavoro

1. In *Workflow1.cs o* *Workflow1.vb* impostare un punto di interruzione accanto al **metodo onWorkflowActivated.**

2. Premere **F5 per** compilare ed eseguire la soluzione.

     Viene visualizzato SharePoint sito web.

3. Nel riquadro di spostamento in SharePoint scegliere il **collegamento Documenti** condivisi.

4. Nella pagina **Documenti condivisi** scegliere il collegamento Documenti **nella** scheda **Strumenti** raccolta e quindi scegliere il **Upload Documento.**

5. Nella finestra Upload **documento** fare clic  sul pulsante Sfoglia, scegliere un  file di documento, scegliere il pulsante Apri e quindi scegliere **il pulsante OK.**

     Il documento selezionato viene caricato nell'elenco **Documenti** condivisi e viene avviato il flusso di lavoro.

6. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verificare che il debugger si arresti in corrispondenza del punto di interruzione accanto al metodo `onWorkflowActivated` .

7. Premere **F5 per** continuare l'esecuzione.

8. È possibile modificare le impostazioni per il documento, ma per il momento lasciare i valori predefiniti scegliendo il **pulsante Salva.**

     Verrà visualizzata di nuovo la **pagina Documenti** condivisi del sito Web SharePoint predefinito.

9. Nella pagina **Documenti condivisi** verificare che il valore sotto la colonna **MySharePointWorkflow - Workflow1** sia impostato su **In corso.** Ciò indica che il flusso di lavoro è in corso e che il documento è in attesa di revisione.

10. Nella pagina **Documenti condivisi** scegliere il documento, scegliere la freccia visualizzata e quindi scegliere la voce di menu **Modifica** proprietà.

11. Impostare **Document Status (Stato** **documento) su Review Complete (Revisione** completata) e quindi **scegliere il pulsante Save (Salva).**

     Verrà visualizzata di nuovo la **pagina Documenti** condivisi del sito Web SharePoint predefinito.

12. Nella pagina **Documenti condivisi** verificare che il valore sotto la colonna **Stato documento** sia impostato su Revisione **completata**. Aggiornare la **pagina Documenti** condivisi e verificare che il valore sotto la colonna **MySharePointWorkflow - Workflow1** sia impostato su **Completato.** Ciò indica che il flusso di lavoro è stato completato e che il documento è stato esaminato.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni su come creare modelli di flusso di lavoro, vedere gli argomenti seguenti:

- Per altre informazioni sulle attività SharePoint flusso di lavoro, vedere Attività del flusso di lavoro [per SharePoint Foundation.](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14))

- Per altre informazioni sulle attività Windows Workflow Foundation, vedere [Spazio dei nomi System.Workflow.Activities](/dotnet/api/system.windows.media.color).

## <a name="see-also"></a>Vedi anche
- [Creare soluzioni SharePoint flusso di lavoro](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [SharePoint modelli di progetto e di elemento di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
