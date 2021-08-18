---
title: 'Procedura dettagliata: Associare dati a controlli in un riquadro Excel azioni'
description: Associare dati ai controlli in un riquadro azioni in Microsoft Excel. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.
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
ms.openlocfilehash: 7a6a6a914c1777142a1febefa12c0c78bbcb290d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099347"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Procedura dettagliata: Associare dati a controlli in un riquadro Excel azioni
  Questa procedura dettagliata illustra data binding controlli in un riquadro azioni in Microsoft Office Excel. I controlli mostrano una relazione master/detail tra le tabelle in un database SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Vengono illustrate le attività seguenti:

- Aggiunta di controlli a un foglio di lavoro.

- Creazione di un controllo riquadro azioni.

- Aggiunta di controlli form Windows dati a un controllo riquadro azioni.

- Visualizzazione del riquadro azioni all'apertura dell'applicazione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Accesso a un server con il database di SQL Server Northwind.

- Autorizzazioni per la lettura e la scrittura nel database SQL Server.

## <a name="create-the-project"></a>Creare il progetto
 Il primo passaggio consiste nella creazione di un progetto Cartella di lavoro di Excel.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto Excel cartella di lavoro con il nome **My Excel Actions Pane**. Nella procedura guidata selezionare **Crea un nuovo documento.** Per altre informazioni, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella Excel cartella di lavoro nella finestra di progettazione e aggiunge il progetto Riquadro **azioni** Excel a **Esplora soluzioni**.

## <a name="add-a-new-data-source-to-the-project"></a>Aggiungere una nuova origine dati al progetto

### <a name="to-add-a-new-data-source-to-the-project"></a>Per aggiungere una nuova origine dati al progetto

1. Se la **finestra Origini** dati non è visibile, visualizzarla nella barra dei menu scegliendo Visualizza altre Windows  >    >  **dati**.

2. Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Selezionare **Database** e quindi fare clic su **Avanti.**

4. Selezionare una connessione dati al database di esempio Northwind SQL Server oppure aggiungere una nuova connessione usando il **pulsante Nuova** connessione.

5. Fare clic su **Avanti**.

6. Deselezionare l'opzione per salvare la connessione, se selezionata, quindi fare clic su **Avanti.**

7. Espandere il **nodo** Tabelle nella **finestra Oggetti di** database .

8. Selezionare la casella di controllo accanto **alla tabella Suppliers.**

9. Espandere la **tabella Products** e **selezionare ProductName**, **SupplierID**, **QuantityPerUnit** e **UnitPrice**.

10. Fare clic su **Fine**.

    La procedura guidata aggiunge **la tabella Suppliers** **e la tabella Products** alla finestra **Origini** dati . Aggiunge anche un set di dati tipizzato al progetto visibile in **Esplora soluzioni**.

## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro
 Aggiungere quindi un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> e un controllo al primo foglio di <xref:Microsoft.Office.Tools.Excel.ListObject> lavoro.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Per aggiungere un controllo NamedRange e un controllo ListObject

1. Verificare che la **cartella di lavoro Excel Actions Pane.xlsx** sia aperta nella finestra di progettazione Visual Studio, con `Sheet1` visualizzata.

2. Nella **finestra Origini** dati espandere la **tabella Suppliers** .

3. Fare clic sulla freccia a discesa nel **nodo Nome società** e quindi fare clic su **NamedRange**.

4. Trascinare **Nome** società dalla **finestra Origini** dati alla cella **A2** in `Sheet1` .

     Viene <xref:Microsoft.Office.Tools.Excel.NamedRange> creato un controllo denominato e il testo viene visualizzato nella cella `CompanyNameNamedRange` \<CompanyName> **A2.** Allo stesso tempo, un oggetto denominato , un adattatore di tabella e <xref:System.Windows.Forms.BindingSource> un oggetto vengono aggiunti al `suppliersBindingSource` <xref:System.Data.DataSet> progetto. Il controllo è associato <xref:System.Windows.Forms.BindingSource> all'oggetto , che a sua volta è associato all'istanza <xref:System.Data.DataSet> di .

5. Nella finestra **Origini dati** scorrere verso il basso oltre le colonne sotto la **tabella Suppliers.** Nella parte inferiore dell'elenco è disponibile **la tabella Products.** è qui perché è un elemento figlio della **tabella Suppliers.** Selezionare questa **tabella Products,** non quella che si trova allo stesso livello della tabella **Suppliers,** quindi fare clic sulla freccia a discesa visualizzata.

