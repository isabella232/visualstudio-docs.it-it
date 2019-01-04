---
title: 'Procedura dettagliata: Testo visualizzato in una casella di testo in un foglio di lavoro tramite un pulsante'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d7cf32019d3bfa1e6690512f4f348728a409bbb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941610"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Procedura dettagliata: Testo visualizzato in una casella di testo in un foglio di lavoro tramite un pulsante
  Questa procedura dettagliata illustra le nozioni di base dell'uso di pulsanti e caselle di testo in fogli di lavoro di Microsoft Office Excel e come creare progetti di Excel con strumenti di sviluppo per Office in Visual Studio. Per visualizzare il risultato come un esempio completo, vedere l'esempio di controlli Excel all'indirizzo [procedure dettagliate ed esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Aggiungere controlli a un foglio di lavoro.  
  
-   Popolare una casella di testo quando viene selezionato un pulsante.  
  
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
  
1.  Creare un progetto cartella di lavoro di Excel con il nome **My Button Excel**. Verificare che l'opzione **creare un nuovo documento** sia selezionata. Per altre informazioni, vedere [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio verrà visualizzata la nuova cartella di lavoro di Excel nella finestra di progettazione e aggiunge il **My Button Excel** progetto al **Esplora soluzioni**.  
  
## <a name="add-controls-to-the-worksheet"></a>Aggiungere controlli al foglio di lavoro  
 Per questa procedura dettagliata, è necessario un pulsante e una casella di testo nel primo foglio di lavoro.  
  
### <a name="to-add-a-button-and-a-text-box"></a>Per aggiungere un pulsante e una casella di testo  
  
1. Verificare che il **My Excel Button.xlsx** cartella di lavoro è aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzato.  
  
2. Dal **controlli comuni** della casella degli strumenti, trascinare un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> a `Sheet1`.  
  
3. Dal **View** dal menu **finestra proprietà**.  
  
4. Assicurarsi che **TextBox1** è visibile nel **delle proprietà** casella di riepilogo a discesa di finestra e modificare il **nome** proprietà della casella di testo per **displayText**.  
  
5. Trascinare un **sul pulsante** sul controllo `Sheet1` e modificare le proprietà seguenti:  
  
   |Proprietà|Value|  
   |--------------|-----------|  
   |**Name**|**insertText**|  
   |**per**|**Inserisci testo**|  
  
   Scrivere ora il codice da eseguire quando si fa clic sul pulsante.  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Popolare la casella di testo quando si fa clic sul pulsante  
 Ogni volta che l'utente fa clic sul pulsante, **Hello World!** viene aggiunto alla casella di testo.  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Per scrivere nella casella di testo quando si fa clic sul pulsante  
  
1.  Nelle **Esplora soluzioni**, fare doppio clic su **Sheet1**, quindi fare clic su **Visualizza codice** menu di scelta rapida.  
  
2.  Aggiungere il codice seguente per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del pulsante:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  In c#, è necessario aggiungere un gestore eventi per il <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, come illustrato di seguito. Per informazioni sulla creazione di gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
 È ora possibile testare la cartella di lavoro per assicurarsi che il messaggio **Hello World!** Quando si fa clic sul pulsante, viene visualizzato nella casella di testo.  
  
### <a name="to-test-your-workbook"></a>Per testare la cartella di lavoro  
  
1.  Premere **F5** per eseguire il progetto.  
  
2.  Fare clic sul pulsante.  
  
3.  Verificare che **Hello World!** viene visualizzato nella casella di testo.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata illustra le nozioni di base dell'uso di pulsanti e caselle di testo in fogli di lavoro di Excel. Ecco alcune possibili attività successive:  
  
-   La distribuzione del progetto. Per altre informazioni, vedere [distribuire una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
-   Usando le caselle di controllo per modificare la formattazione. Per altre informazioni, vedere [Procedura dettagliata: Modificare la formattazione del foglio di lavoro mediante controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)   
 [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
