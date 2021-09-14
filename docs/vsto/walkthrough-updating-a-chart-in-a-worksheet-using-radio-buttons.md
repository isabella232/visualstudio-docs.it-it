---
title: Aggiornare un grafico nel foglio di lavoro usando i pulsanti di opzione
description: Informazioni di base sull'uso dei pulsanti di opzione in Microsoft Excel foglio di lavoro per offrire all'utente un modo per passare rapidamente da un'opzione all'altro.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4edf0813fcbcd9b7013b85bcf251da9a47beb78a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710027"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Procedura dettagliata: aggiornamento di un grafico in un foglio di lavoro mediante i pulsanti di opzione
  Questa procedura dettagliata illustra le nozioni di base sull'uso dei pulsanti di opzione in un Microsoft Office Excel di lavoro per offrire all'utente un modo per passare rapidamente da un'opzione all'altro. In questo caso, le opzioni modificano lo stile di un grafico.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Per visualizzare il risultato come esempio completo, vedere l'esempio Excel controls in Office di sviluppo [e procedure dettagliate.](../vsto/office-development-samples-and-walkthroughs.md)

 Vengono illustrate le attività seguenti:

- Aggiunta di un gruppo di pulsanti di opzione a un foglio di lavoro.

- Modifica dello stile del grafico quando si seleziona un'opzione.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="add-a-chart-to-a-worksheet"></a>Aggiungere un grafico a un foglio di lavoro
 È possibile creare un progetto Excel cartella di lavoro esistente che personalizza una cartella di lavoro esistente. In questa procedura dettagliata si aggiungerà un grafico a una cartella di lavoro e quindi si userà questa cartella di lavoro in una nuova Excel soluzione. L'origine dati in questa procedura dettagliata è un foglio di lavoro **denominato Data for Chart**.

### <a name="to-add-the-data"></a>Per aggiungere i dati

1. Aprire Microsoft Excel.

2. Fare clic con il pulsante destro del mouse sulla scheda **Foglio3** , quindi **scegliere Rinomina** dal menu di scelta rapida.

3. Rinominare il foglio in **Dati per Grafico**.

4. Aggiungere i dati seguenti a **Data for Chart con** la cella A4 nell'angolo superiore sinistro e E8 nell'angolo inferiore destro.

   |Area/Trimestre|T1|T2|T3|T4|
   |-|--------|--------|--------|--------|
   |West|500|550|550|600|
   |East|600|625|675|700|
   |North|450|470|490|510|
   |South|800|750|775|790|

   Aggiungere quindi un grafico al primo foglio di lavoro per visualizzare i dati.

### <a name="to-add-a-chart-in-excel"></a>Per aggiungere un grafico in Excel

1. Nel gruppo **Grafici** della  scheda Inserisci fare clic su **Colonna** e quindi su **Tutti i tipi di grafico**.

2. Nella finestra **di dialogo Inserisci** grafico fare clic su **OK.**

3. Nel gruppo **Dati** della scheda Progettazione **fare** clic su **Seleziona dati**.

4. Nella finestra **di dialogo Seleziona origine** dati fare clic nella casella **GraficoA intervalli di dati** e deselezionare qualsiasi selezione predefinita.

5. Nel foglio **Dati per** grafico selezionare il blocco di celle che contiene i numeri, che include A4 nell'angolo superiore sinistro e E8 nell'angolo inferiore destro.

6. Nella finestra **di dialogo Seleziona origine** dati fare clic su **OK.**

7. Riposizionare il grafico in modo che l'angolo superiore destro sia allineato alla **cella E2**.

8. Salvare il file nell'unità C e denotarlo **ExcelChart.xlsx**.

9. Uscire da Excel.

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 In questo passaggio si creerà un progetto Excel cartella di lavoro basata sulla cartella **di lavoro ExcelChart.**

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un progetto Excel cartella di lavoro con il nome **My Excel Chart**. Nella procedura guidata selezionare **Copia un documento esistente.**

     Per altre informazioni, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Fare clic **sul pulsante** Sfoglia e passare alla cartella di lavoro creata in precedenza in questa procedura dettagliata.

3. Fare clic su **OK**.

     Visual Studio apre la nuova cartella Excel cartella di lavoro nella finestra di progettazione e aggiunge il progetto My **Excel Chart** **a Esplora soluzioni**.

## <a name="set-properties-of-the-chart"></a>Impostare le proprietà del grafico
 Quando si crea un nuovo progetto Excel Workbook che usa una cartella di lavoro esistente, i controlli host vengono creati automaticamente per tutti gli intervalli denominati, gli oggetti elenco e i grafici nella cartella di lavoro. È possibile modificare il nome del <xref:Microsoft.Office.Tools.Excel.Chart> controllo usando la **finestra** Proprietà.

### <a name="to-change-the-name-of-the-chart-control"></a>Per modificare il nome del controllo Chart

1. Selezionare il <xref:Microsoft.Office.Tools.Excel.Chart> controllo nella finestra di progettazione e modificare le proprietà seguenti nella **finestra** Proprietà.

    |Proprietà|Valore|
    |--------------|-----------|
    |**Nome**|**dataChart**|
    |**HasLegend**|**false**|

