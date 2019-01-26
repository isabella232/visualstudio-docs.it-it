---
title: 'Procedura dettagliata: La modifica del foglio di lavoro della formattazione mediante controlli CheckBox'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 30e89adf2d93e67a63071f79ded213a3dcff6385
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871026"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Procedura dettagliata: La modifica del foglio di lavoro della formattazione mediante controlli CheckBox
  Questa procedura dettagliata illustra le nozioni di base dell'uso di caselle di controllo in un foglio di lavoro di Microsoft Office Excel per modificare la formattazione. Si userà gli strumenti di sviluppo per Office in Visual Studio per creare e aggiungere codice al progetto. Per visualizzare il risultato come un esempio completo, vedere l'esempio di controlli Excel all'indirizzo [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Aggiungere testo e controlli a un foglio di lavoro.  
  
-   Formattare il testo quando si seleziona un'opzione.  
  
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
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **formattazione in Excel**. Verificare che l'opzione **creare un nuovo documento** sia selezionata. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il **formattazione in Excel** progetto al **Esplora soluzioni**.  
  
## <a name="add-text-and-controls-to-the-worksheet"></a>Aggiungere testo e controlli al foglio di lavoro  
 Per questa procedura dettagliata, sono necessari tre <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controlli e testo in un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo.  
  
### <a name="to-add-three-check-boxes"></a>Per aggiungere tre caselle di controllo  
  
1.  Verificare che sia aperta nella finestra di progettazione di Visual Studio e che la cartella di lavoro `Sheet1` è aperto.  
  
2.  Dal **controlli comuni** scheda della finestra di **della casella degli strumenti**, trascinare un <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controllo o accanto alla cella **B2** in **Sheet1**.  
  
3.  Dal **View** dal menu **proprietà** finestra.  
  
4.  Assicurarsi che **Checkbox1** è visibile nella casella di riepilogo Nome oggetto del **proprietà** finestra e modificare le proprietà seguenti:  
  
    |Proprietà|Value|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**per**|**Grassetto**|  
  
5.  Trascinare una seconda casella di controllo in o accanto alla cella **B4** e modificare le proprietà seguenti:  
  
    |Proprietà|Value|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**per**|**Corsivo**|  
  
6.  Trascinare una terza casella di controllo in o accanto alla cella **B6** e modificare le proprietà seguenti:  
  
    |Proprietà|Value|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**per**|**Carattere di sottolineatura**|  
  
7.  Selezionare tutti i controlli casella di controllo tre tenendo il **Ctrl** chiave.  
  
8.  Nel gruppo di disposizione della scheda formato Excel, fare clic su **Align**, quindi fare clic su **Allinea a sinistra**.  
  
     Le tre caselle di controllo sono allineate a sinistra, in corrispondenza della posizione del primo controllo che è selezionata.  
  
     Successivamente, verrà trascinato un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nel foglio di lavoro.  
  
    > [!NOTE]  
    >  È anche possibile aggiungere il <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo digitando **textFont** nel **nome** casella.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Per aggiungere testo a un controllo NamedRange  
  
1. Dal **controlli Excel** della casella degli strumenti, trascinare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo alla cella **B9**.  
  
2. Verificare che **$B$ 9** viene visualizzato nella casella di testo modificabile e che la cella **B9** sia selezionata. In caso contrario, fare clic sulla cella **B9** per selezionarlo.  
  
3. Fare clic su **OK**.  
  
4. Cella **B9** diventa un intervallo denominato `NamedRange1`.  
  
    Non sono presenti indicazioni visibili nel foglio di lavoro, ma `NamedRange1` viene visualizzato nei **casella nome** (di sotto del foglio di lavoro sul lato sinistro) quando la cella **B9** sia selezionata.  
  
5. Assicurarsi che **NamedRange1** è visibile nella casella di riepilogo Nome oggetto del **proprietà** finestra e modificare le proprietà seguenti:  
  
   |Proprietà|Value|  
   |--------------|-----------|  
   |**Name**|**textFont**|  
   |**Value2**|**Fare clic su una casella di controllo per modificare la formattazione del testo.**|  
  
   Successivamente, scrivere il codice per formattare il testo quando si seleziona un'opzione.  
  
## <a name="format-the-text-when-an-option-is-selected"></a>Formattare il testo quando si seleziona un'opzione  
 In questa sezione si scriverà codice in modo che quando l'utente seleziona un'opzione di formattazione, il formato del testo nel foglio di lavoro è stato modificato.  
  
### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Per modificare la formattazione quando una casella di controllo è selezionata  
  
1.  Fare doppio clic su **Sheet1**, quindi fare clic su **Visualizza codice** menu di scelta rapida.  
  
2.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del `applyBoldFont` casella di controllo:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del `applyItalicFont` casella di controllo:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del `applyUnderlineFont` casella di controllo:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  In c#, è necessario aggiungere i gestori eventi per le caselle di controllo per il <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, come illustrato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
 È ora possibile testare la cartella di lavoro per assicurarsi che il testo è formattato correttamente quando si seleziona o deseleziona una casella di controllo.  
  
### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro  
  
1.  Premere **F5** per eseguire il progetto.  
  
2.  Selezionare o deselezionare una casella di controllo.  
  
3.  Verificare che il testo è formattato correttamente.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base usando le caselle di controllo e la formattazione del testo in fogli di lavoro di Excel. Ecco alcune possibili attività successive:  
  
-   La distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
-   Usare un pulsante per popolare una casella di testo. Per altre informazioni, vedere [Procedura dettagliata: Visualizzare il testo in una casella di testo in un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
