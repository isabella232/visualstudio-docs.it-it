---
title: 'Procedura dettagliata: Programmare sugli eventi di un controllo NamedRange'
description: Informazioni su come aggiungere un controllo NamedRange a un foglio di lavoro Microsoft Excel e programmare in base ai relativi eventi usando Office di sviluppo in Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8dcea6c0a963acfec784af11ca19e1623cdecce84ca88d1a6d8d318aa31a3fa3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121383950"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Procedura dettagliata: Programmare sugli eventi di un controllo NamedRange
  Questa procedura dettagliata illustra come aggiungere un controllo a un foglio di lavoro Microsoft Office Excel e programmare in base ai relativi eventi usando Office di sviluppo <xref:Microsoft.Office.Tools.Excel.NamedRange> in Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Durante questa procedura dettagliata, si apprenderà come:

- Aggiungere un controllo a <xref:Microsoft.Office.Tools.Excel.NamedRange> un foglio di lavoro.

- Programmare in base <xref:Microsoft.Office.Tools.Excel.NamedRange> agli eventi di controllo.

- Testare il progetto.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Creare il progetto
 In questo passaggio si creerà un progetto Excel cartella di lavoro usando Visual Studio.

### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto

1. Creare un Excel cartella di lavoro con il nome **My Named Range Events**. Assicurarsi che **l'opzione Crea un nuovo documento** sia selezionata. Per altre informazioni, vedere [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio apre la nuova cartella Excel cartella di lavoro nella finestra di progettazione e aggiunge il progetto **My Named Range Events** a **Esplora soluzioni**.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Aggiungere testo e intervalli denominati al foglio di lavoro
 Poiché i controlli host Office oggetti , è possibile aggiungerli al documento nello stesso modo in cui si aggiunge l'oggetto nativo. È ad esempio possibile aggiungere un controllo Excel a un foglio di lavoro aprendo il menu Inserisci, scegliendo Nome e scegliendo <xref:Microsoft.Office.Tools.Excel.NamedRange>  **Definisci**.  È anche possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo trascinandolo dalla Casella **degli strumenti** nel foglio di lavoro.

 In questo passaggio si aggiungeranno due controlli intervallo denominato al foglio di lavoro usando la Casella degli strumenti **e** quindi si aggiungerà testo al foglio di lavoro.

### <a name="to-add-a-range-to-your-worksheet"></a>Per aggiungere un intervallo al foglio di lavoro

1. Verificare che la *cartella di lavoro My Named Range Events.xlsx* sia aperta nella finestra Visual Studio designer, con `Sheet1` visualizzata.

2. Dalla scheda **Excel Controlli** della casella degli strumenti trascinare un controllo nella <xref:Microsoft.Office.Tools.Excel.NamedRange> cella **A1** in `Sheet1` .

     Verrà visualizzata la finestra di dialogo Aggiungi controllo **NamedRange** .

3. Verificare che **$A$1** sia visualizzato nella casella di testo modificabile e che la cella **A1** sia selezionata. In caso contrario, fare clic sulla **cella A1** per selezionarla.

4. Fare clic su **OK**.

     La **cella A1** diventa un intervallo denominato `namedRange1` . Non è presente alcuna indicazione visibile nel foglio di lavoro, ma viene visualizzata nella casella Nome (che si trova appena sopra il foglio di lavoro a sinistra) quando si seleziona `namedRange1` la cella **A1.** 

5. Aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> altro controllo alla cella **B3.**

6. Verificare che **$B$3** sia visualizzato nella casella di testo modificabile e che la cella **B3** sia selezionata. In caso contrario, fare clic sulla **cella B3** per selezionarla.

7. Fare clic su **OK**.

     La **cella B3** diventa un intervallo denominato `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Per aggiungere testo al foglio di lavoro

1. Nella cella **A1** digitare il testo seguente:

    **Questo è un esempio di controllo NamedRange.**

2. Nella cella **A3** (a sinistra di `namedRange2` ) digitare il testo seguente:

    **Eventi:**

   Nelle sezioni seguenti verrà scritto codice che inserisce testo in e modifica le proprietà del controllo in risposta agli eventi `namedRange2` `namedRange2` , e di <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Aggiungere codice per rispondere all'evento BeforeDoubleClick

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Per inserire testo in NamedRange2 in base all'evento BeforeDoubleClick

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse **su Sheet1.vb** **o Sheet1.cs** e **scegliere Visualizza codice**.

2. Aggiungere il codice in modo `namedRange1_BeforeDoubleClick` che il gestore eventi sia simile al seguente:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet24":::

3. In C# è necessario aggiungere gestori eventi per l'intervallo denominato, come illustrato <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> nell'evento seguente. Per informazioni sulla creazione di gestori eventi, vedere [Procedura: Creare gestori](../vsto/how-to-create-event-handlers-in-office-projects.md)eventi in Office progetti .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet25":::

## <a name="add-code-to-respond-to-the-change-event"></a>Aggiungere codice per rispondere all'evento Change

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Per inserire testo in namedRange2 in base all'evento Change

1. Aggiungere il codice in modo `NamedRange1_Change` che il gestore eventi sia simile al seguente:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet26":::

    > [!NOTE]
    > Poiché facendo doppio clic su una cella in un intervallo Excel viene attivata la modalità di modifica, si verifica un evento quando la selezione viene spostata all'esterno dell'intervallo anche se non si sono verificate modifiche <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> al testo.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Aggiungere codice per rispondere all'evento SelectionChange

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Per inserire testo in namedRange2 in base all'evento SelectionChange

1. Aggiungere il codice in **modo NamedRange1_SelectionChange** gestore eventi simile al seguente:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet27":::

    > [!NOTE]
    > Poiché facendo doppio clic su una cella in un intervallo Excel la selezione viene spostata nell'intervallo, si verifica un evento prima che <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> si <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> verifichi l'evento .

## <a name="test-the-application"></a>Testare l'applicazione
 È ora possibile testare la cartella di lavoro per verificare che il testo che descrive gli eventi di un controllo sia inserito in un altro intervallo denominato <xref:Microsoft.Office.Tools.Excel.NamedRange> quando vengono generati gli eventi.

### <a name="to-test-your-document"></a>Per testare il documento

1. Premere **F5** per eseguire il progetto.

2. Posizionare il cursore in e verificare che il testo relativo all'evento sia inserito e che nel foglio di lavoro `namedRange1` <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> sia inserito un commento.

3. Fare doppio clic all'interno di e verificare che il testo relativo agli eventi sia inserito con testo in `namedRange1` <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> corsivo rosso in `namedRange2` .

4. Fare clic all'esterno di e notare che l'evento di modifica si verifica quando si esce dalla modalità di modifica anche se non è stata `namedRange1` apportata alcuna modifica al testo.

5. Modificare il testo all'interno di `namedRange1` .

6. Fare clic `namedRange1` all'esterno di e verificare che il testo relativo all'evento sia inserito con testo blu in <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> `namedRange2` .

## <a name="next-steps"></a>Passaggi successivi
 Questa procedura dettagliata illustra le nozioni di base della programmazione sugli eventi di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo . Ecco un'attività che potrebbe essere successiva:

- Distribuzione del progetto. Per altre informazioni, vedere [Deploy an Office solution](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Vedi anche
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Procedura: Aggiungere controlli NamedRange ai fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Procedura: Creare gestori eventi in Office progetto](../vsto/how-to-create-event-handlers-in-office-projects.md)
