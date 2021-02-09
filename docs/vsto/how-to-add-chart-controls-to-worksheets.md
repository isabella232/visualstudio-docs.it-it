---
title: 'Procedura: aggiungere controlli Chart a fogli di foglio'
description: Informazioni su come è possibile aggiungere controlli Chart a un foglio di lavoro di Excel Microsoft Office in fase di progettazione e in fase di esecuzione nelle personalizzazioni a livello di documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4fd82cf9d8d5cb15215bf7ecbfa51c735ef52a0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917398"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Procedura: aggiungere controlli Chart a fogli di foglio
  È possibile aggiungere <xref:Microsoft.Office.Tools.Excel.Chart> controlli a un foglio di lavoro Microsoft Office Excel in fase di progettazione e in fase di esecuzione nelle personalizzazioni a livello di documento. È anche possibile aggiungere <xref:Microsoft.Office.Tools.Excel.Chart> controlli in fase di esecuzione nei componenti aggiuntivi VSTO.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Questo argomento descrive le attività seguenti:

- [Aggiunta di controlli Chart in fase di progettazione](#designtime)

- [Aggiungere controlli Chart in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Aggiungere controlli Chart in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)

  Per ulteriori informazioni sui <xref:Microsoft.Office.Tools.Excel.Chart> controlli, vedere [controllo Chart](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Aggiunta di controlli Chart in fase di progettazione
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart> al foglio di lavoro nello stesso modo in cui si aggiunge un grafico dall'interno dell'applicazione.

> [!NOTE]
> Il <xref:Microsoft.Office.Tools.Excel.Chart> controllo non è disponibile dalla **casella degli strumenti** o dalla finestra **origini dati** .

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Per aggiungere un controllo host Chart a un foglio di lavoro in Excel

1. Nel gruppo **grafici** della scheda **Inserisci** fare clic su **colonna**, fare clic su una categoria di grafici, quindi selezionare il tipo di grafico desiderato.

2. Nella finestra di dialogo **Inserisci grafico** fare clic su **OK**.

3. Nella scheda **progettazione** , nel gruppo **dati** , fare clic su **Seleziona dati**.

4. Nella finestra di dialogo **Seleziona origine dati** fare clic nella casella  **intervallo di dati** del grafico e deselezionare le selezioni predefinite.

5. Nel foglio **dati per il grafico** selezionare l'intervallo di celle contenente i dati per il grafico (celle da **a5** a **D8**).

6. Nella finestra di dialogo **Seleziona origine dati** fare clic su **OK**.

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Aggiungere controlli Chart in fase di esecuzione in un progetto a livello di documento
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart> in modo dinamico in fase di esecuzione I grafici creati dinamicamente non vengono salvati in modo permanente nel documento come controlli host quando il documento viene chiuso. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice

1. Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1` inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Aggiungere controlli Chart in fase di esecuzione in un progetto di componente aggiuntivo VSTO
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.Chart> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Per altre informazioni, vedere [estensione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)in fase di esecuzione.

 I controlli Chart creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene chiuso. Per altre informazioni, vedere [aggiungere controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice

1. Il codice seguente genera un elemento host foglio di lavoro basato sul foglio di lavoro aperto e quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.Chart>.

     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio prevede i requisiti seguenti:

- Dati da usare per creare il grafico, archiviati nell'intervallo da A5 a D8 nel foglio di lavoro.

## <a name="see-also"></a>Vedi anche
- [Estendi i documenti di Word e le cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Controllo Chart](../vsto/chart-control.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