6. Fare **clic su ListObject** nell'elenco a discesa e quindi trascinare la **tabella Products** nella cella **A6** in `Sheet1` .

     Nella <xref:Microsoft.Office.Tools.Excel.ListObject> cella `ProductNameListObject` **A6** viene creato un controllo denominato . Allo stesso tempo, un <xref:System.Windows.Forms.BindingSource> adattatore `productsBindingSource` denominato e un adattatore tabella vengono aggiunti al progetto. Il controllo è associato <xref:System.Windows.Forms.BindingSource> all'oggetto , che a sua volta è associato all'istanza <xref:System.Data.DataSet> di .

7. Solo per C#, selezionare **suppliersBindingSource** nella barra dei componenti e modificare la proprietà **Modificatori** in **Interno** nella **finestra** Proprietà.

## <a name="add-controls-to-the-actions-pane"></a>Aggiungere controlli al riquadro azioni
 A questo punto, è necessario un controllo riquadro azioni con una casella combinata.

### <a name="to-add-an-actions-pane-control"></a>Per aggiungere un controllo riquadro azioni

1. Selezionare il **progetto My Excel Actions Pane** in **Esplora soluzioni**.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo elemento** selezionare Controllo **riquadro** azioni, assegnare al controllo il nome **ActionsControl** e fare clic su **Aggiungi.**

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Per aggiungere controlli Form associati Windows dati a un controllo riquadro azioni

1. Dalle schede **Controlli comuni** della Casella **degli strumenti** trascinare un controllo nel controllo <xref:System.Windows.Forms.ComboBox> riquadro azioni.

2. Modificare la **proprietà Size** in **171, 21**.

3. Ridimensionare il controllo utente per adattarlo alla casella combinata.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Associare il controllo nel riquadro azioni ai dati
 In questa sezione si imposta l'origine dati di sulla stessa origine dati <xref:System.Windows.Forms.ComboBox> del controllo nel foglio di <xref:Microsoft.Office.Tools.Excel.NamedRange> lavoro.

### <a name="to-set-data-binding-properties-of-the-control"></a>Per impostare data binding proprietà del controllo

1. Fare clic con il pulsante destro del mouse sul controllo riquadro azioni e **quindi scegliere Visualizza codice.**

2. Aggiungere il codice seguente <xref:System.Windows.Forms.UserControl.Load> all'evento del controllo del riquadro azioni.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet1":::

3. In C# è necessario creare un gestore eventi per `ActionsControl` . È possibile inserire questo codice nel `ActionsControl` costruttore . Per altre informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori eventi in Office progetti](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet2":::

## <a name="show-the-actions-pane"></a>Visualizzare il riquadro azioni
 Il riquadro azioni non è visibile fino a quando non si aggiunge il controllo in fase di esecuzione.

#### <a name="to-show-the-actions-pane"></a>Per visualizzare il riquadro azioni

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su *ThisWorkbook.vb* o *ThisWorkbook.cs* e quindi **scegliere Visualizza codice.**

2. Creare una nuova istanza del controllo utente nella `ThisWorkbook` classe .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet3":::

3. Nel gestore <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> eventi di aggiungere il controllo al riquadro `ThisWorkbook` azioni.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet4":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare il documento per verificare che il riquadro azioni si apra all'apertura del documento e che i controlli siano associati a una relazione master/dettagli.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Verificare che il riquadro azioni sia visibile.

3. Selezionare una società nella casella di riepilogo. Verificare che il nome della società sia elencato nel <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo e che i dettagli del prodotto siano elencati nel controllo <xref:Microsoft.Office.Tools.Excel.ListObject> .

4. Selezionare varie società per verificare che il nome della società e i dettagli del prodotto cambino in base alle esigenze.

## <a name="next-steps"></a>Passaggi successivi
 Ecco alcune possibili attività successive:

- Associazione di dati ai controlli in Word. Per altre informazioni, vedere [Procedura dettagliata: Associare dati a controlli in un riquadro azioni di Word.](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)

- Distribuzione del progetto. Per altre informazioni, vedere [Distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Vedi anche
- [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)
- [Procedura: Gestire il layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Associare dati a controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
