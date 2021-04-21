---
title: "Procedura: Ridimensionare i controlli all'interno delle celle del foglio di lavoro"
description: Informazioni su come usare le Visual Studio per ridimensionare i controlli all'interno delle celle del foglio di lavoro di Microsoft Excel sia in fase di progettazione che in fase di esecuzione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7b42c10fd82ec077b295a8bc683fa138c2eb095b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825745"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Procedura: Ridimensionare i controlli all'interno delle celle del foglio di lavoro
  Quando si ridimensionano colonne o righe in un foglio di lavoro, tutti i controlli host all'interno delle celle vengono automaticamente ridimensionati in base all'altezza o alla larghezza della cella ridimensionata. Windows Forms non vengono ridimensionati automaticamente per impostazione predefinita.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Se si aggiungono i controlli in fase di progettazione, è necessario impostare le opzioni di posizionamento per ogni controllo.

 Se si aggiunge un controllo Windows Forms a livello di codice e si specifica un argomento di intervallo, il controllo viene ridimensionato automaticamente quando viene ridimensionata una cella all'interno dell'intervallo. Per altre informazioni, vedere [Aggiungere controlli ai documenti di Office in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="resize-controls-at-design-time"></a>Ridimensionare i controlli in fase di progettazione

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Per ridimensionare i controlli con le celle in fase di progettazione

1. Dalla Casella **degli strumenti** trascinare un controllo Windows Forms in un foglio di lavoro.

2. Fare clic con il pulsante destro del mouse sul controllo e **quindi scegliere Formatta controllo**.

3. Nella finestra **di dialogo Controllo** formato fare clic sulla **scheda** Proprietà .

4. In **Posizionamento oggetti** selezionare l'opzione **Sposta e ridimensiona con** celle e quindi fare clic su **OK.**

     Quando si ridimensiona la cella che contiene il controllo , il controllo viene ridimensionato in base alla cella.

## <a name="resize-controls-at-run-time"></a>Ridimensionare i controlli in fase di esecuzione
 Se si aggiunge un controllo Windows Forms in fase di esecuzione e si passa un oggetto come posizione per il controllo, il controllo verrà ridimensionato automaticamente quando viene ridimensionata la cella del foglio di lavoro che contiene <xref:Microsoft.Office.Interop.Excel.Range> l'intervallo.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Per ridimensionare i controlli con le celle in fase di esecuzione

1. Aggiungere un controllo all'intervallo A1.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet5":::

     Quando si ridimensiona la cella che contiene il controllo , il controllo viene ridimensionato in base alla cella.

## <a name="reset-control-placement"></a>Reimpostare il posizionamento del controllo
 È possibile reimpostare la posizione e il ridimensionamento del controllo impostando la `Placement` proprietà su uno dei valori <xref:Microsoft.Office.Interop.Excel.XlPlacement> seguenti:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Per modificare il comportamento di un controllo in modo che non venga ridimensionato o spostato con la cella

1. Chiamare la proprietà di posizionamento del controllo e impostare il valore su <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet6":::

## <a name="see-also"></a>Vedi anche
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Procedura: Aggiungere controlli Windows Forms ai documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Procedura: Nascondere i controlli nei fogli di lavoro durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
