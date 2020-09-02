---
title: Creazione di un flusso di lavoro con form di associazione e di avvio
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f257dfed2fe439c5ab22ab9951b6258116c6567
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017136"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Procedura dettagliata: creare un flusso di lavoro con form di associazione e di avvio
  In questa procedura dettagliata viene illustrato come creare un flusso di lavoro sequenziale di base che incorpora l'utilizzo di form di associazione e di avvio. Si tratta di moduli ASPX che consentono l'aggiunta di parametri a un flusso di lavoro quando viene prima associato dall'amministratore di SharePoint (il modulo di associazione) e quando il flusso di lavoro viene avviato dall'utente (modulo di avvio).

 In questa procedura dettagliata viene descritto uno scenario in cui un utente desidera creare un flusso di lavoro di approvazione per le segnalazioni spese che soddisfano i requisiti seguenti:

- Quando il flusso di lavoro è associato a un elenco, all'amministratore viene richiesto un modulo di associazione in cui viene immesso un limite di dollaro per le note spese.

- I dipendenti caricano i report delle spese nell'elenco documenti condivisi, avviano il flusso di lavoro e quindi immettono il totale delle spese nel form di avvio del flusso di lavoro.

- Se il totale di un report spese dipendenti supera il limite predefinito dell'amministratore, viene creata un'attività per il responsabile del dipendente per approvare la nota spese. Tuttavia, se il totale della nota spese di un dipendente è inferiore o uguale al limite di spesa, viene scritto un messaggio di approvazione automatica nell'elenco della cronologia del flusso di lavoro.

  Vengono illustrate le attività seguenti:

- Creazione di un progetto di flusso di lavoro sequenziale di definizione elenco di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Creazione di una pianificazione del flusso di lavoro.

- Gestione degli eventi di attività del flusso di lavoro.

- Creazione di form di associazione e di avvio del flusso di lavoro.

- Associazione del flusso di lavoro.

- Avvio manuale del flusso di lavoro.

