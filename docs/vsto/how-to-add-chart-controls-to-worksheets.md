---
title: 'Procedura: Aggiungere controlli Chart ai fogli di lavoro'
description: Informazioni su come aggiungere controlli Chart a un foglio Microsoft Office Excel in fase di progettazione e in fase di esecuzione nelle personalizzazioni a livello di documento.
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
ms.openlocfilehash: 88ebe38a881e148f10149189a2d27ac81bd0ddc2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827032"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Procedura: Aggiungere controlli Chart ai fogli di lavoro
  È possibile aggiungere controlli a un foglio Microsoft Office Excel in fase di progettazione e in fase di <xref:Microsoft.Office.Tools.Excel.Chart> esecuzione nelle personalizzazioni a livello di documento. È anche possibile aggiungere <xref:Microsoft.Office.Tools.Excel.Chart> controlli in fase di esecuzione nei componenti aggiuntivi VSTO.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Questo argomento descrive le attività seguenti:

- [Aggiungere controlli Chart in fase di progettazione](#designtime)

- [Aggiungere controlli Chart in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Aggiungere controlli Chart in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)

  Per altre informazioni sui <xref:Microsoft.Office.Tools.Excel.Chart> controlli, vedere [Controllo Chart](../vsto/chart-control.md).

## <a name="add-chart-controls-at-design-time"></a><a name="designtime"></a> Aggiungere controlli Chart in fase di progettazione
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart> al foglio di lavoro nello stesso modo in cui si aggiunge un grafico dall'interno dell'applicazione.

> [!NOTE]
> Il <xref:Microsoft.Office.Tools.Excel.Chart> controllo non è disponibile dalla casella degli **strumenti** o dalla **finestra Origini** dati.

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Per aggiungere un controllo host Chart a un foglio di lavoro in Excel

1. Nel gruppo **Grafici** della  scheda Inserisci fare clic su **Colonna,** selezionare una categoria di grafici e quindi fare clic sul tipo di grafico desiderato.

2. Nella finestra **di dialogo** Inserisci grafico fare clic su **OK**.

3. Nel gruppo **Dati** della scheda Progettazione **fare** clic su **Seleziona dati**.

4. Nella finestra **di dialogo Seleziona origine** dati fare clic nella casella **Intervallo** **dati grafico** e deselezionare qualsiasi selezione predefinita.

5. Nel foglio **Dati per grafico** selezionare l'intervallo di celle che contiene i dati per il grafico (celle da **A5** a **D8).**

6. Nella finestra **di dialogo Seleziona origine** dati fare clic su **OK**.

## <a name="add-chart-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Aggiungere controlli grafico in fase di esecuzione in un progetto a livello di documento
 È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart> in modo dinamico in fase di esecuzione I grafici creati dinamicamente non vengono salvati in modo permanente nel documento come controlli host quando il documento viene chiuso. Per altre informazioni, vedere [Aggiungere controlli ai documenti di Office in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice

1. Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> di `Sheet1` inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.Chart>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet1":::

## <a name="add-chart-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Aggiungere controlli grafico in fase di esecuzione in un progetto di componente aggiuntivo VSTO
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.Chart> a livello di codice a qualsiasi foglio di lavoro aperto in un progetto di componente aggiuntivo VSTO. Per altre informazioni, vedere Estendere documenti di Word e cartelle di lavoro [di Excel nei componenti aggiuntivi VSTO in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

 I controlli Chart creati dinamicamente non vengono salvati in modo permanente nel foglio di lavoro come controlli host quando il foglio di lavoro viene chiuso. Per altre informazioni, vedere [Aggiungere controlli ai documenti di Office in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Per aggiungere un controllo Chart a un foglio di lavoro a livello di codice

1. Il codice seguente genera un elemento host foglio di lavoro basato sul foglio di lavoro aperto e quindi aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.Chart>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet9":::

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio prevede i requisiti seguenti:

- Dati da usare per creare il grafico, archiviati nell'intervallo da A5 a D8 nel foglio di lavoro.

## <a name="see-also"></a>Vedi anche
- [Estendere documenti di Word e cartelle di lavoro di Excel nei componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Controllo Grafico](../vsto/chart-control.md)
- [Automatizzare Excel tramite oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
