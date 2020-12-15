---
title: 'Procedura: stampa di fogli di codice a livello di codice'
description: Informazioni su come usare Visual Studio per stampare a livello di codice qualsiasi foglio di lavoro in una cartella di lavoro di Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 356c47ec3275c1442082f367dd08fe6901f9c0a3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523767"
---
# <a name="how-to-programmatically-print-worksheets"></a>Procedura: stampa di fogli di codice a livello di codice

È possibile stampare qualsiasi foglio di lavoro da una cartella di lavoro.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Stampare un foglio di testo in una personalizzazione a livello di documento

### <a name="to-print-a-worksheet"></a>Per stampare un foglio di lavoro

1. Chiamare il metodo `PrintOut` di `Sheet1`, richiedere due copie e visualizzare l'anteprima del documento prima della stampa.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   Il <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metodo consente di visualizzare l'oggetto specificato nella finestra di **Anteprima di stampa** . Il codice seguente presuppone l'esistenza di un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> denominato `Sheet1`.

### <a name="to-preview-a-page-before-printing"></a>Per visualizzare l'anteprima di una pagina prima della stampa

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> del foglio di lavoro.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Stampare un foglio di un foglio di un componente aggiuntivo VSTO

### <a name="to-print-a-worksheet"></a>Per stampare un foglio di lavoro

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> del foglio di lavoro attivo, richiedere due copie e visualizzare l'anteprima del documento prima della stampa.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   Il <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodo consente di visualizzare l'oggetto specificato nella finestra di **Anteprima di stampa** .

### <a name="to-preview-a-page-before-printing"></a>Per visualizzare l'anteprima di una pagina prima della stampa

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> del foglio di lavoro attivo.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Vedere anche

- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: eseguire il controllo ortografico nei fogli di codice a livello di codice](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Elemento host Worksheet](../vsto/worksheet-host-item.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