## <a name="add-controls"></a>Aggiungere controlli
 Questo foglio di lavoro usa i pulsanti di opzione per consentire agli utenti di modificare rapidamente lo stile del grafico. Tuttavia, i pulsanti di opzione devono essere esclusivi: quando si seleziona un pulsante, nessun altro pulsante nel gruppo può essere selezionato contemporaneamente. Questo comportamento non si verifica per impostazione predefinita quando si aggiungono diversi pulsanti di opzione a un foglio di lavoro.

 Un modo per aggiungere questo comportamento è raggruppare i pulsanti di opzione in un controllo utente, scrivere il codice dietro il controllo utente e quindi aggiungere il controllo utente al foglio di lavoro.

### <a name="to-add-a-user-control"></a>Per aggiungere un controllo utente

1. Selezionare il **progetto My Excel Chart** in **Esplora soluzioni**.

2. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo elemento** fare clic su Controllo **utente**, assegnare al controllo il nome **ChartOptions e** fare clic su **Aggiungi**.

### <a name="to-add-radio-buttons-to-the-user-control"></a>Per aggiungere pulsanti di opzione al controllo utente

1. Se il controllo utente non è visibile nella finestra di progettazione, fare doppio clic **su ChartOptions** in **Esplora soluzioni**.

2. Dalla scheda **Controlli comuni** della casella **degli strumenti** trascinare un controllo **Pulsante di** opzione nel controllo utente e modificare le proprietà seguenti.

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

   Scrivere quindi il codice per aggiornare il grafico quando si fa clic su un pulsante di opzione.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Modificare lo stile del grafico quando viene selezionato un pulsante di opzione
 È ora possibile aggiungere il codice per modificare lo stile del grafico. A tale scopo, creare un evento pubblico nel controllo utente, aggiungere una proprietà per impostare il tipo di selezione e creare un gestore eventi per l'evento di ognuno `CheckedChanged` dei pulsanti di opzione.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Per creare un evento e una proprietà in un controllo utente

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul controllo utente e quindi scegliere **Visualizza codice**.

2. Aggiungere codice alla `ChartOptions` classe per creare un evento e la proprietà `SelectionChanged` `Selection` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet13":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet13":::

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Per gestire l'evento CheckedChanged dei pulsanti di opzione

1. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `areaBlockChart` e quindi generare l'evento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet14":::

2. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `barChart`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet15":::

3. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `columnChart`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet16":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet16":::

4. Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `lineChart`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet17":::

5. In C# è necessario aggiungere gestori eventi per i pulsanti di opzione. È possibile aggiungere questo codice al costruttore `ChartOptions` dopo la chiamata a `InitializeComponent`. Per informazioni su come creare gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office progetti .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs" id="Snippet18":::

## <a name="add-the-user-control-to-the-worksheet"></a>Aggiungere il controllo utente al foglio di lavoro
 Quando si compila la soluzione, il nuovo controllo utente viene aggiunto automaticamente alla casella **degli strumenti**. È quindi possibile trascinare il controllo dalla Casella **degli strumenti** al foglio di lavoro.

### <a name="to-add-the-user-control-your-worksheet"></a>Per aggiungere il controllo utente al foglio di lavoro

1. Nel menu **Compila** scegliere **Compila soluzione**.

     Il **controllo utente ChartOptions** viene aggiunto alla casella **degli strumenti**.

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1.vb** o **Sheet1.cs** e **quindi scegliere Progettazione visualizzazioni**.

3. Trascinare **il controllo ChartOptions** dalla **Casella degli strumenti** al foglio di lavoro.

     Al progetto `my_Excel_Chart_ChartOptions1` viene aggiunto un nuovo controllo denominato .

4. Modificare il nome del controllo in **ChartOptions1**.

## <a name="change-the-chart-type"></a>Modificare il tipo di grafico
 Per modificare il tipo di grafico, creare un gestore eventi che imposta lo stile in base all'opzione selezionata nel controllo utente.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Per modificare il tipo di grafico visualizzato nel foglio di lavoro

1. Aggiungi alla classe `Sheet1` il gestore eventi indicato di seguito.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet19":::

2. In C# è necessario aggiungere un gestore eventi per il controllo utente <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> all'evento , come illustrato di seguito. Per informazioni su come creare gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office progetti .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet20":::

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare la cartella di lavoro per verificare che lo stile del grafico sia corretto quando si seleziona un pulsante di opzione.

### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro

1. Premere **F5** per eseguire il progetto.

2. Selezionare vari pulsanti di opzione.

3. Verificare che lo stile del grafico sia modificato in base alla selezione.

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base sull'uso di pulsanti di opzione e stili di grafico nei fogli di lavoro. Ecco alcune possibili attività successive:

- Distribuzione del progetto. Per altre informazioni, vedere [Deploy an Office solution](../vsto/deploying-an-office-solution.md).

- Usare un pulsante per popolare una casella di testo. Per altre informazioni, vedere [Procedura dettagliata: Visualizzare il testo in una casella di testo in un foglio di lavoro usando un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

- Modificare la formattazione in un foglio di lavoro usando le caselle di controllo. Per altre informazioni, vedere Procedura [dettagliata: Modificare la formattazione del foglio di lavoro usando i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Vedi anche
- [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)
