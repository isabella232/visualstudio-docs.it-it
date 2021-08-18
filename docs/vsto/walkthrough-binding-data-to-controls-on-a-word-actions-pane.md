---
title: 'Procedura dettagliata: Associare dati ai controlli in un riquadro azioni di Word'
description: Associare i dati ai controlli in un riquadro azioni in Microsoft Word. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 34408a3f1e08165a4269c0f9741d0d645f4576cc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032134"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Procedura dettagliata: Associare dati ai controlli in un riquadro azioni di Word
  Questa procedura dettagliata illustra data binding controlli in un riquadro azioni in Word. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Creazione di un riquadro azioni con Windows form associati ai dati.

- Uso di una relazione master/dettagli per visualizzare i dati nei controlli.

- Visualizzare il riquadro azioni all'apertura dell'applicazione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Accesso a un server con il database di SQL Server Northwind.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server database.

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nel creare un progetto Documento di Word.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto Documento di Word con il nome **My Word Actions Pane**. Nella procedura guidata selezionare **Crea un nuovo documento**.

     Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre il nuovo documento di Word nella finestra di progettazione e aggiunge il **progetto My Word Actions Pane** a **Esplora soluzioni**.

## <a name="add-controls-to-the-actions-pane"></a>Aggiungere controlli al riquadro azioni
 Per questa procedura dettagliata, è necessario un controllo riquadro azioni che contiene controlli form associati Windows dati. Aggiungere un'origine dati al progetto e quindi trascinare i controlli dalla finestra **Origini** dati al controllo riquadro azioni.

### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo riquadro azioni

1. Selezionare il **progetto My Word Actions Pane** in **Esplora soluzioni**.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo elemento** selezionare Controllo **riquadro** azioni , assegnare al controllo il nome **ActionsControl** e quindi fare clic su **Aggiungi**.

### <a name="to-add-a-data-source-to-the-project"></a>Per aggiungere un'origine dati al progetto

1. Se la **finestra Origini** dati non è visibile, visualizzarla da sulla barra dei menu, scegliendo Visualizza Windows  >    >  **origini dati**.

   > [!NOTE]
   > Se **Mostra origini dati** non è disponibile, fare clic sul documento di Word e quindi controllare di nuovo.

2. Fare **clic su Aggiungi nuova origine dati** per avviare la Configurazione guidata origine **dati**.

3. Selezionare **Database** e quindi fare clic su **Avanti.**

4. Selezionare una connessione dati al database di esempio Northwind SQL Server o aggiungere una nuova connessione usando il **pulsante Nuova** connessione.

5. Fare clic su **Avanti**.

6. Deselezionare l'opzione per salvare la connessione, se selezionata, e quindi fare clic su **Avanti.**

7. Espandere il **nodo** Tabelle nella finestra **Oggetti di** database .

8. Selezionare la casella di controllo accanto **alle tabelle Suppliers** **e Products.**

9. Fare clic su **Fine**.

   La procedura guidata aggiunge **la tabella Suppliers** **e la tabella Products** alla finestra **Origini** dati. Aggiunge anche un set di dati tipizzato al progetto visibile in **Esplora soluzioni**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Per aggiungere controlli Form associati Windows dati a un controllo riquadro azioni

1. Nella finestra **Origini dati** espandere la **tabella Suppliers.**

2. Fare clic sulla freccia a discesa nel **nodo Nome** società e selezionare **ComboBox**.

3. Trascinare **CompanyName** dalla **finestra Origini** dati al controllo riquadro azioni.

     Nel <xref:System.Windows.Forms.ComboBox> controllo del riquadro azioni viene creato un controllo . Allo stesso tempo, un denominato , un adattatore di tabella e un oggetto vengono aggiunti al progetto nella <xref:System.Windows.Forms.BindingSource> `SuppliersBindingSource` barra dei <xref:System.Data.DataSet> componenti.

4. Selezionare `SuppliersBindingNavigator` nella barra **dei** componenti e premere **CANC.** Non verrà utilizzato in `SuppliersBindingNavigator` questa procedura dettagliata.

    > [!NOTE]
    > `SuppliersBindingNavigator`L'eliminazione di non rimuove tutto il codice generato. È possibile rimuovere questo codice.

5. Spostare la casella combinata in modo che sia sotto l'etichetta e impostare la **proprietà Size** su **171, 21**.

6. Nella finestra **Origini** dati espandere la **tabella Products** figlio della **tabella Suppliers.**

7. Fare clic sulla freccia a discesa nel **nodo ProductName** e selezionare **ListBox**.

8. Trascinare **ProductName** nel controllo riquadro azioni.

     Nel <xref:System.Windows.Forms.ListBox> controllo del riquadro azioni viene creato un controllo . Allo stesso tempo, un adattatore denominato e un adattatore di tabella vengono <xref:System.Windows.Forms.BindingSource> aggiunti al progetto nella barra dei `ProductBindingSource` componenti.

9. Spostare la casella di riepilogo in modo che si trova sotto l'etichetta e impostare la **proprietà Size** su **171.95**.

10. Trascinare <xref:System.Windows.Forms.Button> un oggetto dalla Casella **degli** strumenti nel controllo riquadro azioni e posizionarlo sotto la casella di riepilogo.

