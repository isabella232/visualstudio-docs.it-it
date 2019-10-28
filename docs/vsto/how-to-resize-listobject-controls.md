---
title: 'Procedura: ridimensionare i controlli ListObject'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fdebceb7ed6357542877bf13522425f7c013da73
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985750"
---
# <a name="how-to-resize-listobject-controls"></a>Procedura: ridimensionare i controlli ListObject
  Impostare la dimensione di un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> quando lo si aggiunge a una cartella di lavoro di Microsoft Office Excel; tuttavia, potrebbe essere necessario ridimensionarlo in seguito. Ad esempio, potrebbe essere necessario cambiare un elenco a due colonne in uno a tre colonne.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È possibile ridimensionare controlli <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di progettazione oppure in fase di esecuzione in progetti a livello di documento. È possibile ridimensionare i controlli <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione in un progetto di componente aggiuntivo VSTO.

 Questo argomento descrive le attività seguenti:

- [Ridimensiona controlli ListObject in fase di progettazione](#designtime)

- [Ridimensionare i controlli ListObject in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Ridimensionare i controlli ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)

  Per ulteriori informazioni sui controlli <xref:Microsoft.Office.Tools.Excel.ListObject>, vedere [controllo ListObject](../vsto/listobject-control.md).

## <a name="designtime"></a>Ridimensionare un controllo ListObject in fase di progettazione
 Per ridimensionare un elenco, è possibile selezionare e trascinare uno dei punti di controllo oppure è possibile ridefinirne la dimensione nella finestra di dialogo **Ridimensiona elenco** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Per ridimensionare un elenco usando la finestra di dialogo Ridimensiona elenco

1. Fare clic in un punto qualsiasi della tabella <xref:Microsoft.Office.Tools.Excel.ListObject>. Viene visualizzata la scheda **Strumenti tabella** > **progettazione** della barra multifunzione.

2. Nella sezione Proprietà fare clic su **Ridimensiona tabella**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Consente di selezionare il nuovo intervallo di dati per la tabella.

4. Fare clic su **OK**.

## <a name="runtimedoclevel"></a>Ridimensionare un controllo ListObject in fase di esecuzione in un progetto a livello di documento
 È possibile ridimensionare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in fase di esecuzione usando il metodo <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Non è possibile usare questo metodo per spostare il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in una nuova posizione nel foglio di lavoro. Le intestazioni devono rimanere nella stessa riga e il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ridimensionato deve sovrapporsi all'oggetto elenco originale. Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ridimensionato deve contenere una riga di intestazione e almeno una riga di dati.

### <a name="to-resize-a-list-object-programmatically"></a>Per ridimensionare un oggetto elenco a livello di codice

1. Creare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che si estende dalla cella **A1** a quella **B3** in `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Ridimensionare l'elenco in modo da includere le celle da **A1** a **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="runtimeaddin"></a>Ridimensionare un controllo ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO
 È possibile ridimensionare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in qualsiasi foglio di lavoro aperto in fase di esecuzione. Per altre informazioni su come aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di dati usando un componente aggiuntivo VSTO, vedere [procedura: aggiungere controlli ListObject a fogli di](../vsto/how-to-add-listobject-controls-to-worksheets.md)dati.

### <a name="to-resize-a-list-object-programmatically"></a>Per ridimensionare un oggetto elenco a livello di codice

1. Creare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che si estende dalla cella **A1** a quella **B3** in `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Ridimensionare l'elenco in modo da includere le celle da **A1** a **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Vedere anche
- [Estendi i documenti di Word e le cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject (controllo)](../vsto/listobject-control.md)
- [Procedura: aggiungere controlli ListObject a fogli di foglio](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Procedura: ridimensionare i controlli Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Procedura: ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)
