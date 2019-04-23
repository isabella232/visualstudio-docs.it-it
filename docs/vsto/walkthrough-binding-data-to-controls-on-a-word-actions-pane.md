---
title: 'Procedura dettagliata: Associare dati a controlli in un riquadro azioni di Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7069da816d8f693fc38856d1218f5f9f6284dd4c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063608"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Procedura dettagliata: Associare dati a controlli in un riquadro azioni di Word
  Questa procedura dettagliata viene descritta l'associazione dati a controlli in un riquadro azioni di Word. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un riquadro azioni con controlli Windows Form che vengono associati ai dati.

- Utilizzo di una relazione master-Details per visualizzare i dati nei controlli.

- Visualizzare il riquadro azioni quando si apre l'applicazione.

> [!NOTE]
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Accesso a un server con il database di esempio Northwind di SQL Server.

- Autorizzazioni per leggere e scrivere nel database di SQL Server.

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto documento di Word con il nome **My Word Actions Pane**. Nella procedura guidata, selezionare **creare un nuovo documento**.

     Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **My Word Actions Pane** progetto al **Esplora soluzioni**.

## <a name="add-controls-to-the-actions-pane"></a>Aggiungere controlli al riquadro azioni
 Per questa procedura dettagliata, è necessario un controllo riquadro azioni che contiene controlli Windows Form con associazione a dati. Aggiungere un'origine dati al progetto e quindi trascinare controlli dal **Zdroje dat** finestra al controllo del riquadro azioni.

### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo riquadro azioni

1. Selezionare il **My Word Actions Pane** del progetto nelle **Esplora soluzioni**.

2. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nel **Aggiungi nuovo elemento** finestra di dialogo **controllo del riquadro azioni**, denominarlo **ActionsControl**e quindi fare clic su **Aggiungi**.

### <a name="to-add-a-data-source-to-the-project"></a>Per aggiungere un'origine dati al progetto

1. Se il **Zdroje dat** finestra non è visibile, visualizzarla, dalla barra dei menu, scegliendo **View** > **Other Windows**  >   **Zdroje dat**.

   > [!NOTE]
   >  Se **Mostra origini dati** non è disponibile, fare clic sul documento di Word e quindi riprovare.

2. Fare clic su **Aggiungi nuova origine dati** per avviare la **configurazione guidata origine dati**.

3. Selezionare **Database** e quindi fare clic su **successivo**.

4. Selezionare una connessione dati al database di SQL Server di esempio Northwind, oppure aggiungere una nuova connessione usando il **nuova connessione** pulsante.

5. Scegliere **Avanti**.

6. Deselezionare l'opzione per salvare la connessione, se è selezionata, quindi scegliere **successivo**.

7. Espandere la **tabelle** nodo il **degli oggetti di Database** finestra.

8. Selezionare la casella di controllo accanto al **Suppliers** e **prodotti** tabelle.

9. Scegliere **Fine**.

   La procedura guidata aggiunge i **Suppliers** tabella e **prodotti** alla tabella il **Zdroje dat** finestra. Aggiunge anche un set di dati tipizzato al progetto che è visibile nel **Esplora soluzioni**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Per aggiungere controlli Windows Form con associazione a dati a un controllo riquadro azioni

1. Nel **Zdroje dat** finestra, espandere il **Suppliers** tabella.

2. Fare clic sulla freccia giù sul **nome società** nodo e selezionare **ComboBox**.

