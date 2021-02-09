---
title: 'Procedura dettagliata: associare dati a controlli in un riquadro azioni di Excel'
description: Associare dati a controlli in un riquadro azioni in Microsoft Excel. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.
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
ms.workload:
- office
ms.openlocfilehash: 75df7a3a9ddfa6009b0002bfe83b57f2d91e6e0d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906564"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Procedura dettagliata: associare dati a controlli in un riquadro azioni di Excel
  Questa procedura dettagliata illustra data binding ai controlli in un riquadro azioni in Microsoft Office Excel. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di controlli a un foglio di foglio.

- Creazione di un controllo del riquadro azioni.

- Aggiunta di controlli Windows Form associati a dati a un controllo del riquadro azioni.

- Visualizzazione del riquadro azioni all'apertura dell'applicazione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un server con il database di esempio Northwind SQL Server.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server.

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nella creazione di un progetto Cartella di lavoro di Excel.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di cartella di lavoro di Excel con il nome **riquadro azioni di Excel**. Nella procedura guidata selezionare **Crea un nuovo documento**. Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il progetto **riquadro azioni di Excel** per **Esplora soluzioni**.

## <a name="add-a-new-data-source-to-the-project"></a>Aggiungere una nuova origine dati al progetto

### <a name="to-add-a-new-data-source-to-the-project"></a>Per aggiungere una nuova origine dati al progetto

1. Se la finestra **origini dati** non è visibile, visualizzarla dalla barra dei menu scegliendo **Visualizza**  >  **altre**  >  **origini dati** di Windows.

2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **database** e quindi fare clic su **Avanti**.

4. Selezionare una connessione dati all'esempio Northwind SQL Server database oppure aggiungere una nuova connessione usando il pulsante **nuova connessione** .

5. Fare clic su **Avanti**.

6. Deselezionare l'opzione per salvare la connessione se è selezionata, quindi fare clic su **Avanti**.

7. Espandere il nodo **tabelle** nella finestra **oggetti di database** .

8. Selezionare la casella di controllo accanto alla tabella **Suppliers** .

9. Espandere la **tabella Products** e **selezionare ProductName**, **SupplierID**, **QuantityPerUnit** e **PrezzoUnitario**.

10. Fare clic su **Fine**.

    La procedura guidata consente di aggiungere la tabella **Suppliers** e **Products** alla finestra **origini dati** . Aggiunge anche un set di dati tipizzato al progetto che è visibile in **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di controllo
 Successivamente, aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo e un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo al primo foglio di foglio.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Per aggiungere un controllo NamedRange e un controllo ListObject

1. Verificare che la cartella di lavoro **My Excel actions Pane.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzato.

2. Nella finestra **origini dati** espandere la tabella **Suppliers** .

3. Fare clic sulla freccia a discesa nel nodo **nome società** , quindi fare clic su **NamedRange**.

4. Trascinare **nome società** dalla finestra **origini dati** alla cella **a2** in `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Viene creato un controllo denominato `CompanyNameNamedRange` e il testo \<CompanyName> viene visualizzato nella cella **a2**. Allo stesso tempo, un oggetto <xref:System.Windows.Forms.BindingSource> denominato `suppliersBindingSource` , un adattatore di tabella e un oggetto <xref:System.Data.DataSet> vengono aggiunti al progetto. Il controllo è associato a <xref:System.Windows.Forms.BindingSource> , che a sua volta viene associato all' <xref:System.Data.DataSet> istanza di.

5. Nella finestra **origini dati** scorrere verso il basso le colonne che si trovano nella tabella **Suppliers** . Nella parte inferiore dell'elenco è presente la tabella **Products** . si tratta di un elemento figlio della tabella **Suppliers** . Selezionare la tabella **Products** , non quella che si trova allo stesso livello della tabella **Suppliers** , quindi fare clic sulla freccia a discesa visualizzata.

6. Fare clic su **ListObject** nell'elenco a discesa, quindi trascinare la tabella **Products** nella cella **a6** in `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.ListObject>Viene creato un controllo denominato `ProductNameListObject` nella cella **a6**. Allo stesso tempo, <xref:System.Windows.Forms.BindingSource> `productsBindingSource` al progetto vengono aggiunti un adattatore denominato e una tabella. Il controllo è associato a <xref:System.Windows.Forms.BindingSource> , che a sua volta viene associato all' <xref:System.Data.DataSet> istanza di.

7. Solo per C#, selezionare **suppliersBindingSource** nella barra dei componenti e impostare la proprietà **Modifiers** su **Internal** nella finestra **Proprietà** .

## <a name="add-controls-to-the-actions-pane"></a>Aggiungere controlli al riquadro azioni
 Successivamente, è necessario un controllo riquadro azioni con una casella combinata.

### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo del riquadro azioni

1. Selezionare il progetto **riquadro azioni di Excel** in **Esplora soluzioni**.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare il **controllo riquadro azioni**, denominarlo **ActionsControl** e fare clic su **Aggiungi**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Per aggiungere controlli Windows Form associati a dati a un controllo del riquadro azioni

1. Dalle schede **controlli comuni** della **casella degli strumenti** trascinare un <xref:System.Windows.Forms.ComboBox> controllo nel controllo del riquadro azioni.

2. Modificare la proprietà **size** in **171, 21**.

3. Ridimensionare il controllo utente per adattarlo alla casella combinata.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Associare il controllo nel riquadro azioni ai dati
 In questa sezione si imposterà l'origine dati di sulla <xref:System.Windows.Forms.ComboBox> stessa origine dati del <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nel foglio di controllo.

### <a name="to-set-data-binding-properties-of-the-control"></a>Per impostare data binding proprietà del controllo

1. Fare clic con il pulsante destro del mouse sul controllo riquadro azioni, quindi scegliere **Visualizza codice**.

2. Aggiungere il codice seguente all' <xref:System.Windows.Forms.UserControl.Load> evento del controllo del riquadro azioni.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. In C# è necessario creare un gestore eventi per il `ActionsControl` . È possibile inserire questo codice nel `ActionsControl` costruttore. Per altre informazioni sulla creazione di gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Mostra il riquadro azioni
 Il riquadro azioni non è visibile finché non si aggiunge il controllo in fase di esecuzione.

#### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su *ThisWorkbook. vb* o *ThisWorkbook.cs*, quindi scegliere **Visualizza codice**.

2. Creare una nuova istanza del controllo utente nella `ThisWorkbook` classe.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. Nel <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> gestore eventi di `ThisWorkbook` aggiungere il controllo al riquadro azioni.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Testare l'applicazione
 A questo punto è possibile testare il documento per verificare che il riquadro azioni si apra quando il documento viene aperto e che i controlli abbiano una relazione master/dettagli.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Verificare che il riquadro azioni sia visibile.

3. Selezionare una società nella casella di riepilogo. Verificare che il nome della società sia elencato nel <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo e che i dettagli del prodotto siano elencati nel <xref:Microsoft.Office.Tools.Excel.ListObject> controllo.

4. Selezionare le diverse società per verificare il nome della società e i dettagli del prodotto cambiano in base alle esigenze.

## <a name="next-steps"></a>Passaggi successivi
 Ecco alcune possibili attività successive:

- Associazione di dati a controlli in Word. Per ulteriori informazioni, vedere [procedura dettagliata: associare dati a controlli in un riquadro azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

- Distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Vedi anche
- [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)
- [Procedura: gestire il layout di controllo nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
