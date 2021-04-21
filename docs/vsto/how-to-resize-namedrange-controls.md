---
title: 'Procedura: Ridimensionare i controlli NamedRange'
description: Informazioni su come usare le Visual Studio ridimensionare a livello di codice i controlli NamedRange in una cartella di lavoro di Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3b70b34de222c35903a4f08b95d9efe8d8f896d9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826460"
---
# <a name="how-to-resize-namedrange-controls"></a>Procedura: Ridimensionare i controlli NamedRange
  È possibile impostare la dimensione di un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> quando lo si aggiunge a un documento di Microsoft Office Excel; tuttavia, potrebbe essere necessario ridimensionarlo in seguito.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È possibile ridimensionare un intervallo denominato in fase di progettazione oppure in fase di esecuzione in progetti a livello di documento. È inoltre possibile ridimensionare in fase di esecuzione intervalli denominati nei componenti aggiuntivi VSTO a livello di applicazione.

 Questo argomento descrive le attività seguenti:

- [Ridimensionare i controlli NamedRange in fase di progettazione](#designtime)

- [Ridimensionare i controlli NamedRange in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Ridimensionare i controlli NamedRange in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)

## <a name="resize-namedrange-controls-at-design-time"></a><a name="designtime"></a> Ridimensionare i controlli NamedRange in fase di progettazione
 È possibile ridimensionare un intervallo denominato ridefinendone le dimensioni nella finestra di dialogo **Definisci nome** .

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Per ridimensionare un intervallo denominato tramite la finestra di dialogo Definisci nome

1. Fare clic con il pulsante destro del mouse su un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> .

2. Fare clic su **Gestisci intervalli denominati** nel menu di scelta rapida.

     Viene visualizzata la finestra di dialogo **Definisci nome** .

3. Selezionare l'intervallo denominato che si intende ridimensionare.

4. Deselezionare la casella **Riferito a** .

5. Selezionare le celle che si vogliono usare per definire la dimensione dell'intervallo denominato.

6. Fare clic su **OK**.

## <a name="resize-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Ridimensionare i controlli NamedRange in fase di esecuzione in un progetto a livello di documento
 Per ridimensionare a livello di codice un intervallo denominato, è possibile usare la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> .

> [!NOTE]
> Nella finestra **Proprietà** la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> è contrassegnata come di sola lettura.

### <a name="to-resize-a-named-range-programmatically"></a>Per ridimensionare un intervallo denominato a livello di codice

1. Creare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> nella cella **A1** di `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet4":::

2. Ridimensionare l'intervallo denominato in modo da includere la cella **B1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet5":::

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Ridimensionare i controlli NamedRange in fase di esecuzione in un progetto di componente aggiuntivo VSTO
 È possibile ridimensionare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in qualsiasi foglio di lavoro aperto in fase di esecuzione. Per altre informazioni su come aggiungere un controllo a un foglio di lavoro usando un componente aggiuntivo VSTO, vedere Procedura: Aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> [NamedRange ai fogli di lavoro.](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

### <a name="to-resize-a-named-range-programmatically"></a>Per ridimensionare un intervallo denominato a livello di codice

1. Creare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> nella cella **A1** di `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet10":::

2. Ridimensionare l'intervallo denominato in modo da includere la cella **B1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet11":::

## <a name="see-also"></a>Vedi anche
- [Estendere documenti di Word e cartelle di lavoro di Excel nei componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizzare Excel tramite oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Procedura: Aggiungere controlli NamedRange ai fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Procedura: Ridimensionare i controlli Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Procedura: Ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)