3. Trascinare **CompanyName** dalle **Zdroje dat** finestra al controllo del riquadro azioni.

     Oggetto <xref:System.Windows.Forms.ComboBox> controllo viene creato nel controllo del riquadro azioni. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominate `SuppliersBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> vengono aggiunti al progetto nella barra dei componenti.

4. Selezionare `SuppliersBindingNavigator` nella **componente** sulla barra delle applicazioni e premere **eliminare**. Non si userà il `SuppliersBindingNavigator` in questa procedura dettagliata.

    > [!NOTE]
    >  L'eliminazione di `SuppliersBindingNavigator` non rimuove tutto il codice generato per tale. È possibile rimuovere questo codice.

5. Spostare la casella combinata in modo che sia sotto l'etichetta e modificare il **dimensioni** proprietà **171, 21**.

6. Nel **Zdroje dat** finestra, espandere il **prodotti** tabella che rappresenta un elemento figlio del **Suppliers** tabella.

7. Fare clic sulla freccia giù sul **ProductName** nodo e selezionare **ListBox**.

8. Trascinare **ProductName** al controllo del riquadro azioni.

     Oggetto <xref:System.Windows.Forms.ListBox> controllo viene creato nel controllo del riquadro azioni. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominato `ProductBindingSource` e un adattatore di tabella vengono aggiunti al progetto nella barra dei componenti.

9. Spostare la casella di riepilogo in modo che sia sotto l'etichetta e modificare il **dimensioni** proprietà **171, 95**.

10. Trascinare un <xref:System.Windows.Forms.Button> dal **casella degli strumenti** nel riquadro azioni di controllo e posizionarla sotto la casella di riepilogo.

11. Fare doppio clic il <xref:System.Windows.Forms.Button>, fare clic su **proprietà** nel menu di scelta rapida e modificare le proprietà seguenti.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Name**|**Inserisci**|
    |**per**|**Inserisci**|

12. Ridimensionare il controllo utente per adattarlo ai controlli.

## <a name="set-up-the-data-source"></a>Configurare l'origine dati
 Per configurare l'origine dati, aggiungere il codice per il <xref:System.Windows.Forms.UserControl.Load> eventi di controllo del riquadro azioni per riempire il controllo con dati provenienti dal <xref:System.Data.DataTable>e impostare il <xref:System.Windows.Forms.Binding.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> proprietà per ogni controllo.

### <a name="to-load-the-control-with-data"></a>Per caricare i dati nel controllo

1. Nel <xref:System.Windows.Forms.UserControl.Load> gestore dell'evento del `ActionsControl` classe, aggiungere il codice seguente.

     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]

2. In c#, è necessario collegare il gestore eventi per il <xref:System.Windows.Forms.UserControl.Load> evento. È possibile inserire il codice nel `ActionsControl` costruttore, dopo la chiamata a `InitializeComponent`. Per altre informazioni su come creare gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]

### <a name="to-set-data-binding-properties-of-the-controls"></a>Impostare le proprietà di associazione di dati dei controlli

1. Selezionare il controllo `CompanyNameComboBox`.

2. Nel **delle proprietà** finestra, fare clic sul pulsante a destra del **DataSource** proprietà e selezionare **suppliersBindingSource**.

3. Fare clic sul pulsante a destra del **DisplayMember** proprietà e selezionare **CompanyName**.

4. Espandere la **DataBindings** proprietà, fare clic sul pulsante a destra del **testo** proprietà e selezionare **None**.

5. Selezionare il controllo `ProductNameListBox`.

6. Nel **delle proprietà** finestra, fare clic sul pulsante a destra del **DataSource** proprietà e selezionare **productsBindingSource**.

7. Fare clic sul pulsante a destra del **DisplayMember** proprietà e selezionare **ProductName**.

8. Espandere la **DataBindings** proprietà, fare clic sul pulsante a destra del **SelectedValue** proprietà e selezionare **None**.

## <a name="add-a-method-to-insert-data-into-a-table"></a>Aggiungere un metodo per inserire dati in una tabella
 L'attività successiva è come leggere i dati da controlli associati e popolare una tabella nel documento di Word. In primo luogo, creare una stored procedure per formattare le intestazioni della tabella e quindi aggiungere il `AddData` metodo per creare e formattare una tabella di Word.

### <a name="to-format-the-table-headings"></a>Per formattare le intestazioni della tabella

1. Nel `ActionsControl` classe, creare un metodo per formattare le intestazioni della tabella.

     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]

### <a name="to-create-the-table"></a>Per creare la tabella

1. Nel `ActionsControl` classe, scrivere un metodo che verrà creata una tabella se non è già presente e aggiungere i dati nel riquadro azioni per la tabella.

     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]

### <a name="to-insert-text-into-a-word-table"></a>Per inserire testo in una tabella di Word

1. Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del **Inserisci** pulsante.

     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]

2. In c#, è necessario creare un gestore eventi per il <xref:System.Windows.Forms.Control.Click> evento del pulsante.  È possibile inserire il codice nel <xref:System.Windows.Forms.UserControl.Load> gestore dell'evento del `ActionsControl` classe.

     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]

## <a name="show-the-actions-pane"></a>Visualizzare il riquadro azioni
 Nel riquadro azioni diventa visibile dopo che i controlli vengono aggiunti a esso.

### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni

1. Nel **Esplora soluzioni**, fare doppio clic su **ThisDocument. vb** oppure **ThisDocument.cs**, quindi fare clic su **Visualizza codice** menu di scelta rapida.

2. Creare una nuova istanza del controllo nella parte superiore del `ThisDocument` classe in modo che risulti simile al seguente.

     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]

3. Aggiungere il codice per il <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore dell'evento di `ThisDocument` in modo che risulti simile al seguente.

     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare il documento per verificare che venga visualizzato il riquadro azioni quando viene aperto il documento. Verificare la relazione master/dettaglio nei controlli del riquadro azioni e assicurarsi che i dati vengano inseriti in una parola tabella quando la **Inserisci** si fa clic sul pulsante.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Verificare che il riquadro azioni sia visibile.

3. Selezionare una società nella casella combinata e verificare che gli elementi di **prodotti** casella di riepilogo cambino.

4. Selezionare un prodotto, fare clic su **Inserisci** nel riquadro azioni e verificare che i dettagli del prodotto vengono aggiunti alla tabella di Word.

5. Inserire ulteriori prodotti da società diverse.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base di associazione dati a controlli in un riquadro azioni in Word. Ecco alcune possibili attività successive:

- Associazione dati a controlli in Excel. Per altre informazioni, vedere [Procedura dettagliata: Associare dati a controlli in un riquadro azioni di Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

- La distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Procedura: Aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
