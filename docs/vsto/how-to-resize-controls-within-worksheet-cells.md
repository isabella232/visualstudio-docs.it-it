---
title: 'Procedura: Ridimensionare i controlli nelle celle di un foglio di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b51f26a4ea2dec50c5ee90c38f49412866b6f866
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961491"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Procedura: Ridimensionare i controlli nelle celle di un foglio di lavoro
  Quando si ridimensiona colonne o righe in un foglio di lavoro, tutti i controlli host all'interno delle celle viene ridimensionato automaticamente per l'altezza o la larghezza della cella che è stata ridimensionata. Controlli Windows Form non vengono ridimensionano automaticamente per impostazione predefinita.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Se si aggiungono i controlli in fase di progettazione, è necessario impostare opzioni di posizionamento per ogni controllo.

 Se si aggiunge un controllo Windows Form a livello di codice e fornire un argomento di intervallo, il controllo viene ridimensionato automaticamente durante il ridimensionamento di una cella all'interno dell'intervallo. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Ridimensionare i controlli in fase di progettazione

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Per impostare i controlli per ridimensionare le celle in fase di progettazione

1. Dal **casella degli strumenti**, trascinare un controllo Windows Form a un foglio di lavoro.

2. Il pulsante destro del controllo e quindi fare clic su **formato controllo**.

3. Nel **formato controllo** finestra di dialogo, fare clic sul **proprietà** scheda.

4. Sotto **oggetto posizionamento**, selezionare la **spostare e ridimensionare con le celle** opzione e quindi fare clic su **OK**.

     Quando si ridimensiona la cella che contiene il controllo, il controllo viene ridimensionato per adattarsi alla cella.

## <a name="resize-controls-at-runtime"></a>Ridimensionare i controlli in fase di esecuzione
 Se si aggiunge un controllo Windows Form in fase di esecuzione e passare un <xref:Microsoft.Office.Interop.Excel.Range> come percorso per il controllo, il controllo viene ridimensionato automaticamente quando la cella di foglio di lavoro che contiene l'intervallo viene ridimensionata.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Per impostare i controlli per ridimensionare le celle in fase di esecuzione

1. Aggiungere un controllo intervallo A1.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Quando si ridimensiona la cella che contiene il controllo, il controllo viene ridimensionato per adattarsi alla cella.

## <a name="reset-control-placement"></a>Reimpostare il posizionamento dei controlli
 È possibile reimpostare la posizione e il ridimensionamento del controllo impostando il `Placement` proprietà su uno dei seguenti <xref:Microsoft.Office.Interop.Excel.XlPlacement> valori:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Per modificare il comportamento di un controllo in modo che non ridimensionare o spostare la cella contenente

1. Chiamare la proprietà di posizionamento del controllo e impostare il valore su <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Vedere anche
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Procedura: Aggiungere controlli Windows Form ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedura: Nascondere controlli nei fogli di lavoro durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
