---
title: Creare flussi di lavoro con form di associazione e avvio
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: b64d1c9fbbd81a21ab268dfa29287895bd355197
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401159"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Procedura dettagliata: Creare un flusso di lavoro con form di associazione e di avvio
  Questa procedura dettagliata viene illustrato come creare un flusso di lavoro sequenza base che incorpora l'utilizzo dei form di associazione e di avvio. Questi sono i form ASPX che abilitano i parametri per essere aggiunti a un flusso di lavoro quando è associato prima di tutto dall'amministratore di SharePoint (form di associazione) e quando il flusso di lavoro viene avviato dall'utente (form di avvio).

 Questa procedura dettagliata descrive uno scenario in cui un utente vuole creare un flusso di lavoro di approvazione delle note spese presenta i requisiti seguenti:

- Quando il flusso di lavoro è associato a un elenco, l'amministratore viene visualizzato un form di associazione in cui immettere un limite di dollari per spese.

- I dipendenti caricare i rapporti spese nell'elenco di documenti condivisi, avviare il flusso di lavoro e quindi immettere il costo totale nel form di avvio del flusso di lavoro.

- Se un rapporto spese dipendente totale supera il limite predefinito dell'amministratore, viene creata un'attività per il responsabile approvazione della nota spese. Tuttavia, se expense report totale un dipendente è minore o uguale al limite di spesa, viene scritto un messaggio di approvazione automatica all'elenco cronologia del flusso di lavoro.

  Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un progetto di flusso di lavoro sequenziale di definizione elenco di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- Creazione di una pianificazione del flusso di lavoro.

- La gestione degli eventi di attività del flusso di lavoro.

- Creazione di form di associazione e di avvio del flusso di lavoro.

- Associazione del flusso di lavoro.

- Avviare manualmente il flusso di lavoro.

> [!NOTE]
> Sebbene questa procedura dettagliata Usa un progetto di flusso di lavoro sequenziale, il processo è lo stesso per flussi di lavoro di stato.
>
> Inoltre, il computer potrebbe mostrare nomi o i percorsi per alcune delle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementi dell'interfaccia utente nelle istruzioni seguenti. Il [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] edizione in uso e le impostazioni che consentono di determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Creare un progetto di flusso di lavoro sequenziale di SharePoint
 In primo luogo, creare un progetto di flusso di lavoro sequenziale in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Flusso di lavoro sequenza è una serie di passaggi eseguiti in ordine fino al termine dell'ultima attività. In questa procedura si creerà un flusso di lavoro sequenza che si applica all'elenco di documenti condivisi in SharePoint. Creazione guidata del flusso di lavoro consente di associare il flusso di lavoro con il sito o la definizione di elenco e consente di determinare quando verrà avviato il flusso di lavoro.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Per creare un progetto di flusso di lavoro sequenziale di SharePoint

1. Nella barra dei menu, scegliere **File** > **New** > **progetto** per visualizzare il **nuovo progetto** nella finestra di dialogo.

2. Espandere la **SharePoint** nodo sotto **Visual c#** o **Visual Basic**, quindi scegliere il **2010** nodo.

3. Nel **modelli** riquadro, scegliere il **progetto SharePoint 2010** modello di progetto.

4. Nel **Name** casella, immettere **ExpenseReport** e quindi scegliere il **OK** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzata.

5. Nel **specificare il livello di sito e la sicurezza per il debug** pagina, scegliere il **Distribuisci come soluzione farm** pulsante di opzione e quindi scegliere il **fine** pulsante per accettare il sito di livello e predefinito trust.

     Questo passaggio imposta anche il livello di attendibilità per la soluzione come soluzione farm, che è l'unica opzione disponibile per i progetti di flusso di lavoro.

6. Scegliere il nodo di progetto in **Esplora soluzioni**.

7. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

8. In presenza di una **Visual c#** o **Visual Basic**, espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.

9. Nel **modelli** riquadro, scegliere **flusso di lavoro sequenziale (solo soluzione Farm)** modello e quindi scegliere il **Add** pulsante.

     Il **Personalizzazione guidata SharePoint** viene visualizzata.

10. Nel **specificare il nome del flusso di lavoro per il debug** pagina, accettare il nome predefinito (**ExpenseReport - Workflow1**). Mantenere il valore di tipo modello del flusso di lavoro predefinito (**flusso di lavoro elenco)** . Fare clic su **Avanti**.

11. Nel **preferisci Visual Studio per associare automaticamente il flusso di lavoro in una sessione di debug?** pagina, deselezionare la casella che consente di associare automaticamente il modello di flusso di lavoro se è selezionata.

     Questo passaggio consente di associare manualmente il flusso di lavoro con l'elenco di documenti condivisi in un secondo momento che visualizza il form di associazione.

12. Scegliere il **fine** pulsante.

