---
title: Aggiornare il grafico nel foglio di comando usando i pulsanti di opzione
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
ms.openlocfilehash: e63d7d09a09fe4c051d8137428fdae90490cbae5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238816"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Procedura dettagliata: aggiornamento di un grafico in un foglio di lavoro mediante i pulsanti di opzione
  Questa procedura dettagliata illustra le nozioni di base sull'uso dei pulsanti di opzione in un foglio di lavoro di Excel Microsoft Office per consentire all'utente di passare rapidamente da una modalità all'altra. In questo caso, le opzioni cambiano lo stile di un grafico.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Per visualizzare il risultato come esempio completo, vedere l'esempio relativo ai controlli di Excel in [esempi e procedure dettagliate per lo sviluppo di Office](../vsto/office-development-samples-and-walkthroughs.md).

 Vengono illustrate le attività seguenti:

- Aggiunta di un gruppo di pulsanti di opzione a un foglio di foglio.

- Modifica dello stile del grafico quando si seleziona un'opzione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="add-a-chart-to-a-worksheet"></a>Aggiungere un grafico a un foglio di foglio
 È possibile creare un progetto di cartella di lavoro di Excel che personalizza una cartella di lavoro esistente. In questa procedura dettagliata verrà aggiunto un grafico a una cartella di lavoro di, che verrà quindi utilizzata in una nuova soluzione Excel. L'origine dati in questa procedura dettagliata è un foglio **di dati denominato data per il grafico**.

### <a name="to-add-the-data"></a>Per aggiungere i dati

1. Aprire Microsoft Excel.

2. Fare clic con il pulsante destro del mouse sulla scheda **Sheet3** , quindi scegliere **Rinomina** dal menu di scelta rapida.

3. Rinominare il foglio in **dati per il grafico**.

4. Aggiungere i dati seguenti ai **dati per il grafico** con la cella A4 che è l'angolo superiore sinistro e E8 l'angolo inferiore destro.

   |Area/trimestre|T1|T2|T3|T4|
   |-|--------|--------|--------|--------|
   |West|500|550|550|600|
   |East|600|625|675|700|
   |North|450|470|490|510|
   |South|800|750|775|790|

   Successivamente, aggiungere un grafico al primo foglio di foglio per visualizzare i dati.

### <a name="to-add-a-chart-in-excel"></a>Per aggiungere un grafico in Excel

1. Nel gruppo **grafici** della scheda **Inserisci** fare clic su **colonna**, quindi fare clic su **tutti i tipi di grafico**.

2. Nella finestra di dialogo **Inserisci grafico** fare clic su **OK**.

3. Nella scheda **progettazione** , nel gruppo **dati** , fare clic su **Seleziona dati**.

4. Nella finestra di dialogo **Seleziona origine dati** fare clic nella casella **intervallo ChartData** e deselezionare le selezioni predefinite.

5. Nel foglio **dati per il grafico** selezionare il blocco di celle che contiene i numeri, che include a4 nell'angolo superiore sinistro a E8 nell'angolo in basso a destra.

6. Nella finestra di dialogo **Seleziona origine dati** fare clic su **OK**.

7. Riposizionare il grafico in modo che l'angolo superiore destro venga allineato alla cella **e2**.

8. Salvare il file nell'unità C e denominarlo **ExcelChart.xlsx**.

9. Uscire da Excel.

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 In questo passaggio verrà creato un progetto di cartella di lavoro di Excel basato sulla cartella di lavoro **ExcelChart** .

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto di cartella di lavoro di Excel con il nome **grafico Excel**. Nella procedura guidata selezionare **copia un documento esistente**.

     Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Fare clic sul pulsante **Sfoglia** e selezionare la cartella di lavoro creata in precedenza in questa procedura dettagliata.

3. Fare clic su **OK**.

     Visual Studio apre la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il progetto **grafico di Excel** a **Esplora soluzioni**.

## <a name="set-properties-of-the-chart"></a>Impostare le proprietà del grafico
 Quando si crea un nuovo progetto cartella di lavoro di Excel in cui viene utilizzata una cartella di lavoro esistente, i controlli host vengono creati automaticamente per tutti gli intervalli denominati, gli oggetti elenco e i grafici nella cartella di lavoro. È possibile modificare il nome del <xref:Microsoft.Office.Tools.Excel.Chart> controllo utilizzando la finestra **Proprietà** .

### <a name="to-change-the-name-of-the-chart-control"></a>Per modificare il nome del controllo Chart

1. Selezionare il <xref:Microsoft.Office.Tools.Excel.Chart> controllo nella finestra di progettazione e modificare le proprietà seguenti nella finestra **Proprietà** .

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**datachart**|
    |**HasLegend**|**false**|

## <a name="add-controls"></a>Aggiungere controlli
 Questo foglio di utilizzo usa i pulsanti di opzione per fornire agli utenti un modo per modificare rapidamente lo stile del grafico. Tuttavia, i pulsanti di opzione devono essere esclusivi: quando si seleziona un pulsante, non è possibile selezionare contemporaneamente nessun altro pulsante del gruppo. Questo comportamento non si verifica per impostazione predefinita quando si aggiungono diversi pulsanti di opzione a un foglio di foglio.

 Un modo per aggiungere questo comportamento consiste nel raggruppare i pulsanti di opzione in un controllo utente, scrivere il codice dietro il controllo utente e quindi aggiungere il controllo utente al foglio di lavoro.

