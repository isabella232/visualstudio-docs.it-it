---
title: 'Procedura: Aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4630834f1673e1c96ca67b90a8bb329951f53de1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827020"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Procedura: Aggiungere un riquadro Azioni ai documenti Word o alle cartelle di lavoro Excel
  Per aggiungere un riquadro azioni a un documento di Microsoft Office Word o una cartella di lavoro di Microsoft Excel, creare innanzitutto un controllo utente Windows Form. Quindi, aggiungere il controllo utente per il <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> proprietà del `ThisDocument.ActionsPane` campo (Word) o `ThisWorkbook.ActionsPane` campo (Excel) nel progetto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Creazione del controllo utente  
 La procedura seguente illustra come creare un controllo utente o un progetto di Excel. Aggiunge anche un pulsante al controllo utente che scrive il testo nel documento o cartella di lavoro quando viene selezionato.  
  
#### <a name="to-create-the-user-control"></a>Per creare il controllo utente  
  
1.  Aprire il progetto a livello di documento di Word o Excel in Visual Studio.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nel **Aggiungi nuovo elemento** finestra di dialogo **controllo del riquadro azioni**, denominarlo **HelloControl**e fare clic su **Aggiungi**.  
  
    > [!NOTE]  
    >  In alternativa, è possibile aggiungere un **controllo utente** elemento al progetto. Le classi generate per il **controllo riquadro azioni** e **controllo utente** gli elementi sono funzionalmente equivalenti.  
  
4.  Dal **Windows Forms** scheda della finestra di **della casella degli strumenti,** trascinare un **pulsante** controllo nel controllo.  
  
    > [!NOTE]  
    >  Se il controllo non è visibile nella finestra di progettazione, fare doppio clic su **HelloControl** nelle **Esplora soluzioni**.  
  
5.  Aggiungere il codice per il <xref:System.Windows.Forms.Control.Click> gestore dell'evento del pulsante. Nell'esempio seguente viene illustrato il codice per un documento di Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  In c#, è necessario aggiungere un gestore eventi per il clic del pulsante. È possibile inserire il codice nel `HelloControl` dopo la chiamata al costruttore `InitializeComponent`.  
  
     Per informazioni su come creare gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>Aggiungere il controllo utente al riquadro azioni  
 Per visualizzare il riquadro azioni, aggiungere il controllo utente per il <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> proprietà del `ThisDocument.ActionsPane` campo (Word) o `ThisWorkbook.ActionsPane` campo (Excel).  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>Per aggiungere il controllo utente al riquadro azioni  
  
1.  Aggiungere il codice seguente per il `ThisDocument` o `ThisWorkbook` classe come una dichiarazione a livello di classe (non aggiungere questo codice a un metodo).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Aggiungere il codice seguente per il `ThisDocument_Startup` gestore dell'evento del `ThisDocument` classe o il `ThisWorkbook_Startup` gestore dell'evento del `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Procedura dettagliata: Inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procedura: Gestire il layout dei controlli nei riquadri azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Procedura dettagliata: Inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