11. Fare clic con il pulsante destro del mouse su , scegliere Proprietà dal menu di scelta <xref:System.Windows.Forms.Button> rapida e modificare le proprietà seguenti. 

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**Inserimento**|
    |**Text**|**Inserimento**|

12. Ridimensionare il controllo utente per adattarlo ai controlli.

## <a name="set-up-the-data-source"></a>Configurare l'origine dati
 Per configurare l'origine dati, aggiungere codice all'evento del controllo riquadro azioni per riempire il controllo con i dati di e impostare le proprietà e <xref:System.Windows.Forms.UserControl.Load> <xref:System.Data.DataTable> per ogni <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> controllo.

### <a name="to-load-the-control-with-data"></a>Per caricare il controllo con dati

1. Nel gestore <xref:System.Windows.Forms.UserControl.Load> eventi della classe aggiungere il codice `ActionsControl` seguente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet1":::

2. In C# è necessario associare il gestore eventi <xref:System.Windows.Forms.UserControl.Load> all'evento . È possibile inserire questo codice nel `ActionsControl` costruttore dopo la chiamata a `InitializeComponent` . Per altre informazioni su come creare gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office progetti .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet33":::

### <a name="to-set-data-binding-properties-of-the-controls"></a>Per impostare data binding proprietà dei controlli

1. Selezionare il controllo `CompanyNameComboBox`.

2. Nella finestra **Proprietà** fare clic sul pulsante a destra della **proprietà DataSource** e selezionare **suppliersBindingSource**.

3. Fare clic sul pulsante a destra della **proprietà DisplayMember** e selezionare **CompanyName**.

4. Espandere la **proprietà DataBindings,** fare clic sul pulsante a destra della **proprietà Text** e selezionare **Nessuno.**

5. Selezionare il controllo `ProductNameListBox`.

6. Nella finestra **Proprietà** fare clic sul pulsante a destra della **proprietà DataSource** e selezionare **productsBindingSource**.

7. Fare clic sul pulsante a destra della **proprietà DisplayMember** e selezionare **ProductName**.

8. Espandere la **proprietà DataBindings,** fare clic sul pulsante a destra della **proprietà SelectedValue** e selezionare **Nessuno.**

## <a name="add-a-method-to-insert-data-into-a-table"></a>Aggiungere un metodo per inserire dati in una tabella
 L'attività successiva è leggere i dati dai controlli associati e popolare una tabella nel documento di Word. Creare prima di tutto una procedura per formattare le intestazioni nella tabella e quindi aggiungere il metodo per creare e `AddData` formattare una tabella di Word.

### <a name="to-format-the-table-headings"></a>Per formattare le intestazioni di tabella

1. Nella classe `ActionsControl` creare un metodo per formattare le intestazioni della tabella.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet2":::

### <a name="to-create-the-table"></a>Per creare la tabella

1. Nella classe scrivere un metodo che creerà una tabella, se non ne esiste già una, e aggiungere dati dal riquadro `ActionsControl` azioni alla tabella.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet3":::

### <a name="to-insert-text-into-a-word-table"></a>Per inserire testo in una tabella di Word

1. Aggiungere il codice seguente al <xref:System.Windows.Forms.Control.Click> gestore eventi del **pulsante** Inserisci.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet4":::

2. In C# è necessario creare un gestore eventi per <xref:System.Windows.Forms.Control.Click> l'evento del pulsante.  È possibile inserire questo codice nel <xref:System.Windows.Forms.UserControl.Load> gestore eventi della classe `ActionsControl` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet5":::

## <a name="show-the-actions-pane"></a>Visualizzare il riquadro azioni
 Il riquadro azioni diventa visibile dopo l'aggiunta dei controlli.

### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisDocument.vb** o **ThisDocument.cs** e quindi scegliere Visualizza **codice** dal menu di scelta rapida.

2. Creare una nuova istanza del controllo all'inizio della classe in modo che `ThisDocument` sia simile all'esempio seguente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet6":::

3. Aggiungere codice al gestore <xref:Microsoft.Office.Tools.Word.Document.Startup> eventi di in modo che sia simile `ThisDocument` all'esempio seguente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet7":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare il documento per verificare che il riquadro azioni venga visualizzato all'apertura del documento. Verificare la relazione master/dettagli nei controlli del riquadro azioni e assicurarsi che i  dati siano popolati in una tabella di Word quando si fa clic sul pulsante Inserisci.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Verificare che il riquadro azioni sia visibile.

3. Selezionare una società nella casella combinata e verificare che gli elementi nella casella di riepilogo **Prodotti** cambino.

4. Selezionare un prodotto, fare **clic su** Inserisci nel riquadro azioni e verificare che i dettagli del prodotto siano stati aggiunti alla tabella in Word.

5. Inserire prodotti aggiuntivi di varie aziende.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'associazione di dati ai controlli in un riquadro azioni in Word. Ecco alcune possibili attività successive:

- Associazione di dati a controlli in Excel. Per altre informazioni, vedere [Procedura dettagliata: Associare dati a controlli in un riquadro Excel azioni.](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)

- Distribuzione del progetto. Per altre informazioni, vedere [Distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Vedi anche
- [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)
- [Procedura: Aggiungere un riquadro azioni a documenti di Word o Excel cartelle di lavoro](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Associare dati a controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