### <a name="to-add-a-user-control"></a>Per aggiungere un controllo utente

1. Selezionare il progetto di **grafico Excel** in **Esplora soluzioni**.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **controllo utente**, denominare il controllo **ChartOptions** e quindi fare clic su **Aggiungi**.

### <a name="to-add-radio-buttons-to-the-user-control"></a>Per aggiungere pulsanti di opzione al controllo utente

1. Se il controllo utente non è visibile nella finestra di progettazione, fare doppio clic su **ChartOptions** in **Esplora soluzioni**.

2. Dalla scheda **controlli comuni** della **casella degli strumenti**trascinare un controllo **pulsante di opzione** sul controllo utente e modificare le proprietà seguenti.

   | Proprietà | Valore |
   |----------|------------------|
   | **Nome** | **columnChart** |
   | **Text** | **Istogramma** |

3. Aggiungere un secondo pulsante di opzione al controllo utente e modificare le proprietà seguenti.

   | Proprietà | Valore |
   |----------|---------------|
   | **Nome** | **barChart** |
   | **Text** | **Grafico a barre** |

4. Aggiungere un terzo pulsante di opzione al controllo utente e modificare le proprietà seguenti.

   | Proprietà | Valore |
   |----------|----------------|
   | **Nome** | **lineChart** |
   | **Text** | **Grafico a linee** |

5. Aggiungere un quarto pulsante di opzione al controllo utente e modificare le proprietà seguenti.

   |Proprietà|Valore|
   |--------------|-----------|
   |**Nome**|**areaBlockChart**|
   |**Text**|**Grafico ad area**|

   Quindi, scrivere il codice per aggiornare il grafico quando si fa clic su un pulsante di opzione.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Modificare lo stile del grafico quando si seleziona un pulsante di opzione
 A questo punto è possibile aggiungere il codice per modificare lo stile del grafico. A tale scopo, creare un evento pubblico sul controllo utente, aggiungere una proprietà per impostare il tipo di selezione e creare un gestore eventi per l' `CheckedChanged` evento di ognuno dei pulsanti di opzione.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Per creare un evento e una proprietà in un controllo utente

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul controllo utente, quindi scegliere **Visualizza codice**.

2. Aggiungere codice alla `ChartOptions` classe per creare un `SelectionChanged` evento e la `Selection` Proprietà.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Per gestire l'evento CheckedChanged dei pulsanti di opzione

1. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `areaBlockChart` e quindi generare l'evento.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]

2. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `barChart`.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]

3. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `columnChart`.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]

4. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `lineChart`.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]

5. In C# è necessario aggiungere gestori eventi per i pulsanti di opzione. È possibile aggiungere questo codice al costruttore `ChartOptions` dopo la chiamata a `InitializeComponent`. Per informazioni su come creare i gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]

## <a name="add-the-user-control-to-the-worksheet"></a>Aggiungere il controllo utente al foglio di controllo
 Quando si compila la soluzione, il nuovo controllo utente viene aggiunto automaticamente alla **casella degli strumenti**. È quindi possibile trascinare il controllo dalla **casella degli strumenti** al foglio di lavoro.

### <a name="to-add-the-user-control-your-worksheet"></a>Per aggiungere il controllo utente del foglio di lavoro

1. Nel menu **Compila** scegliere **Compila soluzione**.

     Il controllo utente **ChartOptions** viene aggiunto alla **casella degli strumenti**.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **Sheet1. vb** o **Sheet1.cs**, quindi scegliere **Visualizza finestra di progettazione**.

3. Trascinare il controllo **ChartOptions** dalla **casella degli strumenti** al foglio di comando.

     `my_Excel_Chart_ChartOptions1`Al progetto viene aggiunto un nuovo controllo denominato.

4. Modificare il nome del controllo in **ChartOptions1**.

## <a name="change-the-chart-type"></a>Modificare il tipo di grafico
 Per modificare il tipo di grafico, creare un gestore eventi che imposta lo stile in base all'opzione selezionata nel controllo utente.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Per modificare il tipo di grafico visualizzato nel foglio di testo

1. Aggiungere il seguente gestore eventi alla classe `Sheet1`.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]

2. In C# è necessario aggiungere un gestore eventi per il controllo utente all'evento, <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> come illustrato di seguito. Per informazioni su come creare i gestori eventi, vedere [procedura: creare gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]

## <a name="test-the-application"></a>Test dell'applicazione
 È ora possibile testare la cartella di lavoro per verificare che lo stile del grafico sia corretto quando si seleziona un pulsante di opzione.

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per eseguire il progetto.

2. Selezionare vari pulsanti di opzione.

3. Verificare che lo stile del grafico sia modificato in base alla selezione.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base relative all'uso di pulsanti di opzione e stili dei grafici nei fogli di foglio Ecco alcune possibili attività successive:

- Distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).

- Usare un pulsante per popolare una casella di testo. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzare il testo in una casella di testo di un foglio di un foglio di testo utilizzando un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

- Modificare la formattazione di un foglio di controllo utilizzando le caselle di controllo. Per altre informazioni, vedere [procedura dettagliata: modificare la formattazione del foglio di controllo tramite i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Vedere anche
- [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)
