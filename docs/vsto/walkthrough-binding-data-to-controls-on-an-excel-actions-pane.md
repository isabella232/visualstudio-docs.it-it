---
title: 'Procedura dettagliata: Associare dati a controlli in un riquadro azioni di Excel'
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
ms.openlocfilehash: de51ead9b3395df1c48f1340e27bd8c891a87fa4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56647007"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Procedura dettagliata: Associare dati a controlli in un riquadro azioni di Excel
  Questa procedura dettagliata viene descritta l'associazione dati a controlli in un riquadro azioni in Microsoft Office Excel. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Questa procedura dettagliata illustra le attività seguenti:

-   Aggiunta di controlli a un foglio di lavoro.

-   Creazione di un controllo riquadro azioni.

-   Aggiunta di controlli Windows Form con associazione a dati a un controllo riquadro azioni.

-   Quando si apre l'applicazione, che mostra il riquadro azioni.

> [!NOTE]
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

-   Accesso a un server con il database di esempio Northwind di SQL Server.

-   Autorizzazioni per leggere e scrivere nel database di SQL Server.

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nella creazione di un progetto Cartella di lavoro di Excel.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1.  Creare un progetto cartella di lavoro di Excel con il nome **riquadro di azioni di Excel personale**. Nella procedura guidata, selezionare **creare un nuovo documento**. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il **My Excel Actions Pane** progetto al **Esplora soluzioni**.

## <a name="add-a-new-data-source-to-the-project"></a>Aggiungere una nuova origine dati al progetto

### <a name="to-add-a-new-data-source-to-the-project"></a>Per aggiungere una nuova origine dati al progetto

1. Se il **Zdroje dat** finestra non è visibile, visualizzarla, dalla barra dei menu, scegliendo **View** > **Other Windows**  >   **Zdroje dat**.

2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **Database** e quindi fare clic su **successivo**.

4. Selezionare una connessione dati al database di SQL Server di esempio Northwind, oppure aggiungere una nuova connessione usando il **nuova connessione** pulsante.

5. Scegliere **Avanti**.

6. Deselezionare l'opzione per salvare la connessione, se è selezionata, quindi scegliere **successivo**.

7. Espandere la **tabelle** nodo il **degli oggetti di Database** finestra.

8. Selezionare la casella di controllo accanto al **Suppliers** tabella.

9. Espandere la **prodotti** tabelle e selezionare **ProductName**, **SupplierID**, **QuantityPerUnit**, e **UnitPrice**.

10. Scegliere **Fine**.

    La procedura guidata aggiunge i **Suppliers** tabella e **prodotti** alla tabella il **Zdroje dat** finestra. Aggiunge anche un set di dati tipizzato al progetto che è visibile nel **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro
 Successivamente, aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo e un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo per il primo foglio di lavoro.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Per aggiungere un controllo NamedRange e un controllo ListObject

1.  Verificare che il **My Excel azioni Pane.xlsx** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzato.

2.  Nel **Zdroje dat** finestra, espandere il **Suppliers** tabella.

3.  Fare clic sulla freccia giù sul **nome società** nodo e quindi fare clic su **NamedRange**.

4.  Trascinare **nome società** dalle **Zdroje dat** finestra alla cella **A2** in `Sheet1`.

     Oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo denominato `CompanyNameNamedRange` viene creato e il testo \<CompanyName > viene visualizzato nella cella **A2**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominate `suppliersBindingSource`, un adattatore di tabella e un <xref:System.Data.DataSet> vengono aggiunti al progetto. Il controllo viene associato ai <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato ai <xref:System.Data.DataSet> istanza.

5.  Nel **Zdroje dat** finestra, scorrere verso il basso oltre le colonne che sono sotto il **Suppliers** tabella. Nella parte inferiore dell'elenco è il **prodotti** tabella; è qui perché è un figlio delle **Suppliers** tabella. Selezionare questa opzione **prodotti** tabella, non quello che si trova allo stesso livello di **Suppliers** di tabella e quindi fare clic sulla freccia giù visualizzata.