## <a name="add-an-association-form-to-the-workflow"></a>Aggiungere un form di associazione al flusso di lavoro
 A questo punto, creare una. Form di associazione di ASPX che viene visualizzato quando l'amministratore di SharePoint associa prima di tutto il flusso di lavoro a un documento di nota spese.

#### <a name="to-add-an-association-form-to-the-workflow"></a>Per aggiungere un form di associazione al flusso di lavoro

1. Scegliere il **Workflow1** nodo **Esplora soluzioni**.

2. Nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento** per visualizzare la **Aggiungi nuovo elemento** nella finestra di dialogo.

3. Nella visualizzazione albero della finestra di dialogo, espandere **Visual c#** o **Visual Basic** (a seconda del linguaggio del progetto), espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.

4. Nell'elenco dei modelli, scegliere il **Form di associazione del flusso di lavoro** modello.

5. Nel **Name** testo casella, immettere **ExpenseReportAssocForm**.

6. Scegliere il **Add** pulsante per aggiungere il form al progetto.

## <a name="designing-and-coding-the-association-form"></a>Progettazione e codifica form di associazione
 In questa procedura si fornisce funzionalità per il form di associazione mediante l'aggiunta di controlli e codice a esso.

#### <a name="to-design-and-code-the-association-form"></a>Progettare e scrivere il codice il form di associazione

1. Nel form di associazione (ExpenseReportAssocForm), individuare il `asp:Content` elemento avente `ID="Main"`.

2. Direttamente dopo la prima riga in questo elemento di contenuto, aggiungere il codice seguente per creare un'etichetta e una casella di testo che richiede il limite di approvazione delle spese (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Espandere la **ExpenseReportAssocForm** del file in **Esplora soluzioni** per visualizzare i file dipendenti.

    > [!NOTE]
    > Se il progetto si trova in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], è necessario scegliere il **Visualizza tutti i file** pulsante per eseguire questo passaggio.

4. Aprire il menu di scelta rapida per il file ExpenseReportAssocForm e scegliere **Visualizza codice**.

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

## <a name="add-an-initiation-form-to-the-workflow"></a>Aggiungere un modulo di avvio per il flusso di lavoro
 Successivamente, creare il form di avvio che viene visualizzato quando gli utenti eseguono il flusso di lavoro per le note spese.

#### <a name="to-create-an-initiation-form"></a>Per creare un form di avvio

1. Scegliere il **Workflow1** nodo **Esplora soluzioni**.

2. Nella barra dei menu, scegliere **Project** > **Aggiungi nuovo elemento** visualizzare il **Aggiungi nuovo elemento** nella finestra di dialogo.

3. Nella visualizzazione albero della finestra di dialogo, espandere **Visual c#** o **Visual Basic** (a seconda del linguaggio del progetto), espandere il **SharePoint** nodo, quindi scegliere il **2010** nodo.

4. Nell'elenco dei modelli, scegliere il **Form di avvio del flusso di lavoro** modello.

5. Nel **Name** testo casella, immettere **ExpenseReportInitForm**.

6. Scegliere il **Add** pulsante per aggiungere il form al progetto.

## <a name="designing-and-coding-the-initiation-form"></a>Progettazione e codifica il form di avvio
 Successivamente, introducono funzionalità per il form di avvio tramite l'aggiunta di controlli e codice a esso.

#### <a name="to-code-the-initiation-form"></a>Per codificare il form di avvio

1. Nel form di avvio (ExpenseReportInitForm), individuare il `asp:Content` elemento contenente `ID="Main"`.

