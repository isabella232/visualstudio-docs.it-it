---
title: Creare un flusso di lavoro con moduli di associazione e di avvio
description: In questa SharePoint procedura dettagliata creare un flusso di lavoro sequenziale di base che incorpora l'uso di moduli di associazione e di avvio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2f3852452d163f14e93b73e7fd894759f7aa0197
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625086"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Procedura dettagliata: Creare un flusso di lavoro con moduli di associazione e avvio
  Questa procedura dettagliata illustra come creare un flusso di lavoro sequenziale di base che incorpora l'uso di moduli di associazione e di avvio. Si tratta di moduli ASPX che consentono l'aggiunta di parametri a un flusso di lavoro quando viene associato per la prima volta dall'amministratore di SharePoint (modulo di associazione) e quando il flusso di lavoro viene avviato dall'utente (modulo di avvio).

 Questa procedura dettagliata descrive uno scenario in cui un utente vuole creare un flusso di lavoro di approvazione per le note spese con i requisiti seguenti:

- Quando il flusso di lavoro è associato a un elenco, all'amministratore viene richiesto un modulo di associazione in cui immettere un limite di dollari per le note spese.

- I dipendenti caricano le note spese nell'elenco Documenti condivisi, avviano il flusso di lavoro e quindi immettono il totale delle spese nel modulo di avvio del flusso di lavoro.

- Se il totale di una nota spese dei dipendenti supera il limite predefinito dell'amministratore, viene creata un'attività per il responsabile del dipendente per approvare la nota spese. Tuttavia, se il totale della nota spese di un dipendente è minore o uguale al limite di spesa, viene scritto un messaggio approvato automaticamente nell'elenco della cronologia del flusso di lavoro.

  Vengono illustrate le attività seguenti:

- Creazione di un SharePoint di flusso di lavoro sequenziale di definizione dell'elenco in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Creazione di una pianificazione del flusso di lavoro.

- Gestione degli eventi dell'attività del flusso di lavoro.

- Creazione di moduli di associazione e avvio del flusso di lavoro.

- Associazione del flusso di lavoro.

- Avvio manuale del flusso di lavoro.

> [!NOTE]
> Anche se questa procedura dettagliata usa un progetto flusso di lavoro sequenziale, il processo è lo stesso per i flussi di lavoro delle macchine a stati.
>
> Inoltre, il computer potrebbe visualizzare nomi o percorsi diversi per alcuni degli elementi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dell'interfaccia utente nelle istruzioni seguenti. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]L'edizione in uso e le impostazioni usate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Creare un progetto SharePoint flusso di lavoro sequenziale
 Creare prima di tutto un progetto flusso di lavoro sequenziale in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Un flusso di lavoro sequenziale è una serie di passaggi che vengono eseguiti nell'ordine fino al completamento dell'ultima attività. In questa procedura verrà creato un flusso di lavoro sequenziale che si applica all'elenco Documenti condivisi in SharePoint. La procedura guidata del flusso di lavoro consente di associare il flusso di lavoro al sito o alla definizione dell'elenco e consente di determinare quando il flusso di lavoro verrà avviato.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Per creare un progetto SharePoint flusso di lavoro sequenziale

1. Nella barra dei menu scegliere **File** nuovo Project  >    >   per visualizzare la **finestra di dialogo Project** nuovo file.

2. Espandere il **SharePoint** in **Visual C#** o **Visual Basic** e quindi scegliere il **nodo 2010.**

3. Nel riquadro **Modelli** scegliere il modello di **SharePoint 2010 Project** progetto.

4. Nella casella **Nome** immettere **ExpenseReport** e quindi fare clic sul **pulsante OK.**

     Verrà **SharePoint personalizzazione guidata.**

5. Nella pagina **Specificare il sito e** il livello di sicurezza per il debug  scegliere il pulsante di opzione Distribuisci come soluzione **farm** e quindi scegliere il pulsante Fine per accettare il livello di attendibilità e il sito predefinito.

     Questo passaggio imposta anche il livello di attendibilità per la soluzione come soluzione farm, che è l'unica opzione disponibile per i progetti del flusso di lavoro.