6.  Fare clic su **ListObject** nell'elenco a discesa, quindi trascinare il **Products** alla cella **A6** in `Sheet1`.

     Oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> controllo denominato `ProductNameListObject` viene memorizzato nella cella **A6**. Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> denominato `productsBindingSource` e un adattatore di tabella vengono aggiunti al progetto. Il controllo viene associato ai <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato ai <xref:System.Data.DataSet> istanza.

7.  Per C# solo, selezionare **suppliersBindingSource** sulla barra dei componenti e modificare il **modificatori** proprietà **interno** nel **delle proprietà**  finestra.

## <a name="add-controls-to-the-actions-pane"></a>Aggiungere controlli al riquadro azioni
 Successivamente, è necessario un controllo riquadro azioni con una casella combinata.

### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo riquadro azioni

1.  Selezionare il **My Excel Actions Pane** del progetto **Esplora soluzioni**.

2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3.  Nel **Aggiungi nuovo elemento** finestra di dialogo **controllo del riquadro azioni**, denominarlo **ActionsControl**e fare clic su **Aggiungi**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Per aggiungere controlli Windows Form con associazione a dati a un controllo riquadro azioni

1.  Dal **controlli comuni** schede della finestra il **della casella degli strumenti**, trascinare un <xref:System.Windows.Forms.ComboBox> controllo al controllo del riquadro azioni.

2.  Modifica il **dimensioni** proprietà **171, 21**.

3.  Ridimensionare il controllo utente per adattare la casella combinata.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Associare il controllo del riquadro azioni ai dati
 In questa sezione, si verrà impostato l'origine dati del <xref:System.Windows.Forms.ComboBox> alla stessa origine dati come il <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nel foglio di lavoro.

### <a name="to-set-data-binding-properties-of-the-control"></a>Impostare le proprietà di associazione dati del controllo

1.  Fare doppio clic sul controllo riquadro azioni e quindi fare clic su **Visualizza codice**.

2.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.UserControl.Load> eventi di controllo del riquadro azioni.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3.  In C#, è necessario creare un gestore eventi per il `ActionsControl`. È possibile inserire il codice nel `ActionsControl` costruttore. Per altre informazioni sulla creazione di gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Visualizzare il riquadro azioni
 Fino a quando non si aggiunge il controllo in fase di esecuzione non è visibile nel riquadro azioni.

#### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni

1.  Nelle **Esplora soluzioni**, fare doppio clic su *ThisWorkbook. vb* oppure *ThisWorkbook.cs*, quindi fare clic su **Visualizza codice**.

2.  Creare una nuova istanza del controllo utente nel `ThisWorkbook` classe.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3.  Nel <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> gestore dell'evento di `ThisWorkbook`, aggiungere il controllo riquadro azioni.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare il documento per verificare che il riquadro azioni viene aperto quando il documento viene aperto e che i controlli hanno una relazione master/dettaglio.

### <a name="to-test-your-document"></a>Per testare il documento

1.  Premere **F5** per eseguire il progetto.

2.  Verificare che il riquadro azioni sia visibile.

3.  Selezionare una società nella casella di riepilogo. Verificare che sia elencato il nome della società nel <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo e i dettagli del prodotto sono elencati nel <xref:Microsoft.Office.Tools.Excel.ListObject> controllo.

4.  Consente di selezionare varie società per verificare il nome della società e dettagli sul prodotto modificare come appropriato.

## <a name="next-steps"></a>Passaggi successivi
 Ecco alcune possibili attività successive:

-   Associazione dati ai controlli di Word. Per altre informazioni, vedere [Procedura dettagliata: Associare dati a controlli in un riquadro azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

-   La distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Vedere anche
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Procedura: Gestire il layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