2. Subito dopo la prima riga in questo elemento di contenuto, aggiungere il codice seguente per creare un'etichetta e una casella di testo che visualizza il limite di approvazione delle spese (*AutoApproveLimit*) che è stato immesso in form di associazione e un'altra etichetta e Nella casella di testo per la richiesta per il totale delle spese (*ExpenseTotal*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Espandere la **ExpenseReportInitForm** del file in **Esplora soluzioni** per visualizzare i file dipendenti.

4. Aprire il menu di scelta rapida per il file ExpenseReportInitForm e scegliere **Visualizza codice**.

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

## <a name="cutomize-the-workflow"></a>Personalizza il flusso di lavoro
 Successivamente, Personalizza il flusso di lavoro. In un secondo momento, si assocerà due forme al flusso di lavoro.

#### <a name="to-customize-the-workflow"></a>Per personalizzare il flusso di lavoro

1. Visualizzare il flusso di lavoro nella finestra di progettazione del flusso di lavoro aprendo Workflow1 nel progetto.

2. Nel **casella degli strumenti**, espandere il **Windows Workflow v3.0** nodo e individuare il **IfElse** attività.

3. Aggiungere questa attività per il flusso di lavoro effettuando una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per il **IfElse** attività, scegliere **copia**, aprire il menu di scelta rapida per la riga sotto il **onWorkflowActivated1** attività nella finestra di progettazione del flusso di lavoro, e quindi scegliere **Incolla**.

    - Trascinare il **IfElse** attività dal **della casella degli strumenti**e connetterla alla riga sotto il **onWorkflowActiviated1** attività nella finestra di progettazione del flusso di lavoro.

4. Nella casella degli strumenti espandere il **flusso di lavoro SharePoint** nodo e individuare le **CreateTask** attività.

5. Aggiungere questa attività per il flusso di lavoro effettuando una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per il **CreateTask** attività, scegliere **copia**, aprire il menu di scelta rapida per uno dei due **Rilascia attività qui** aree all'interno di  **Attività IfElseActivity1** nella finestra di progettazione del flusso di lavoro, quindi scegliere **Incolla**.

    - Trascinare il **CreateTask** attività dalle **della casella degli strumenti** su uno dei due **Rilascia attività qui** aree all'interno di **attività IfElseActivity1**.

6. Nel **delle proprietà** finestra, immettere un valore della proprietà *taskToken* per il **CorrelationToken** proprietà.

7. Espandere la **CorrelationToken** proprietà facendo clic sul segno più (![più di TreeView](../sharepoint/media/plus.gif "più di TreeView")) accanto a esso.

8. Scegliere la freccia a discesa nel **OwnerActivityName da parte** sub proprietà e impostare le *Workflow1* valore.

9. Scegliere il **TaskId** proprietà, quindi scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) per visualizzare il **Associa proprietà** nella finestra di dialogo.

10. Scegliere il **associare a un nuovo membro** scheda, scegliere il **campo creare** pulsante di opzione e quindi scegliere il **OK** pulsante.

11. Scegliere il **TaskProperties** proprietà, quindi scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ellisse di ASP.NET Mobile Designer")) per visualizzare il  **Associare proprietà** nella finestra di dialogo.

12. Scegliere il **associare a un nuovo membro** scheda, scegliere il **campo creare** pulsante di opzione e quindi scegliere il **OK** pulsante.

13. Nel **casella degli strumenti**, espandere il **flusso di lavoro SharePoint** nodo e individuare il **LogToHistoryListActivity** attività.

14. Aggiungere questa attività per il flusso di lavoro effettuando una delle operazioni seguenti:

    - Aprire il menu di scelta rapida per il **LogToHistoryListActivity** attività, scegliere **copia**, aprire il menu di scelta rapida per gli altri **Rilascia attività qui** area all'interno di **Attività IfElseActivity1** nella finestra di progettazione del flusso di lavoro, quindi scegliere **incollare**.

    - Trascinare il **LogToHistoryListActivity** attività dalle **della casella degli strumenti**e trascinarlo in altra **Rilascia attività qui** area all'interno di **attività IfElseActivity1** .

## <a name="add-code-to-the-workflow"></a>Aggiungere codice al flusso di lavoro
 Aggiungere quindi codice al flusso di lavoro per assegnargli una funzionalità.

#### <a name="to-add-code-to-the-workflow"></a>Per aggiungere codice al flusso di lavoro

1. Aprire il menu di scelta rapida per il **createTask1** attività nella finestra di progettazione del flusso di lavoro, quindi scegliere **Visualizza codice**.

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
    > Nel codice, sostituire `somedomain\\someuser` con un nome di dominio e utente per il quale verrà creata un'attività, ad esempio, "`Office\\JoeSch`". Per il test è più semplice usare l'account che con cui si sta sviluppando.

3. Di seguito il `MethodInvoking` metodo, aggiungere l'esempio seguente:

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

4. Nella finestra di progettazione del flusso di lavoro, scegliere il **ifElseBranchActivity1** attività.

5. Nel **delle proprietà** finestra, scegliere la freccia a discesa del **condizione** proprietà e quindi impostare il *condizione di codice* valore.

6. Espandere la **Condition** proprietà facendo clic sul segno più (![più di TreeView](../sharepoint/media/plus.gif "più di TreeView")) accanto a esso, quindi impostare il relativo valore su *checkApprovalNeeded* .

7. Nella finestra di progettazione del flusso di lavoro, aprire il menu di scelta rapida per il **logToHistoryListActivity1** attività, quindi scegliere **genera gestori** per generare un metodo vuoto per il `MethodInvoking` evento.

8. Sostituire il `MethodInvoking` codice con quanto segue:

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

9. Scegliere il **F5** chiave per eseguire il debug del programma.

     Si compila l'applicazione, pacchetto, lo distribuisce, attivate le funzionalità, viene riciclato il [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] pool di applicazioni e quindi avviare il browser in corrispondenza della posizione specificato nel **Url del sito** proprietà.

