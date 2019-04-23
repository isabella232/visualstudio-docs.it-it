---
title: 'Procedura: Ridimensionare i controlli ListObject'
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
ms.openlocfilehash: af494a87b2feea10d121e59931e51ef3dd344f67
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669302"
---
# <a name="how-to-resize-listobject-controls"></a>Procedura: Ridimensionare i controlli ListObject
  Impostare la dimensione di un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> quando lo si aggiunge a una cartella di lavoro di Microsoft Office Excel; tuttavia, potrebbe essere necessario ridimensionarlo in seguito. Ad esempio, potrebbe essere necessario cambiare un elenco a due colonne in uno a tre colonne.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È possibile ridimensionare <xref:Microsoft.Office.Tools.Excel.ListObject> controlli in fase di progettazione o in fase di esecuzione nei progetti a livello di documento. È possibile ridimensionare <xref:Microsoft.Office.Tools.Excel.ListObject> controlli in fase di esecuzione in un progetto di componente aggiuntivo VSTO.

 Questo argomento descrive le attività seguenti:

- [Ridimensionare i controlli ListObject in fase di progettazione](#designtime)

- [Ridimensionare i controlli ListObject in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Ridimensionare i controlli ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)

  Per altre informazioni sulle <xref:Microsoft.Office.Tools.Excel.ListObject> controlli, vedere [controllo ListObject](../vsto/listobject-control.md).

  ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [ricerca per categorie Aggiungere colonne a un oggetto elenco associato a dati in fase di esecuzione? ](http://go.microsoft.com/fwlink/?LinkID=130318).

##  <a name="designtime"></a> Ridimensiona un controllo ListObject in fase di progettazione
 Per ridimensionare un elenco, è possibile selezionare e trascinare uno dei punti di controllo oppure è possibile ridefinirne la dimensione nella finestra di dialogo **Ridimensiona elenco** .

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Per ridimensionare un elenco usando la finestra di dialogo Ridimensiona elenco

1.  Fare clic in qualsiasi punto nel <xref:Microsoft.Office.Tools.Excel.ListObject> tabella. Il **strumenti di tabelle** > **progettazione** verrà visualizzata la scheda nella barra multifunzione.

2.  Nella sezione proprietà, fare clic su **Ridimensiona tabella**.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3.  Selezionare il nuovo intervallo di dati per la tabella.

4.  Fare clic su **OK**.

##  <a name="runtimedoclevel"></a> Ridimensiona un controllo ListObject in fase di esecuzione in un progetto a livello di documento
 È possibile ridimensionare un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo in fase di esecuzione usando il <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> (metodo). Non è possibile usare questo metodo per spostare il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> in una nuova posizione nel foglio di lavoro. Le intestazioni devono rimanere nella stessa riga e il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ridimensionato deve sovrapporsi all'oggetto elenco originale. Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ridimensionato deve contenere una riga di intestazione e almeno una riga di dati.

### <a name="to-resize-a-list-object-programmatically"></a>Per ridimensionare un oggetto elenco a livello di codice

1.  Creare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che si estende dalla cella **A1** a quella **B3** in `Sheet1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2.  Ridimensionare l'elenco in modo da includere le celle da **A1** a **C5**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

##  <a name="runtimeaddin"></a> Ridimensionare un controllo ListObject in fase di esecuzione in un progetto di componente aggiuntivo VSTO
 È possibile ridimensionare un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo su qualsiasi foglio di lavoro aperto in fase di esecuzione. Per altre informazioni su come aggiungere un <xref:Microsoft.Office.Tools.Excel.ListObject> il controllo a un foglio di lavoro usando un componente aggiuntivo VSTO, vedere [come: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Per ridimensionare un oggetto elenco a livello di codice

1.  Creare un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che si estende dalla cella **A1** a quella **B3** in `Sheet1`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2.  Ridimensionare l'elenco in modo da includere le celle da **A1** a **C5**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Vedere anche
- [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject (controllo)](../vsto/listobject-control.md)
- [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Procedura: Ridimensionare i controlli Bookmark](../vsto/how-to-resize-bookmark-controls.md)
- [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)
