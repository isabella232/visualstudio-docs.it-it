---
title: 'Procedura: Aggiungere controlli NamedRange ai fogli di lavoro'
description: Informazioni su come aggiungere controlli NamedRange a un foglio Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e6192a4fcd8a10f2152fc26602e52e3f9ec44f58
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122904"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Procedura: Aggiungere controlli NamedRange ai fogli di lavoro
  È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro di Microsoft Office Excel in fase di progettazione e in fase di esecuzione nei progetti a livello di documento.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 È anche possibile aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> in fase di esecuzione nei progetti di componente aggiuntivo VSTO.

 Questo argomento descrive le attività seguenti:

- [Aggiungere controlli NamedRange in fase di progettazione](#designtime)

- [Aggiungere controlli NamedRange in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Aggiungere controlli NamedRange in fase di esecuzione in un VSTO di componente aggiuntivo](#runtimeaddin)

  Per altre informazioni sui <xref:Microsoft.Office.Tools.Excel.NamedRange> controlli, vedere [Controllo NamedRange](../vsto/namedrange-control.md).

## <a name="add-namedrange-controls-at-design-time"></a><a name="designtime"></a> Aggiungere controlli NamedRange in fase di progettazione
 Esistono diversi modi per aggiungere controlli <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro in un progetto a livello di documento in fase di progettazione: da Excel, dalla **casella degli strumenti** di Visual Studio e dalla finestra **Origini dati** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro usando la casella Nome in Excel

1. Selezionare una o più celle da includere nell'intervallo denominato.

2. Nella casella **Nome digitare** un nome per l'intervallo e premere **INVIO.**

     La casella **Nome** si trova accanto alla barra della formula, sopra la colonna **A** del foglio di lavoro.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro con la Casella degli strumenti

1. Aprire la **Casella degli strumenti** e fare clic sulla scheda **Controlli Excel** .

2. Fare clic su <xref:Microsoft.Office.Tools.Excel.NamedRange> e trascinarlo in un foglio di lavoro.

     Verrà visualizzata la finestra di dialogo **Aggiungi controllo NamedRange** .

3. Selezionare una o più celle da includere nell'intervallo denominato.

4. Fare clic su **OK**.

     Se non si vuole assegnare al controllo il nome predefinito, è possibile modificarlo nella finestra **Proprietà** .

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro con la finestra Origini dati

1. Aprire la finestra **Origini dati** e creare un'origine dati per il progetto. Per altre informazioni, vedere [Aggiungere nuove connessioni.](../data-tools/add-new-connections.md)

2. Trascinare un singolo campo dalla finestra **Origini dati** al foglio di lavoro.

     Un controllo con associazione ai dati <xref:Microsoft.Office.Tools.Excel.NamedRange> viene aggiunto al foglio di lavoro. Per altre informazioni, vedere [Data binding e Windows Forms.](/dotnet/framework/winforms/data-binding-and-windows-forms)

## <a name="add-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Aggiungere controlli NamedRange in fase di esecuzione in un progetto a livello di documento
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a livello di codice al foglio di lavoro in fase di esecuzione e creare in questo modo i controlli host in risposta a eventi. Gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere [Aggiungere controlli Office documenti in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro a livello di codice

1. Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1`inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> alla cella **A1** e impostarne la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> su `Hello world!`

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet3":::

## <a name="add-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>Aggiungere controlli NamedRange in fase di esecuzione in un progetto VSTO componente aggiuntivo
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Gli intervalli denominati creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host alla chiusura del foglio di lavoro. Per altre informazioni, vedere Estendere documenti di Word e Excel cartelle di lavoro in VSTO [componenti aggiuntivi in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo NamedRange a un foglio di lavoro a livello di codice

1. Il codice seguente genera un elemento host del foglio di lavoro basato sul foglio di lavoro aperto, quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> alla cella **A1** e ne imposta la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> su `Hello world`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Vedi anche
- [Estendere documenti di Word Excel cartelle di lavoro in VSTO componenti aggiuntivi in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli sui Office di lavoro](../vsto/controls-on-office-documents.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
