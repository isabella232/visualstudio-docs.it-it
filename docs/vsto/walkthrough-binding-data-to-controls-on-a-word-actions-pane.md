---
title: 'Procedura dettagliata: associare dati a controlli in un riquadro azioni di Word'
description: Associare dati a controlli in un riquadro azioni in Microsoft Word. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: 76dffda9b332b9b76d6c0e0a423073959bcc7a56
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526207"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Procedura dettagliata: associare dati a controlli in un riquadro azioni di Word
  Questa procedura dettagliata illustra data binding a controlli in un riquadro azioni in Word. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un riquadro azioni con Windows Forms controlli associati ai dati.

- Utilizzo di una relazione Master/Detail per visualizzare i dati nei controlli.

- Mostra il riquadro azioni all'apertura dell'applicazione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Accesso a un server con il database di esempio Northwind SQL Server.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server.

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di documento di Word con il nome **My Word Actions pane**. Nella procedura guidata selezionare **Crea un nuovo documento**.

     Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il progetto del **riquadro azioni di Word** a **Esplora soluzioni**.

## <a name="add-controls-to-the-actions-pane"></a>Aggiungere controlli al riquadro azioni
 Per questa procedura dettagliata è necessario un controllo del riquadro azioni che contiene i controlli di Windows Forms associati a dati. Aggiungere un'origine dati al progetto, quindi trascinare i controlli dalla finestra **origini dati** al controllo del riquadro azioni.

### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo del riquadro azioni

1. Selezionare il progetto **My Word Actions pane** in **Esplora soluzioni**.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare il **controllo riquadro azioni**, denominarlo **ActionsControl** e quindi fare clic su **Aggiungi**.

### <a name="to-add-a-data-source-to-the-project"></a>Per aggiungere un'origine dati al progetto

1. Se la finestra **origini dati** non è visibile, visualizzarla dalla barra dei menu scegliendo **Visualizza**  >  **altre**  >  **origini dati** di Windows.

   > [!NOTE]
   > Se **Mostra origini dati** non è disponibile, fare clic sul documento di Word, quindi eseguire di nuovo la verifica.

2. Fare clic su **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **database** e quindi fare clic su **Avanti**.

4. Selezionare una connessione dati all'esempio Northwind SQL Server database oppure aggiungere una nuova connessione usando il pulsante **nuova connessione** .

5. Fare clic su **Avanti**.

6. Deselezionare l'opzione per salvare la connessione, se selezionata, quindi fare clic su **Avanti**.

7. Espandere il nodo **tabelle** nella finestra **oggetti di database** .

8. Selezionare la casella di controllo accanto alle tabelle **Suppliers** e **Products** .

9. Fare clic su **Fine**.

   La procedura guidata consente di aggiungere la tabella **Suppliers** e **Products** alla finestra **origini dati** . Aggiunge anche un set di dati tipizzato al progetto che è visibile in **Esplora soluzioni**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Per aggiungere controlli Windows Forms associati a dati a un controllo del riquadro azioni

1. Nella finestra **origini dati** espandere la tabella **Suppliers** .

2. Fare clic sulla freccia a discesa nel nodo **nome società** e selezionare **ComboBox**.

3. Trascinare **CompanyName** dalla finestra **origini dati** al controllo del riquadro azioni.

     <xref:System.Windows.Forms.ComboBox>Viene creato un controllo nel controllo del riquadro azioni. Allo stesso tempo, un oggetto <xref:System.Windows.Forms.BindingSource> denominato `SuppliersBindingSource` , un adattatore di tabella e un oggetto <xref:System.Data.DataSet> vengono aggiunti al progetto nella barra dei componenti.

4. Selezionare `SuppliersBindingNavigator` nella barra dei **componenti** e premere **CANC**. `SuppliersBindingNavigator`In questa procedura dettagliata non verrà usato.

    > [!NOTE]
    > L'eliminazione `SuppliersBindingNavigator` di non comporta la rimozione di tutto il codice generato. È possibile rimuovere questo codice.

5. Spostare la casella combinata in modo che si trovi sotto l'etichetta e impostare la proprietà **size** su **171, 21**.

6. Nella finestra **origini dati** espandere la tabella **Products** che è un elemento figlio della tabella **Suppliers** .

7. Fare clic sulla freccia a discesa nel nodo **ProductName** e selezionare **ListBox**.

8. Trascinare **ProductName** nel controllo del riquadro azioni.

     <xref:System.Windows.Forms.ListBox>Viene creato un controllo nel controllo del riquadro azioni. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> adattatore denominato `ProductBindingSource` e una tabella vengono aggiunti al progetto nella barra dei componenti.

9. Spostare la casella di riepilogo in modo che si trovi sotto l'etichetta e impostare la proprietà **size** su **171, 95**.

10. Trascinare un <xref:System.Windows.Forms.Button> dalla **casella degli strumenti** nel controllo del riquadro azioni e posizionarlo sotto la casella di riepilogo.