## <a name="associating-the-workflow-to-the-documents-list"></a>Associare il flusso di lavoro all'elenco di documenti
 Successivamente, visualizzare il form di associazione del flusso di lavoro associando il flusso di lavoro con il **SharedDocuments** elenco nel sito di SharePoint.

#### <a name="to-associate-the-workflow"></a>Per associare il flusso di lavoro

1. Scegliere il **documenti condivisi** collegamento sulla barra Avvio veloce.

2. Scegliere il **Library** sul collegamento il **Strumenti raccolta** scheda e quindi scegliere il **impostazioni libreria** pulsante della barra multifunzione.

3. Nel **autorizzazioni e gestione** keychains il **le impostazioni del flusso di lavoro** collegamento e quindi scegliere il **aggiungere un flusso di lavoro** sul collegamento il **iflussidilavoro** pagina.

4. Nell'elenco superiore nella pagina delle impostazioni del flusso di lavoro, scegliere il **ExpenseReport - Workflow1** modello.

5. Nel campo successivo, immettere **ExpenseReportWorkflow** e quindi scegliere il **successivo** pulsante.

     In questo modo il flusso di lavoro con il **documenti condivisi** elenco e visualizza il form di associazione del flusso di lavoro.

6. Nel **limite di approvazione automatica** testo casella, immettere **1200** e quindi scegliere il **Associa flusso di lavoro** pulsante.

## <a name="start-the-workflow"></a>Avviare il flusso di lavoro
 Associare il flusso di lavoro a uno dei documenti nella **documenti condivisi** elenco per visualizzare il form di avvio del flusso di lavoro.

#### <a name="to-start-the-workflow"></a>Per avviare il flusso di lavoro

1. Nella pagina di SharePoint, scegliere il **Home** pulsante.

2. Scegliere il **documenti condivisi** collegamento sulla barra Avvio veloce per visualizzare i **documenti condivisi** elenco.

3. Scegliere il **documenti** sul collegamento il **strumenti per le raccolte** scheda nella parte superiore della pagina e quindi scegliere il **Carica documento** pulsante della barra multifunzione per caricare un nuovo documento nel **Documenti condivisi** elenco.

4. Nel **Carica documento** finestra di dialogo scegliere la **Sfoglia** pulsante scegliere qualsiasi file di documento, scegliere il **Open** pulsante e quindi scegliere il **OK** pulsante.

     È possibile modificare le impostazioni per il documento nella finestra di dialogo, ma lasciare i valori predefiniti, scegliere il **salvare** pulsante.

5. Scegliere il documento caricato, scegliere la freccia a discesa visualizzato e quindi sceglie il **flussi di lavoro** elemento.

6. Scegliere l'immagine accanto ExpenseReportWorkflow.

     Ciò consente di visualizzare il form di avvio del flusso di lavoro. (Si noti che il valore visualizzato nei **limite di approvazione automatica** casella è di sola lettura poiché è stato immesso nel form di associazione.)

7. Nel **spese totali** testo casella, immettere **1600**e quindi scegliere il **Avvia flusso di lavoro** pulsante.

     Ciò consente di visualizzare il **documenti condivisi** elencare di nuovo. Una nuova colonna denominata **ExpenseReportWorkflow** con il valore **Completed** viene aggiunto all'elemento di flusso di lavoro appena avviata.

8. Scegliere la freccia giù accanto al documento caricato e quindi scegliere il **flussi di lavoro** elemento per visualizzare la pagina di stato del flusso di lavoro. Scegliere il **Completed** valore sotto **flussi di lavoro completati**. L'attività elencata sotto le **attività** sezione.

9. Scegliere il titolo dell'attività per visualizzarne i dettagli.

10. Tornare al **SharedDocuments** elencare e riavviare il flusso di lavoro, usando lo stesso documento o uno diverso.

11. Immettere un importo nella pagina di avvio che è minore o uguale a quello immesso nella pagina di associazione (**1200**).

     In questo caso, invece di un'attività viene creata una voce nell'elenco della cronologia. La voce viene visualizzata nella **Cronologia flussi di lavoro** sezione della pagina stato del flusso di lavoro. Si noti il messaggio nel **risultato** colonna dell'evento della cronologia. Contiene il testo immesso nel `logToHistoryListActivity1.MethodInvoking` eventi che includono la quantità che è stata approvata automaticamente.

## <a name="next-steps"></a>Passaggi successivi
 Altre informazioni su come creare modelli di flusso di lavoro vedere gli argomenti seguenti:

- Per altre informazioni sui flussi di lavoro di SharePoint, vedere [flussi di lavoro di Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).

## <a name="see-also"></a>Vedere anche
- [Creare soluzioni di flusso di lavoro di SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Procedura dettagliata: Aggiungere una pagina dell'applicazione a un flusso di lavoro](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