6. Scegliere il nodo di progetto in **Esplora soluzioni**.

7. Sulla barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

8. In **Visual C#** o **Visual Basic** espandere  il nodo SharePoint e quindi scegliere il **nodo 2010.**

9. Nel riquadro **Modelli** scegliere il modello Flusso di **lavoro sequenziale (solo** soluzione farm) e quindi scegliere **il pulsante** Aggiungi.

     Verrà **SharePoint personalizzazione guidata.**

10. Nella pagina **Specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito (**ExpenseReport - Workflow1**). Mantenere il valore predefinito del tipo di modello di flusso di lavoro (**Elenca flusso di lavoro).** Fare clic su **Avanti**.

11. Nella pagina **Si vuole Visual Studio automaticamente** il flusso di lavoro in una sessione di debug? deselezionare la casella che associa automaticamente il modello di flusso di lavoro se è selezionato.

     Questo passaggio consente di associare manualmente il flusso di lavoro all'elenco Documenti condivisi in un secondo momento, in cui viene visualizzato il modulo di associazione.

12. Fare clic sul pulsante **Fine**.

## <a name="add-an-association-form-to-the-workflow"></a>Aggiungere un modulo di associazione al flusso di lavoro
 Creare quindi un oggetto . Modulo di associazione ASPX che viene visualizzato quando l SharePoint amministratore associa per la prima volta il flusso di lavoro a un documento della nota spese.

#### <a name="to-add-an-association-form-to-the-workflow"></a>Per aggiungere un modulo di associazione al flusso di lavoro

1. Scegliere il **nodo Workflow1** in **Esplora soluzioni**.

2. Sulla barra dei menu scegliere **Project** Aggiungi nuovo  >  **elemento** per visualizzare la finestra **di dialogo** Aggiungi nuovo elemento.

3. Nella visualizzazione albero della finestra di dialogo espandere **Visual C#** o **Visual Basic (a** seconda del linguaggio del progetto), espandere il nodo **SharePoint** e quindi scegliere il **nodo 2010.**

4. Nell'elenco di modelli scegliere il modello **Form di associazione del** flusso di lavoro.

5. Nella casella **di** testo Nome immettere **ExpenseReportAssocForm.aspx**.

6. Scegliere il **pulsante** Aggiungi per aggiungere il modulo al progetto.

## <a name="designing-and-coding-the-association-form"></a>Progettazione e codifica del modulo di associazione
 In questa procedura si introducono funzionalità al modulo di associazione aggiungendo controlli e codice.

#### <a name="to-design-and-code-the-association-form"></a>Per progettare e codificare il modulo di associazione

1. Nel modulo di associazione (ExpenseReportAssocForm.aspx) individuare `asp:Content` l'elemento con `ID="Main"` .

2. Subito dopo la prima riga in questo elemento di contenuto, aggiungere il codice seguente per creare un'etichetta e una casella di testo che richiede il limite di approvazione delle spese (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Espandere il file **ExpenseReportAssocForm.aspx** in **Esplora soluzioni** visualizzare i file dipendenti.

    > [!NOTE]
    > Se il progetto è in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , è necessario scegliere il pulsante Visualizza tutti **i** file per eseguire questo passaggio.

4. Aprire il menu di scelta rapida per il file ExpenseReportAssocForm.aspx e scegliere **Visualizza codice**.

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
 Creare quindi il modulo di avvio che viene visualizzato quando gli utenti eseguono il flusso di lavoro in base alle note spese.

#### <a name="to-create-an-initiation-form"></a>Per creare un modulo di avvio

1. Scegliere il **nodo Workflow1** in **Esplora soluzioni**.

2. Sulla barra dei menu scegliere **Project** Aggiungi nuovo elemento visualizzare la finestra di dialogo Aggiungi  >   nuovo elemento. 