11. Fare clic con il pulsante destro del mouse su <xref:System.Windows.Forms.Button> , scegliere **Proprietà** dal menu di scelta rapida e modificare le proprietà seguenti.

    |Proprietà|valore|
    |--------------|-----------|
    |**Nome**|**Inserimento**|
    |**Testo**|**Inserimento**|

12. Ridimensionare il controllo utente per adattarlo ai controlli.

## <a name="set-up-the-data-source"></a>Configurare l'origine dati
 Per configurare l'origine dati, aggiungere il codice all' <xref:System.Windows.Forms.UserControl.Load> evento del controllo del riquadro azioni in modo da riempire il controllo con i dati da <xref:System.Data.DataTable> e impostare le <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> proprietà e per ogni controllo.

### <a name="to-load-the-control-with-data"></a>Per caricare il controllo con i dati

1. Nel <xref:System.Windows.Forms.UserControl.Load> gestore eventi della `ActionsControl` classe aggiungere il codice seguente.

     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]

2. In C# è necessario alleghi il gestore eventi all' <xref:System.Windows.Forms.UserControl.Load> evento. È possibile inserire questo codice nel `ActionsControl` costruttore, dopo la chiamata a `InitializeComponent` . Per altre informazioni su come creare i gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]

### <a name="to-set-data-binding-properties-of-the-controls"></a>Per impostare data binding proprietà dei controlli

1. Selezionare il controllo `CompanyNameComboBox`.

2. Nella finestra **Proprietà** fare clic sul pulsante a destra della proprietà **DataSource** , quindi selezionare **suppliersBindingSource**.

3. Fare clic sul pulsante a destra della proprietà **DisplayMember** e selezionare **CompanyName**.

4. Espandere la proprietà **DataBindings** , fare clic sul pulsante a destra della proprietà **Text** e selezionare **None**.

5. Selezionare il controllo `ProductNameListBox`.

6. Nella finestra **Proprietà** fare clic sul pulsante a destra della proprietà **DataSource** , quindi selezionare **ProductsBindingSource**.

7. Fare clic sul pulsante a destra della proprietà **DisplayMember** e selezionare **ProductName**.

8. Espandere la proprietà **DataBindings** , fare clic sul pulsante a destra della proprietà **SelectedValue** e selezionare **None**.

## <a name="add-a-method-to-insert-data-into-a-table"></a>Aggiungere un metodo per inserire i dati in una tabella
 L'attività successiva consiste nel leggere i dati dai controlli associati e popolare una tabella nel documento di Word. Per prima cosa, creare una procedura per formattare le intestazioni nella tabella e quindi aggiungere il `AddData` metodo per creare e formattare una tabella di Word.

### <a name="to-format-the-table-headings"></a>Per formattare le intestazioni di tabella

1. Nella `ActionsControl` classe creare un metodo per formattare le intestazioni della tabella.

     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]

### <a name="to-create-the-table"></a>Per creare la tabella

1. Nella `ActionsControl` classe scrivere un metodo che creerà una tabella, se non ne esiste già uno, e aggiungere i dati dal riquadro azioni alla tabella.

     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]

### <a name="to-insert-text-into-a-word-table"></a>Per inserire testo in una tabella di Word

1. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi del pulsante **Inserisci** .

     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]

2. In C# è necessario creare un gestore eventi per l' <xref:System.Windows.Forms.Control.Click> evento del pulsante.  È possibile inserire questo codice nel <xref:System.Windows.Forms.UserControl.Load> gestore eventi della `ActionsControl` classe.

     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]

## <a name="show-the-actions-pane"></a>Mostra il riquadro azioni
 Il riquadro azioni diventa visibile dopo l'aggiunta dei controlli.

### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisDocument. vb** o **ThisDocument.cs**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.

2. Creare una nuova istanza del controllo nella parte superiore della classe in `ThisDocument` modo che abbia un aspetto simile all'esempio seguente.

     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]

3. Aggiungere il codice al <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore eventi di in `ThisDocument` modo che abbia un aspetto simile all'esempio seguente.

     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

## <a name="test-the-application"></a>Test dell'applicazione
 A questo punto è possibile testare il documento per verificare che il riquadro azioni venga visualizzato all'apertura del documento. Verificare la relazione master/dettaglio nei controlli nel riquadro azioni e assicurarsi che i dati vengano inseriti in una tabella di Word quando si fa clic sul pulsante **Inserisci** .

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Verificare che il riquadro azioni sia visibile.

3. Selezionare una società nella casella combinata e verificare che gli elementi nella casella di riepilogo **prodotti** cambino.

4. Selezionare un prodotto, fare clic su **Inserisci** nel riquadro azioni e verificare che i dettagli del prodotto vengano aggiunti alla tabella in Word.

5. Inserire prodotti aggiuntivi da diverse aziende.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base per l'associazione dei dati ai controlli in un riquadro azioni in Word. Ecco alcune possibili attività successive:

- Associazione di dati a controlli in Excel. Per ulteriori informazioni, vedere [procedura dettagliata: associare dati a controlli in un riquadro azioni di Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

- Distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