> [!NOTE]
> Sebbene in questa procedura dettagliata venga utilizzato un progetto flusso di lavoro sequenziale, il processo è lo stesso per i flussi di lavoro della macchina a Stati.
>
> Il computer potrebbe inoltre mostrare nomi o percorsi diversi per alcuni [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementi dell'interfaccia utente nelle istruzioni seguenti. L' [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] edizione in uso e le impostazioni usate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Creazione di un progetto flusso di lavoro sequenziale di SharePoint
 Per prima cosa, creare un progetto di flusso di lavoro sequenziale in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Un flusso di lavoro sequenziale è una serie di passaggi eseguiti in ordine fino al completamento dell'ultima attività. In questa procedura verrà creato un flusso di lavoro sequenziale che si applica all'elenco di documenti condivisi in SharePoint. La procedura guidata del flusso di lavoro consente di associare il flusso di lavoro al sito o alla definizione di elenco e consente di determinare quando verrà avviato il flusso di lavoro.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Per creare un progetto di flusso di lavoro sequenziale di SharePoint

1. Sulla barra dei menu scegliere **file**  >  **nuovo**  >  **progetto** per visualizzare la finestra di dialogo **nuovo progetto** .

2. Espandere il nodo **SharePoint** sotto **Visual C#** o **Visual Basic**, quindi scegliere il nodo **2010** .

3. Nel riquadro **modelli** scegliere il modello di progetto **SharePoint 2010 Project** .

4. Nella casella **nome** immettere **ExpenseReport** , quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

5. Nella pagina **specificare il sito e il livello di sicurezza per il debug** scegliere il pulsante di opzione **Distribuisci come soluzione farm** , quindi scegliere il pulsante **fine** per accettare il livello di attendibilità e il sito predefinito.

     Questo passaggio imposta inoltre il livello di attendibilità della soluzione come soluzione farm, che è l'unica opzione disponibile per i progetti di flusso di lavoro.

6. Scegliere il nodo di progetto in **Esplora soluzioni**.

7. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

8. In **Visual C#** o **Visual Basic**espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

9. Nel riquadro **modelli** scegliere modello di **flusso di lavoro sequenziale (solo soluzione farm)** , quindi scegliere il pulsante **Aggiungi** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

10. Nella pagina **specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito (**ExpenseReport-Workflow1**). Mantieni il valore del tipo di modello di flusso di lavoro predefinito (**elenco flusso di lavoro)**. Fare clic su **Avanti**.

11. Nella pagina **si desidera che Visual Studio associ automaticamente il flusso di lavoro in una sessione di debug?** deselezionare la casella che associa automaticamente il modello di flusso di lavoro, se selezionato.

     Questo passaggio consente di associare manualmente il flusso di lavoro all'elenco documenti condivisi in un secondo momento, che consente di visualizzare il modulo di associazione.

12. Fare clic sul pulsante **Fine**.

## <a name="add-an-association-form-to-the-workflow"></a>Aggiungere un modulo di associazione al flusso di lavoro
 Successivamente, creare un. Modulo di associazione ASPX visualizzato quando l'amministratore di SharePoint associa il flusso di lavoro a un documento di nota spese.

#### <a name="to-add-an-association-form-to-the-workflow"></a>Per aggiungere un modulo di associazione al flusso di lavoro

1. Scegliere il nodo **Workflow1** in **Esplora soluzioni**.

2. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento** per visualizzare la finestra di dialogo **Aggiungi nuovo elemento** .

3. Nella visualizzazione albero della finestra di dialogo espandere **Visual C#** o **Visual Basic** (a seconda del linguaggio del progetto), espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

4. Nell'elenco dei modelli scegliere il modello di **modulo di associazione del flusso di lavoro** .

5. Nella casella di testo **nome** immettere **ExpenseReportAssocForm. aspx**.

6. Scegliere il pulsante **Aggiungi** per aggiungere il modulo al progetto.

## <a name="designing-and-coding-the-association-form"></a>Progettazione e codifica del modulo di associazione
 In questa procedura si introdurranno le funzionalità al modulo di associazione mediante l'aggiunta di controlli e codice.

#### <a name="to-design-and-code-the-association-form"></a>Per progettare e codificare il form di associazione

1. Nel modulo di associazione (ExpenseReportAssocForm. aspx) individuare l' `asp:Content` elemento con `ID="Main"` .

2. Subito dopo la prima riga in questo elemento di contenuto, aggiungere il codice seguente per creare un'etichetta e una casella di testo che richiede il limite di approvazione della spesa (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Espandere il file **ExpenseReportAssocForm. aspx** in **Esplora soluzioni** per visualizzare i file dipendenti.

    > [!NOTE]
    > Se il progetto è in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , è necessario scegliere il pulsante **Visualizza tutti i file** per eseguire questo passaggio.

4. Aprire il menu di scelta rapida per il file ExpenseReportAssocForm. aspx e scegliere **Visualizza codice**.

5. Sostituire il `GetAssociationData` metodo con:

    ```vb
    Private Function GetAssociationData() As String
        ' TODO: Return a string that contains the association data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return Me.AutoApproveLimit.Text
    End Function
    ```

    ```csharp
    private string GetAssociationData()
    {
        // TODO: Return a string that contains the association data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.AutoApproveLimit.Text;
    }
    ```

## <a name="add-an-initiation-form-to-the-workflow"></a>Aggiungere un modulo di avvio al flusso di lavoro
 Successivamente, creare il modulo di avvio che viene visualizzato quando gli utenti eseguono il flusso di lavoro in relazione alle spese.

#### <a name="to-create-an-initiation-form"></a>Per creare un modulo di avvio

1. Scegliere il nodo **Workflow1** in **Esplora soluzioni**.

2. Nella barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento** per visualizzare la finestra di dialogo **Aggiungi nuovo elemento** .

3. Nella visualizzazione albero della finestra di dialogo espandere **Visual C#** o **Visual Basic**  (a seconda del linguaggio del progetto), espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

4. Nell'elenco dei modelli scegliere il modello **modulo di avvio del flusso di lavoro** .

5. Nella casella di testo **nome** immettere **ExpenseReportInitForm. aspx**.

6. Scegliere il pulsante **Aggiungi** per aggiungere il modulo al progetto.

## <a name="designing-and-coding-the-initiation-form"></a>Progettazione e codifica del modulo di avvio
 Introdurre quindi la funzionalità per il form di avvio aggiungendo controlli e codice.

#### <a name="to-code-the-initiation-form"></a>Per codificare il form di avvio

1. Nel modulo di avvio (ExpenseReportInitForm. aspx) individuare l' `asp:Content` elemento che contiene `ID="Main"` .

2. Subito dopo la prima riga in questo elemento di contenuto, aggiungere il codice seguente per creare un'etichetta e una casella di testo che Visualizza il limite di approvazione della spesa (*AutoApproveLimit*) immesso nel modulo di associazione e un'altra etichetta e casella di testo per richiedere il totale delle spese (*ExpenseTotal*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Espandere il file **ExpenseReportInitForm. aspx** in **Esplora soluzioni** per visualizzare i file dipendenti.

4. Aprire il menu di scelta rapida per il file ExpenseReportInitForm. aspx e scegliere **Visualizza codice**.

5. Sostituire il `Page_Load` metodo con l'esempio seguente:

    ```vb
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As
      EventArgs) Handles Me.Load
        InitializeParams()
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New
          Guid(associationGuid)).AssociationData
        ' Optionally, add code here to pre-populate your form fields.
    End Sub
    ```

    ```csharp
    protected void Page_Load(object sender, EventArgs e)
    {
        InitializeParams();
        this.AutoApproveLimit.Text =
          workflowList.WorkflowAssociations[new
          Guid(associationGuid)].AssociationData;
    }
    ```

6. Sostituire il `GetInitiationData` metodo con l'esempio seguente:

    ```vb
    ' This method is called when the user clicks the button to start the workflow.
    Private Function GetInitiationData() As String
        Return Me.ExpenseTotal.Text
        ' TODO: Return a string that contains the initiation data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return String.Empty
    End Function
    ```

    ```csharp
    // This method is called when the user clicks the button to start the workflow.
    private string GetInitiationData()
    {
        // TODO: Return a string that contains the initiation data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.ExpenseTotal.Text;
    }
    ```

## <a name="cutomize-the-workflow"></a>Personalizzare del flusso di lavoro
 Personalizzare quindi il flusso di lavoro. In seguito, si associeranno due moduli al flusso di lavoro.

#### <a name="to-customize-the-workflow"></a>Per personalizzare il flusso di lavoro

1. Visualizzare il flusso di lavoro in Progettazione flussi di lavoro aprendo Workflow1 nel progetto.

2. Nella **casella degli strumenti**espandere il nodo **Windows Workflow v 3.0** e individuare l'attività **IfElse** .

3. Aggiungere questa attività al flusso di lavoro eseguendo uno dei passaggi seguenti:

    - Aprire il menu di scelta rapida per l'attività **IfElse** , scegliere **copia**, aprire il menu di scelta rapida per la riga sotto l'attività **onWorkflowActivated1** nella finestra di progettazione del flusso di lavoro, quindi scegliere **Incolla**.

    - Trascinare l'attività **IfElse** dalla **casella degli strumenti**e connetterla alla riga sotto l'attività **onWorkflowActiviated1** nella finestra di progettazione del flusso di lavoro.

4. Nella casella degli strumenti espandere il nodo **flusso di lavoro SharePoint** e individuare l'attività **CreateTask** .

5. Aggiungere questa attività al flusso di lavoro eseguendo uno dei passaggi seguenti:

    - Aprire il menu di scelta rapida per l'attività **CreateTask** , scegliere **copia**, aprire il menu di scelta rapida per una delle due aree **attività rilasciate qui** all'interno di **IfElseActivity1** nella finestra di progettazione del flusso di lavoro, quindi scegliere **Incolla**.

    - Trascinare l'attività **CreateTask** dalla **casella degli strumenti** in una delle due aree **attività drop qui** all'interno di **IfElseActivity1**.

6. Nella finestra **Proprietà** immettere il valore della proprietà *TaskToken* per la proprietà **CorrelationToken** .

7. Espandere la proprietà **CorrelationToken** scegliendo il segno più (![TreeView Plus](../sharepoint/media/plus.gif "Più di TreeView")) accanto.

8. Scegliere la freccia a discesa nella sottoproprietà **OwnerActivityName** e impostare il valore *Workflow1* .

9. Scegliere la proprietà **taskId** , quindi fare clic sul pulsante con i puntini di sospensione (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) per visualizzare la finestra di dialogo **Associa proprietà** .

10. Scegliere la scheda **associa a un nuovo membro** , scegliere il pulsante di opzione **Crea campo** , quindi scegliere il pulsante **OK** .

11. scegliere la proprietà **TaskProperties** , quindi fare clic sul pulsante con i puntini di sospensione (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) per visualizzare la finestra di dialogo **Associa proprietà** .

12. Scegliere la scheda **associa a un nuovo membro** , scegliere il pulsante di opzione **Crea campo** , quindi scegliere il pulsante **OK** .

13. Nella **casella degli strumenti**espandere il nodo **flusso di lavoro SharePoint** e individuare l'attività **LogToHistoryListActivity** .

14. Aggiungere questa attività al flusso di lavoro eseguendo uno dei passaggi seguenti:

    - Aprire il menu di scelta rapida per l'attività **LogToHistoryListActivity** , scegliere **copia**, aprire il menu di scelta rapida per le altre aree **Drop Activities** in **IfElseActivity1** nella finestra di progettazione del flusso di lavoro, quindi scegliere **Incolla**.

    - Trascinare l'attività **LogToHistoryListActivity** dalla **casella degli strumenti**e rilasciarla sull'area di rilascio delle altre **attività** all'interno di **IfElseActivity1**.

## <a name="add-code-to-the-workflow"></a>Aggiungere codice al flusso di lavoro
 Successivamente, aggiungere il codice al flusso di lavoro per fornire la funzionalità.

#### <a name="to-add-code-to-the-workflow"></a>Per aggiungere codice al flusso di lavoro

1. Aprire il menu di scelta rapida per l'attività **createTask1** in Progettazione flussi di lavoro, quindi scegliere **Visualizza codice**.

2. Aggiungere il metodo seguente:

    ```vb
    Private Sub createTask1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        createTask1_TaskId1 = Guid.NewGuid
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"
        createTask1_TaskProperties1.Description = "Please approve the
          expense report"
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed"
    End Sub
    ```

    ```csharp
    private void createTask1_MethodInvoking(object sender, EventArgs e)
    {
        createTask1_TaskId1 = Guid.NewGuid();
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";
        createTask1_TaskProperties1.Description = "Please approve the
          expense report";
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed";
    }
    ```

    > [!NOTE]
    > Nel codice sostituire `somedomain\\someuser` con un dominio e un nome utente per cui verrà creata un'attività, ad esempio " `Office\\JoeSch` ". Per il test è più semplice usare l'account con cui si sta sviluppando.

3. Sotto il `MethodInvoking` metodo aggiungere l'esempio seguente:

    ```vb
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As
      ConditionalEventArgs)
        Dim approval As Boolean = False
        If (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData)) Then
            approval = True
        End If
        e.Result = approval
    End Sub
    ```

    ```csharp
    private void checkApprovalNeeded(object sender, ConditionalEventArgs
      e)
    {
        bool approval = false;
        if (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData))
        {
            approval = true;
        }
        e.Result = approval;
    }
    ```

4. Nella finestra di progettazione del flusso di lavoro scegliere l'attività **ifElseBranchActivity1** .

5. Nella finestra **Proprietà** scegliere la freccia a discesa della proprietà **Condition** , quindi impostare il valore della *condizione del codice* .

6. Espandere la proprietà **Condition** scegliendo il segno più (![TreeView Plus](../sharepoint/media/plus.gif "Più di TreeView")) accanto, quindi impostare il relativo valore su *checkApprovalNeeded*.

7. Nella finestra di progettazione del flusso di lavoro aprire il menu di scelta rapida per l'attività **logToHistoryListActivity1** , quindi scegliere **genera gestori** per generare un metodo vuoto per l' `MethodInvoking` evento.

8. Sostituire il `MethodInvoking` codice con il codice seguente:

    ```vb
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto
          approved for " + workflowProperties.InitiationData)
    End Sub
    ```

    ```csharp
    private void logToHistoryListActivity1_MethodInvoking(object sender,
      EventArgs e)
    {
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was
          auto approved for " + workflowProperties.InitiationData;
    }
    ```

9. Premere il tasto **F5** per eseguire il debug del programma.

     Questa operazione compila l'applicazione, la inserisce in un pacchetto, la distribuisce, ne attiva le funzionalità, ricicla il [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool di applicazioni e quindi avvia il browser nel percorso specificato nella proprietà **URL sito** .

## <a name="associating-the-workflow-to-the-documents-list"></a>Associazione del flusso di lavoro all'elenco documenti
 Successivamente, visualizzare il form di associazione del flusso di lavoro associando il flusso di lavoro all'elenco **Documenticondivisi** nel sito di SharePoint.

#### <a name="to-associate-the-workflow"></a>Per associare il flusso di lavoro

1. Scegliere il collegamento **documenti condivisi** sulla barra QuickLaunch.

2. Scegliere il collegamento **libreria** nella scheda **strumenti libreria** , quindi scegliere il pulsante della barra multifunzione **Impostazioni libreria** .

3. Nella sezione **autorizzazioni e gestione** scegliere il collegamento **Impostazioni flusso di lavoro** , quindi scegliere il collegamento **Aggiungi un flusso di lavoro** nella pagina **flussi** di lavoro.

4. Nell'elenco in alto nella pagina Impostazioni flusso di lavoro scegliere il modello **ExpenseReport-Workflow1** .

5. Nel campo successivo immettere **ExpenseReportWorkflow** , quindi scegliere il pulsante **Avanti** .

     Il flusso di lavoro viene associato all'elenco dei **documenti condivisi** e viene visualizzato il form di associazione del flusso di lavoro.

6. Nella casella di testo **limite approvazione automatica** immettere **1200** , quindi scegliere il pulsante **Associa flusso di lavoro** .

## <a name="start-the-workflow"></a>Avviare il flusso di lavoro
 Associare quindi il flusso di lavoro a uno dei documenti nell'elenco **documenti condivisi** per visualizzare il form di avvio del flusso di lavoro.

#### <a name="to-start-the-workflow"></a>Per avviare il flusso di lavoro

1. Nella pagina di SharePoint scegliere il pulsante **Home** .

2. Scegliere il collegamento **documenti condivisi** sulla barra QuickLaunch per visualizzare l'elenco dei **documenti condivisi** .

3. Scegliere il collegamento **documenti** nella scheda **strumenti libreria** nella parte superiore della pagina, quindi scegliere il pulsante **Carica documento** sulla barra multifunzione per caricare un nuovo documento nell'elenco **documenti condivisi** .

4. Nella finestra di dialogo **Carica documento** scegliere il pulsante **Sfoglia** , scegliere un file di documento, scegliere il pulsante **Apri** , quindi scegliere il pulsante **OK** .

     È possibile modificare le impostazioni per il documento in questa finestra di dialogo, ma lasciare i valori predefiniti scegliendo il pulsante **Salva** .

5. Scegliere il documento caricato, scegliere la freccia a discesa visualizzata, quindi scegliere l'elemento flussi di **lavoro** .

6. Scegliere l'immagine accanto a ExpenseReportWorkflow.

     Viene visualizzato il form di avvio del flusso di lavoro. Si noti che il valore visualizzato nella casella **limite approvazione automatica** è di sola lettura perché è stato immesso nel modulo di associazione.

7. Nella casella di testo **spese totali** immettere **1600**, quindi scegliere il pulsante **Avvia flusso di lavoro** .

     Verrà visualizzato di nuovo l'elenco dei **documenti condivisi** . Una nuova colonna denominata **ExpenseReportWorkflow** con il valore **Completed** viene aggiunta all'elemento appena avviato dal flusso di lavoro.

8. Scegliere la freccia a discesa accanto al documento caricato, quindi scegliere l'elemento **flussi di lavoro** per visualizzare la pagina stato del flusso di lavoro. Scegliere il valore **completato** in **flussi di lavoro completati**. L'attività è elencata nella sezione **attività** .

9. Scegliere il titolo dell'attività per visualizzare i dettagli dell'attività.

10. Tornare all'elenco **Documenticondivisi** e riavviare il flusso di lavoro, usando lo stesso documento o uno diverso.

11. Immettere una quantità nella pagina di avvio minore o uguale alla quantità immessa nella pagina di associazione (**1200**).

     In tal caso, viene creata una voce nell'elenco della cronologia anziché un'attività. La voce viene visualizzata nella sezione **cronologia del flusso di lavoro** della pagina stato del flusso di lavoro. Si noti il messaggio nella colonna **risultato** dell'evento History. Contiene il testo immesso nell' `logToHistoryListActivity1.MethodInvoking` evento che include la quantità che è stata approvata automaticamente.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni su come creare modelli di flusso di lavoro, vedere questi argomenti:

- Per ulteriori informazioni sui flussi di lavoro di SharePoint, vedere [flussi di lavoro in Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14)).

## <a name="see-also"></a>Vedere anche
- [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Procedura dettagliata: aggiungere una pagina dell'applicazione a un flusso di lavoro](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
