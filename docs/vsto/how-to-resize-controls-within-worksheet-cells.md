---
title: "Procedura: ridimensionare i controlli all'interno di celle del foglio di comando"
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f2d22973e13ee77b66de303041f8b6a765b4b93a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545873"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Procedura: ridimensionare i controlli all'interno di celle del foglio di comando
  Quando si ridimensionano le colonne o le righe di un foglio di foglio, tutti i controlli host all'interno delle celle vengono automaticamente ridimensionati in altezza o larghezza della cella che è stata ridimensionata. Per impostazione predefinita, i controlli Windows Forms non vengono ridimensionati automaticamente.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Se si aggiungono i controlli in fase di progettazione, è necessario impostare le opzioni di posizionamento per ogni controllo.

 Se si aggiunge un controllo Windows Forms a livello di codice e si fornisce un argomento di intervallo, il controllo viene ridimensionato automaticamente quando una cella all'interno dell'intervallo viene ridimensionata. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Ridimensionare i controlli in fase di progettazione

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Per ridimensionare i controlli con le celle in fase di progettazione

1. Dalla **casella degli strumenti**trascinare un controllo Windows Forms in un foglio di foglio.

2. Fare clic con il pulsante destro del mouse sul controllo, quindi scegliere **formato controllo**.

3. Nella finestra di dialogo **formato controllo** fare clic sulla scheda **Proprietà** .

4. In **posizionamento oggetti**selezionare l'opzione **Sposta e dimensioni con celle** , quindi fare clic su **OK**.

     Quando si ridimensiona la cella che contiene il controllo, il controllo viene ridimensionato in base alla cella.

## <a name="resize-controls-at-run-time"></a>Ridimensionare i controlli in fase di esecuzione
 Se si aggiunge un controllo Windows Forms in fase di esecuzione e si passa un <xref:Microsoft.Office.Interop.Excel.Range> come percorso per il controllo, il controllo verrà ridimensionato automaticamente quando la cella del foglio di controllo che contiene l'intervallo viene ridimensionata.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Per ridimensionare i controlli con le celle in fase di esecuzione

1. Aggiungere un controllo all'intervallo a1.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Quando si ridimensiona la cella che contiene il controllo, il controllo viene ridimensionato in base alla cella.

## <a name="reset-control-placement"></a>Reimposta posizionamento del controllo
 È possibile reimpostare la posizione e il ridimensionamento del controllo impostando la `Placement` proprietà su uno dei <xref:Microsoft.Office.Interop.Excel.XlPlacement> valori seguenti:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Per modificare il comportamento di un controllo in modo che non venga ridimensionato o spostato con la cella

1. Chiamare la proprietà Placement del controllo e impostare il valore su <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Vedere anche
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Procedura: aggiungere controlli Windows Forms ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedura: nascondere i controlli nei fogli di foglio durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
