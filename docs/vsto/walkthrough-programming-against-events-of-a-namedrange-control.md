---
title: 'Procedura dettagliata: Programmazione per eventi di un controllo NamedRange'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 020d10aec83cd9249378c326f02ba37c3721b126
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910818"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Procedura dettagliata: Programmazione per eventi di un controllo NamedRange
  Questa procedura dettagliata illustra come aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un foglio di lavoro di Microsoft Office Excel e un programma per i relativi eventi usando gli strumenti di sviluppo per Office in Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un foglio di lavoro.  
  
-   Programmare <xref:Microsoft.Office.Tools.Excel.NamedRange> agli eventi di controllo.  
  
-   Testare il progetto.  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Creare il progetto  
 In questo passaggio si creerà un progetto cartella di lavoro di Excel utilizzando Visual Studio.  
  
### <a name="to-create-a-new-project"></a>Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **My Events intervallo denominato**. Verificare che l'opzione **creare un nuovo documento** sia selezionata. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il **eventi di intervallo denominato My** progetto al **Esplora soluzioni**.  
  
## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Aggiungere testo e intervalli denominati per il foglio di lavoro  
 Poiché i controlli host sono estese agli oggetti di Office, è possibile aggiungerli al documento nello stesso modo si aggiungerà l'oggetto nativo. Ad esempio, è possibile aggiungere un Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un foglio di lavoro, aprire il **inserire** menu, che punta alla **nome**e scegliendo **Definisci**. È anche possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo trascinandolo dal **casella degli strumenti** nel foglio di lavoro.  
  
 In questo passaggio si aggiungeranno due controlli di intervallo denominato al foglio di lavoro usando il **casella degli strumenti**e quindi aggiungere testo al foglio di lavoro.  
  
### <a name="to-add-a-range-to-your-worksheet"></a>Per aggiungere un intervallo al foglio di lavoro  
  
1.  Verificare che il *My denominato intervallo Events.xlsx* cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzato.  
  
2.  Dal **controlli Excel** della casella degli strumenti, trascinare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo alla cella **A1** in `Sheet1`.  
  
     Il **Aggiungi controllo NamedRange** verrà visualizzata la finestra di dialogo.  
  
3.  Verificare che **$A 1 dollaro** viene visualizzato nella casella di testo modificabile e che la cella **A1** sia selezionata. In caso contrario, fare clic sulla cella **A1** per selezionarlo.  
  
4.  Fare clic su **OK**.  
  
     Cella **A1** diventa un intervallo denominato `namedRange1`. Non sono presenti indicazioni visibili nel foglio di lavoro, ma `namedRange1` viene visualizzato nei **nome** finestra (che si trova sul lato sinistro del foglio di lavoro) quando la cella **A1** sia selezionata.  
  
5.  Aggiungere un'altra <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo alla cella **B3**.  
  
6.  Verificare che **$B 3 dollari** viene visualizzato nella casella di testo modificabile e che la cella **B3** sia selezionata. In caso contrario, fare clic sulla cella **B3** per selezionarlo.  
  
7.  Fare clic su **OK**.  
  
     Cella **B3** diventa un intervallo denominato `namedRange2`.  
  
### <a name="to-add-text-to-your-worksheet"></a>Per aggiungere testo al foglio di lavoro  
  
1. Nella cella **A1**, digitare il testo seguente:  
  
    **Questo è un esempio di un controllo NamedRange.**  
  
2. Nella cella **A3** (a sinistra del `namedRange2`), digitare il testo seguente:  
  
    **Eventi:**  
  
   Nelle sezioni seguenti, si scriverà codice che inserisce il testo in `namedRange2` e modificare le proprietà del `namedRange2` controllo in risposta al <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, e <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> degli eventi di `namedRange1`.  
  
## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Aggiungere il codice per rispondere all'evento BeforeDoubleClick  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Per inserire il testo in base all'evento BeforeDoubleClick NamedRange2  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su **Sheet1.vb** oppure **Sheet1.cs** e selezionare **Visualizza codice**.  
  
2.  Aggiungere il codice in modo che il `namedRange1_BeforeDoubleClick` gestore dell'evento è simile a quanto segue:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  In c#, è necessario aggiungere i gestori eventi per l'intervallo denominato, come illustrato nella <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> eventi riportato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="add-code-to-respond-to-the-change-event"></a>Aggiungere il codice per rispondere all'evento di modifica  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Per inserire il testo in base all'evento di modifica namedRange2  
  
1.  Aggiungere il codice in modo che il `NamedRange1_Change` gestore dell'evento è simile a quanto segue:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Poiché facendo doppio clic su una cella in un intervallo di Excel passa alla modalità di modifica, un <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> evento si verifica quando la selezione viene spostata all'esterno dell'intervallo, anche se si è verificata alcuna modifica al testo.  
  
## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Aggiungere il codice per rispondere a SelectionChange (evento)  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Per inserire il testo in base all'evento SelectionChange namedRange2  
  
1.  Aggiungere il codice in modo che il **NamedRange1_SelectionChange** gestore dell'evento è simile a quanto segue:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Poiché facendo doppio clic su una cella in un intervallo di Excel fa in modo che la selezione spostare nell'intervallo, un <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> evento si verifica prima il <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> evento si verifica.  
  
## <a name="test-the-application"></a>Testare l'applicazione  
 A questo punto è possibile testare la cartella di lavoro per verificare che il testo che descrive gli eventi di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo viene inserito in un altro intervallo denominato quando vengono generati gli eventi.  
  
### <a name="to-test-your-document"></a>Per testare il documento  
  
1.  Premere **F5** per eseguire il progetto.  
  
2.  Posizionare il cursore nella `namedRange1`e verificare che il testo per quanto riguarda il <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> evento verrà inserito e che viene inserito un commento nel foglio di lavoro.  
  
3.  Fare doppio clic all'interno `namedRange1`e verificare che il testo per quanto riguarda <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> eventi viene inserita con testo in corsivo di colore rosso in `namedRange2`.  
  
4.  Fare clic all'esterno di `namedRange1` e notare che l'evento di modifica si verifica quando si esce dalla modalità di modifica, anche se è stata apportata alcuna modifica al testo.  
  
5.  Modificare il testo all'interno di `namedRange1`.  
  
6.  Fare clic all'esterno di `namedRange1`e verificare che il testo per quanto riguarda <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> evento viene inserito con testo in blu in `namedRange2`.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra i concetti fondamentali di programmazione per eventi di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo. Di seguito è un'attività successiva potrebbe essere:  
  
-   La distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Procedura: Aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Procedura: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
