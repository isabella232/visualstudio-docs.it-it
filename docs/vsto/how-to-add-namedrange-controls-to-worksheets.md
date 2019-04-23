---
title: 'Procedura: Aggiungere controlli NamedRange a fogli di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2cc909828dc77c0f1dbe31c79255f2c93d2a95b3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066845"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Procedura: Aggiungere controlli NamedRange a fogli di lavoro
  È possibile aggiungere <xref:Microsoft.Office.Tools.Excel.NamedRange> controlli a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È anche possibile aggiungere <xref:Microsoft.Office.Tools.Excel.NamedRange> controlli in fase di esecuzione nei progetti di componente aggiuntivo VSTO.

 Questo argomento descrive le attività seguenti:

- [Aggiungere controlli NamedRange in fase di progettazione](#designtime)

- [Aggiungere controlli NamedRange in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Aggiungere controlli NamedRange in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)

  Per altre informazioni sulle <xref:Microsoft.Office.Tools.Excel.NamedRange> controlli, vedere [controllo NamedRange](../vsto/namedrange-control.md).

## <a name="designtime"></a> Aggiungere controlli NamedRange in fase di progettazione
 Esistono diversi modi per aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro in un progetto a livello di documento in fase di progettazione: da Excel, dalla **casella degli strumenti**di Visual Studio e dalla finestra **Origini dati** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro usando la casella Nome in Excel

1. Selezionare una o più celle da includere nell'intervallo denominato.

2. Nel **casella nome**, digitare un nome per l'intervallo e premere **invio**.

     La casella **Nome** si trova accanto alla barra della formula, sopra la colonna **A** del foglio di lavoro.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro con la Casella degli strumenti

1. Aprire la **Casella degli strumenti** e fare clic sulla scheda **Controlli Excel** .

2. Fare clic su <xref:Microsoft.Office.Tools.Excel.NamedRange> e trascinarlo in un foglio di lavoro.

     Verrà visualizzata la finestra di dialogo **Aggiungi controllo NamedRange** .

3. Selezionare una o più celle da includere nell'intervallo denominato.

4. Fare clic su **OK**.

     Se non si vuole assegnare al controllo il nome predefinito, è possibile modificarlo nella finestra **Proprietà** .

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro con la finestra Origini dati

1. Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per altre informazioni, vedere [aggiungere le nuove connessioni](../data-tools/add-new-connections.md).

2. Trascinare un singolo campo dalla finestra **Origini dati** al foglio di lavoro.

     Un controllo con associazione ai dati <xref:Microsoft.Office.Tools.Excel.NamedRange> viene aggiunto al foglio di lavoro. Per altre informazioni, vedere [Data binding e Windows Form](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="runtimedoclevel"></a> Aggiungere controlli NamedRange in fase di esecuzione in un progetto a livello di documento
 È possibile aggiungere un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a livello di codice al foglio di lavoro in fase di esecuzione. e creare in questo modo i controlli host in risposta a eventi. Gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro a livello di codice

1. Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1`inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> alla cella **A1** e impostarne la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> su `Hello world!`

     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]

## <a name="runtimeaddin"></a> Aggiungere controlli NamedRange in fase di esecuzione in un progetto di componente aggiuntivo VSTO
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [estendere documenti Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro a livello di codice

1. Il codice seguente genera un elemento host del foglio di lavoro basato sul foglio di lavoro aperto, quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> alla cella **A1** e ne imposta la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> su `Hello world`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]

## <a name="see-also"></a>Vedere anche
- [Estendere i documenti di Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