3. Nella visualizzazione albero della finestra di dialogo espandere **Visual C#** o **Visual Basic (a** seconda del linguaggio del progetto), espandere il nodo **SharePoint** e quindi scegliere il **nodo 2010.**

4. Nell'elenco dei modelli scegliere il modello **Modulo di avvio flusso di** lavoro.

5. Nella casella **di** testo Nome immettere **ExpenseReportInitForm.aspx.**

6. Scegliere il **pulsante** Aggiungi per aggiungere il modulo al progetto.

## <a name="designing-and-coding-the-initiation-form"></a>Progettazione e codifica del modulo di avvio
 Introdurre quindi la funzionalità nel modulo di avvio aggiungendo controlli e codice.

#### <a name="to-code-the-initiation-form"></a>Per codificare il modulo di avvio

1. Nel modulo di avvio (ExpenseReportInitForm.aspx) individuare `asp:Content` l'elemento che contiene `ID="Main"` .

2. Subito dopo la prima riga di questo elemento di contenuto, aggiungere il codice seguente per creare un'etichetta e una casella di testo che visualizza il limite di approvazione delle spese (*AutoApproveLimit*) immesso nel modulo di associazione e un'altra etichetta e una casella di testo per richiedere il totale delle spese (*ExpenseTotal*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Espandere il file **ExpenseReportInitForm.aspx** in **Esplora soluzioni** visualizzare i relativi file dipendenti.

4. Aprire il menu di scelta rapida per il file ExpenseReportInitForm.aspx e scegliere **Visualizza codice**.

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

## <a name="cutomize-the-workflow"></a>Ridurre il flusso di lavoro
 Personalizzare quindi il flusso di lavoro. In un secondo momento verranno associati due moduli al flusso di lavoro.

#### <a name="to-customize-the-workflow"></a>Per personalizzare il flusso di lavoro

1. Visualizzare il flusso di lavoro nella finestra di progettazione del flusso di lavoro aprendo Workflow1 nel progetto.

2. Nella casella **degli strumenti** espandere il Windows **workflow v3.0** e individuare **l'attività IfElse.**

3. Aggiungere questa attività al flusso di lavoro eseguendo uno dei passaggi seguenti:

    - Aprire il menu di scelta rapida per l'attività **IfElse,** scegliere **Copia,** aprire il menu di scelta rapida per la riga nell'attività **onWorkflowActivated1** nella finestra di progettazione del flusso di lavoro e quindi scegliere **Incolla**.

    - Trascinare **l'attività IfElse** dalla Casella **degli** strumenti e connetterla alla riga sotto l'attività **onWorkflowActiviated1** nella finestra di progettazione del flusso di lavoro.

4. Nella casella degli strumenti espandere il nodo **SharePoint flusso di lavoro** e individuare l'attività **CreateTask.**

5. Aggiungere questa attività al flusso di lavoro eseguendo uno dei passaggi seguenti:

    - Aprire il menu di scelta rapida per l'attività **CreateTask,** scegliere **Copia,** aprire il menu di scelta rapida per una delle due aree **Drop Activities Here** all'interno di **IfElseActivity1** nella finestra di progettazione del flusso di lavoro e quindi scegliere **Incolla**.

    - Trascinare **l'attività CreateTask** dalla **Casella degli strumenti** in una delle due aree Drop Activities **Here** all'interno **di IfElseActivity1.**

6. Nella finestra **Proprietà** immettere il valore della proprietà *taskToken* per la **proprietà CorrelationToken.**

7. Espandere la **proprietà CorrelationToken** scegliendo il segno più (![TreeView più](../sharepoint/media/plus.gif "Più di TreeView")) accanto.

8. Scegliere la freccia a discesa nella sotto property **OwnerActivityName** e impostare il *valore Workflow1.*

9. Scegliere la **proprietà TaskId** e quindi scegliere i puntini di sospensione ( ASP.NET ![puntini](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")di sospensione di Progettazione dispositivi mobili ) per visualizzare la finestra di **dialogo Associa** proprietà.

10. Scegliere la **scheda Associa a un nuovo membro,** scegliere il pulsante di opzione **Crea** campo e quindi scegliere il **pulsante OK.**

11. Scegliere la **proprietà TaskProperties** e quindi scegliere i puntini di sospensione ( ASP.NET ![puntini](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")di sospensione di Progettazione dispositivi mobili ) per visualizzare la finestra di **dialogo Associa** proprietà.

12. Scegliere la **scheda Associa a un nuovo membro,** scegliere il pulsante di opzione **Crea** campo e quindi scegliere il **pulsante OK.**

13. Nella casella **degli strumenti** espandere il SharePoint **flusso di** lavoro e individuare **l'attività LogToHistoryListActivity.**

14. Aggiungere questa attività al flusso di lavoro eseguendo uno dei passaggi seguenti:

    - Aprire il menu di scelta rapida per l'attività **LogToHistoryListActivity,** scegliere **Copia,** aprire il menu di scelta rapida per l'altra **area** Rilascia attività qui all'interno di **IfElseActivity1** nella finestra di progettazione del flusso di lavoro e quindi scegliere **Incolla.**

    - Trascinare **l'attività LogToHistoryListActivity** dalla Casella degli strumenti e rilasciarla nell'altra area **Drop Activities Here** (Rilascia attività qui) all'interno di **IfElseActivity1.** 

## <a name="add-code-to-the-workflow"></a>Aggiungere codice al flusso di lavoro
 Aggiungere quindi il codice al flusso di lavoro per assegnargli la funzionalità.

#### <a name="to-add-code-to-the-workflow"></a>Per aggiungere codice al flusso di lavoro

1. Aprire il menu di scelta rapida per **l'attività createTask1** nella finestra di progettazione del flusso di lavoro e quindi **scegliere Visualizza codice.**

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
    > Nel codice sostituire con un dominio e un nome utente per cui verrà creata un'attività, ad `somedomain\\someuser` esempio " `Office\\JoeSch` ". Per il test è più semplice usare l'account con cui si sta sviluppando.

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

4. Nella finestra di progettazione del flusso di lavoro scegliere **l'attività ifElseBranchActivity1.**

5. Nella finestra **Proprietà** scegliere la freccia a discesa della proprietà **Condizione** e quindi impostare il *valore Condizione codice.*

6. Espandere la **proprietà Condizione** scegliendo il segno più (![TreeView più](../sharepoint/media/plus.gif "Più di TreeView")) accanto e quindi impostarne il valore su *checkApprovalNeeded.*

7. Nella finestra di progettazione del flusso di lavoro aprire il menu di  scelta rapida per l'attività **logToHistoryListActivity1** e quindi scegliere Genera gestori per generare un metodo vuoto per `MethodInvoking` l'evento.

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

9. Premere **F5 per** eseguire il debug del programma.

     L'applicazione viene compilata, in pacchetto, distribuita, attiva le funzionalità, ricicla il pool di applicazioni e quindi avvia il browser nel percorso specificato nella proprietà [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] **URL** sito.

## <a name="associating-the-workflow-to-the-documents-list"></a>Associazione del flusso di lavoro all'elenco di documenti
 Visualizzare quindi il form di associazione del flusso di lavoro associando il flusso di lavoro **all'elenco SharedDocuments** SharePoint sito.

#### <a name="to-associate-the-workflow"></a>Per associare il flusso di lavoro

1. Scegliere il **collegamento Documenti** condivisi sulla barra avvio rapido.

2. Scegliere il **collegamento Libreria** nella scheda **Strumenti libreria** e quindi fare clic sul pulsante Libreria Impostazioni **barra** multifunzione.

3. Nella sezione Autorizzazioni **e gestione scegliere** il collegamento **Impostazioni** flusso  di lavoro e quindi scegliere il collegamento Aggiungi un flusso di lavoro nella **pagina Flussi di** lavoro.

4. Nell'elenco superiore della pagina delle impostazioni del flusso di lavoro scegliere il **modello ExpenseReport - Workflow1.**

5. Nel campo successivo immettere **ExpenseReportWorkflow** e quindi scegliere **il pulsante** Avanti.

     In questo modo il flusso di lavoro viene associato **all'elenco Documenti** condivisi e viene visualizzato il form di associazione del flusso di lavoro.

6. Nella casella **di testo Auto Approval Limit (Limite** approvazione automatica) immettere **1200** e quindi scegliere il **pulsante Associate Workflow (Associa flusso di** lavoro).

## <a name="start-the-workflow"></a>Avviare il flusso di lavoro
 Associare quindi il flusso di lavoro a uno dei documenti nell'elenco **Documenti** condivisi per visualizzare il form di avvio del flusso di lavoro.

#### <a name="to-start-the-workflow"></a>Per avviare il flusso di lavoro

1. Nella pagina SharePoint fare clic sul **pulsante Home.**

2. Scegliere il **collegamento Documenti** condivisi sulla barra avvio rapido per visualizzare l'elenco **Documenti** condivisi.

3. Scegliere il **collegamento** Documenti nella scheda **Strumenti** raccolta nella parte superiore della pagina e quindi scegliere il pulsante Documento **Upload** sulla barra multifunzione per caricare un nuovo documento nell'elenco Documenti **condivisi.**

4. Nella finestra Upload **documento** fare clic  sul pulsante Sfoglia, scegliere un  file di documento, scegliere il pulsante Apri e quindi scegliere **il pulsante OK.**

     È possibile modificare le impostazioni per il documento in questa finestra di dialogo, ma lasciare i valori predefiniti scegliendo il **pulsante Salva.**

5. Scegliere il documento caricato, scegliere la freccia a discesa visualizzata e quindi scegliere **l'elemento Flussi di** lavoro.

6. Scegliere l'immagine accanto a ExpenseReportWorkflow.

     Verrà visualizzato il form di avvio del flusso di lavoro. Si noti che il valore visualizzato nella casella **Limite** approvazione automatica è di sola lettura perché è stato immesso nel modulo di associazione.

7. Nella casella **di testo Expense Total** (Totale spese) immettere **1600** e quindi scegliere il **pulsante Start Workflow (Avvia flusso di** lavoro).

     Verrà visualizzato di **nuovo l'elenco** Documenti condivisi. Una nuova colonna denominata **ExpenseReportWorkflow** con il valore **Completed** viene aggiunta all'elemento appena avviato dal flusso di lavoro.

8. Scegliere la freccia a discesa accanto al documento caricato e quindi scegliere l'elemento **Flussi** di lavoro per visualizzare la pagina dello stato del flusso di lavoro. Scegliere il **valore Completato** in Flussi di **lavoro completati**. L'attività è elencata nella **sezione** Attività.

9. Scegliere il titolo dell'attività per visualizzarne i dettagli.

10. Tornare **all'elenco SharedDocuments e** riavviare il flusso di lavoro, usando lo stesso documento o uno diverso.

11. Immettere un importo nella pagina di avvio minore o uguale a quello immesso nella pagina di associazione (**1200**).

     In questo caso, viene creata una voce nell'elenco della cronologia anziché un'attività. La voce viene visualizzata nella sezione **Cronologia flusso di lavoro** della pagina dello stato del flusso di lavoro. Si noti il messaggio nella **colonna Risultato** dell'evento della cronologia. Contiene il testo immesso `logToHistoryListActivity1.MethodInvoking` nell'evento che include l'importo approvato automaticamente.

## <a name="next-steps"></a>Passaggi successivi
 Per altre informazioni su come creare modelli di flusso di lavoro, vedere gli argomenti seguenti:

- Per altre informazioni sui flussi SharePoint, vedere [Flussi di lavoro in Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14)).

## <a name="see-also"></a>Vedi anche
- [Creare soluzioni SharePoint flusso di lavoro](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Procedura dettagliata: Aggiungere una pagina dell'applicazione a un flusso di lavoro](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
