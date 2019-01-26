---
title: 'Procedura: Gestire il layout dei controlli nei riquadri azioni'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 87ec74628bad3d4c0e2031b8399e279bc9b5229d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873119"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Procedura: Gestire il layout dei controlli nei riquadri azioni
  Un riquadro azioni viene ancorato a destra di un documento o foglio di lavoro per impostazione predefinita. Tuttavia, possono essere ancorata a sinistra, superiore o inferiore. Se si usano più controlli utente, è possibile scrivere codice per sovrapporre correttamente i controlli utente del riquadro azioni. Per altre informazioni, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L'ordine di sovrapposizione dei controlli dipende se il riquadro azioni è ancorato in verticale o orizzontale.  
  
> [!NOTE]  
>  Se l'utente ridimensiona il riquadro azioni in fase di esecuzione, è possibile impostare i controlli per ridimensionare il riquadro azioni. È possibile usare la proprietà <xref:System.Windows.Forms.Control.Anchor%2A> di un controllo Windows Form per ancorare i controlli al riquadro azioni. Per altre informazioni, vedere [Procedura: Agganciare i controlli in Windows Form](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
> [!NOTE]  
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Per impostare l'ordine dello stack dei controlli riquadro azioni  
  
1.  Aprire un progetto a livello di documento per Microsoft Office Word che include un riquadro azioni con più controlli utente o controlli del riquadro azioni annidati. Per altre informazioni, vedere [Procedura: Aggiungere un riquadro azioni ai documenti di Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Fare doppio clic su **ThisDocument.cs** oppure **ThisDocument. vb** nelle **Esplora soluzioni** e quindi fare clic su **Visualizza codice**.  
  
3.  Nel <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> gestore dell'evento del riquadro azioni, controllare se l'orientamento del riquadro azioni è orizzontale.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  Se l'orientamento orizzontale, stack i controlli del riquadro azioni da sinistra. in caso contrario, li sovrapposizione dall'alto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  In c#, è necessario aggiungere un gestore eventi per il `ActionsPane` per il <xref:Microsoft.Office.Tools.Word.Document.Startup> gestore dell'evento. Per informazioni sulla creazione di gestori eventi, vedere [come: Creare i gestori eventi nei progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  Eseguire il progetto e verificare che i controlli del riquadro azioni sono in pila da sinistra a destra quando il riquadro azioni è ancorato alla parte superiore del documento e i controlli sono impilati dall'alto verso il basso per il riquadro azioni viene ancorato a destra del documento.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Controlla un progetto a livello di documento di Word con un riquadro delle azioni che contiene più controlli utente o del riquadro azioni annidati.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)   
 [Procedura: Aggiungere un riquadro azioni ai documenti Word o le cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura: Aggiungere un riquadro azioni a cartelle di lavoro documenti di Word o Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura dettagliata: Inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procedura dettagliata: Inserire testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
