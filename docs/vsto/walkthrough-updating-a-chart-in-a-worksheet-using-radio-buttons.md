---
title: 'Procedura dettagliata: Aggiornamento di un grafico in un foglio di lavoro mediante pulsanti di opzione'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ae451b42642cd3c124b3fe9d5df627c2306a2020
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873873"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Procedura dettagliata: Aggiornamento di un grafico in un foglio di lavoro mediante pulsanti di opzione
  Questa procedura dettagliata illustra le nozioni di base dell'uso di pulsanti di opzione in un foglio di lavoro di Microsoft Office Excel per consentire all'utente un modo per passare rapidamente tra le opzioni. In questo caso, le opzioni di modificare lo stile di un grafico.  

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  

 Per visualizzare il risultato come un esempio completo, vedere l'esempio di controlli Excel all'indirizzo [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  

 Questa procedura dettagliata illustra le attività seguenti:  

-   Aggiunta di un gruppo di pulsanti di opzione in un foglio di lavoro.  

-   Modifica dello stile del grafico quando si seleziona un'opzione.  

> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  

## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  

## <a name="add-a-chart-to-a-worksheet"></a>Aggiungere un grafico a un foglio di lavoro  
 È possibile creare un progetto cartella di lavoro di Excel che consente di personalizzare una cartella di lavoro esistente. In questa procedura dettagliata verrà aggiungere un grafico a una cartella di lavoro e quindi usare questa cartella di lavoro in una nuova soluzione di Excel. L'origine dati in questa procedura dettagliata è un foglio di lavoro denominato **dei dati per il grafico**.  

### <a name="to-add-the-data"></a>Per aggiungere i dati  

1. Aprire Microsoft Excel.  

2. Fare doppio clic il **Sheet3** scheda e quindi fare clic su **rinominare** menu di scelta rapida.  

3. Rinomina il foglio **dei dati per il grafico**.  

4. Aggiungere i dati seguenti per **dei dati per il grafico** cella A4 che rappresenta l'angolo superiore sinistro angolo ed E8 angolo inferiore destro.  

   ||Q1|(DOMANDA 2)|Q3|Q4|  
   |-|--------|--------|--------|--------|  
   |Occidentale|500|550|550|600|  
   |Orientale|600|625|675|700|  
   |Centro-settentrionali|450|470|490|510|  
   |Meridionale|800|750|775|790|  

   Successivamente, aggiungere un grafico al primo foglio di lavoro per visualizzare i dati.  

### <a name="to-add-a-chart-in-excel"></a>Per aggiungere un grafico in Excel  

1.  Nel **inserire** nella scheda il **grafici** fare clic su **colonna**e quindi fare clic su **tutti i tipi di grafico**.  

2.  Nel **Inserisci grafico** finestra di dialogo, fare clic su **OK**.  

3.  Nel **progettazione** nella scheda il **dati** fare clic su **selezione dati**.  

4.  Nel **selezionare un'origine dati** fare clic nella finestra di dialogo il **intervallo Chartdata** casella e deselezionare eventuali selezioni predefinite.  

5.  Nel **dei dati per il grafico** foglio, selezionare l'intervallo di celle contenente i numeri, che include A4 nell'angolo superiore sinistro per E8 nell'angolo inferiore destro.  

6.  Nel **selezionare un'origine dati** finestra di dialogo, fare clic su **OK**.  

7.  Riposizionare il grafico in modo che l'angolo superiore destro viene allineato cella **E2**.  

8.  Salvare il file sull'unità C e denominarlo **ExcelChart.xlsx**.  

9. Uscire da Excel.  

## <a name="create-a-new-project"></a>Creare un nuovo progetto  
 In questo passaggio si creerà un progetto cartella di lavoro di Excel sulla base di **ExcelChart** della cartella di lavoro.  

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  

1.  Creare un progetto cartella di lavoro di Excel con il nome **My Chart Excel**. Nella procedura guidata, selezionare **copia un documento esistente**.  

     Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

2.  Scegliere il **esplorare** pulsante e passare alla cartella di lavoro è stato creato in precedenza in questa procedura dettagliata.  

3.  Fare clic su **OK**.  

     Visual Studio verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il **My Chart Excel** progetto al **Esplora soluzioni**.  

## <a name="set-properties-of-the-chart"></a>Impostare le proprietà del grafico  
 Quando si crea un nuovo progetto cartella di lavoro di Excel che usa una cartella di lavoro esistente, i controlli host vengono creati automaticamente per tutti gli intervalli denominati, elenco degli oggetti e i grafici nella cartella di lavoro. È possibile modificare il nome del <xref:Microsoft.Office.Tools.Excel.Chart> controllo usando il **proprietà** finestra.  

### <a name="to-change-the-name-of-the-chart-control"></a>Per modificare il nome del controllo del grafico  

1.  Selezionare il <xref:Microsoft.Office.Tools.Excel.Chart> nella finestra di progettazione e modificare le proprietà seguenti nella **proprietà** finestra.  

    |Proprietà|Value|  
    |--------------|-----------|  
    |**Name**|**dataChart**|  
    |**HasLegend**|**false**|  

## <a name="add-controls"></a>Aggiungere controlli  
 Questo foglio di lavoro Usa i pulsanti di opzione per concedere agli utenti un modo per modificare rapidamente lo stile del grafico. Tuttavia, devono essere esclusivi pulsanti di opzione, quando si seleziona un pulsante, non selezionabile alcun pulsante del gruppo contemporaneamente. Questo comportamento non avviene per impostazione predefinita quando si aggiungono più pulsanti di opzione a un foglio di lavoro.  

 Un modo per aggiungere questo comportamento consiste nel raggruppare i pulsanti di opzione in un controllo utente, scrivere il codice dietro il controllo utente e quindi aggiungere il controllo utente al foglio di lavoro.  

### <a name="to-add-a-user-control"></a>Per aggiungere un controllo utente  

1.  Selezionare il **My Chart Excel** del progetto nelle **Esplora soluzioni**.  

2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  

3.  Nel **Aggiungi nuovo elemento** finestra di dialogo, fare clic su **controllo utente**, denominare il controllo **ChartOptions** e fare clic su **Aggiungi**.  

### <a name="to-add-radio-buttons-to-the-user-control"></a>Per aggiungere pulsanti di opzione nel controllo utente  

1. Se il controllo utente non è visibile nella finestra di progettazione, fare doppio clic su **ChartOptions** nelle **Esplora soluzioni**.  

2. Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare un **pulsante di opzione** al controllo utente e modificare le proprietà seguenti.  


   | Proprietà | Value |
   |----------|------------------|
   | **Name** | **columnChart** |
   | **per** | **Istogramma a colonne** |


3. Aggiungere un secondo pulsante di opzione nel controllo utente e modificare le proprietà seguenti.  


   | Proprietà | Value |
   |----------|---------------|
   | **Name** | **barChart** |
   | **per** | **Grafico a barre** |


4. Aggiungere un terzo pulsante di opzione nel controllo utente e modificare le proprietà seguenti.  


   | Proprietà | Value |
   |----------|----------------|
   | **Name** | **lineChart** |
   | **per** | **Grafico a linee** |


5. Aggiungere un quarto pulsante di opzione nel controllo utente e modificare le proprietà seguenti.  

   |Proprietà|Value|  
   |--------------|-----------|  
   |**Name**|**areaBlockChart**|  
   |**per**|**Grafico ad area**|  

   Successivamente, scrivere il codice per aggiornare il grafico quando si seleziona un pulsante di opzione.  

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Modificare lo stile del grafico quando viene selezionato un pulsante di opzione  
 A questo punto è possibile aggiungere il codice per modificare lo stile del grafico. A tale scopo, creare un evento pubblico nel controllo utente, aggiungere una proprietà per impostare il tipo di selezione e creare un gestore eventi per il `CheckedChanged` evento della ognuno dei pulsanti di opzione.  

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Per creare un evento e una proprietà in un controllo utente  

1.  Nelle **Esplora soluzioni**, fare clic sul controllo utente e quindi fare clic su **Visualizza codice**.  

2.  Aggiungere il codice per il `ChartOptions` classe per creare un `SelectionChanged` evento e il `Selection` proprietà.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Per gestire l'evento CheckedChanged dei pulsanti di opzione  

1.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `areaBlockChart` e quindi generare l'evento.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  

2.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `barChart`.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  

3.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `columnChart`.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  

4.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `lineChart`.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  

5.  In C# è necessario aggiungere gestori eventi per i pulsanti di opzione. È possibile aggiungere questo codice al costruttore `ChartOptions` dopo la chiamata a `InitializeComponent`. Per informazioni su come creare gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  

## <a name="add-the-user-control-to-the-worksheet"></a>Aggiungere il controllo utente al foglio di lavoro  
 Quando si compila la soluzione, il nuovo controllo utente viene automaticamente aggiunto per il **casella degli strumenti**. È quindi possibile trascinare il controllo dal **casella degli strumenti** al foglio di lavoro.  

### <a name="to-add-the-user-control-your-worksheet"></a>Per aggiungere il controllo utente nel foglio di lavoro  

1.  Scegliere **Compila soluzione** dal menu **Compila**.  

     Il **ChartOptions** controllo utente viene aggiunto per il **della casella degli strumenti**.  

2.  Nella **Esplora soluzioni**, fare doppio clic su **Sheet1.vb** oppure **Sheet1.cs**, quindi fare clic su **Progettazione viste**.  

3.  Trascinare il **ChartOptions** controllare dalle **della casella degli strumenti** al foglio di lavoro.  

     Un nuovo controllo denominato `my_Excel_Chart_ChartOptions1` viene aggiunto al progetto.  

4.  Modificare il nome del controllo **ChartOptions1**.  

## <a name="change-the-chart-type"></a>Modificare il tipo di grafico  
 Per modificare il tipo di grafico, creare un gestore eventi che imposta lo stile in base all'opzione selezionata nel controllo utente.  

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Per modificare il tipo di grafico che viene visualizzato nel foglio di lavoro  

1.  Aggiungere il seguente gestore eventi alla classe `Sheet1`.  

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  

2.  In c#, è necessario aggiungere un gestore eventi per il controllo utente per il <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, come illustrato di seguito. Per informazioni su come creare gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  

## <a name="test-the-application"></a>Testare l'applicazione  
 È ora possibile testare la cartella di lavoro per verificare che il grafico viene applicato lo stile corretto quando si seleziona un pulsante di opzione.  

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro  

1.  Premere **F5** per eseguire il progetto.  

2.  Selezionare vari pulsanti di opzione.  

3.  Verificare che lo stile del grafico sia modificato in base alla selezione.  

## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base dell'uso di pulsanti di opzione e gli stili dei grafici in fogli di lavoro. Ecco alcune possibili attività successive:  

-   La distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).  

-   Usare un pulsante per popolare una casella di testo. Per altre informazioni, vedere [Procedura dettagliata: Visualizzare il testo in una casella di testo in un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  

-   Modificare la formattazione in un foglio di lavoro usando le caselle di controllo. Per altre informazioni, vedere [Procedura dettagliata: Modificare la formattazione del foglio di lavoro mediante controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  

## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)  
