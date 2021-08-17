---
title: 'Procedura: Stampare fogli di lavoro a livello di codice'
description: Informazioni su come usare Visual Studio per stampare a livello di codice qualsiasi foglio di lavoro in una Microsoft Excel cartella di lavoro.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9671e678c28523bf3ab0aaeb443845b795f7b208b9db5db459afcd2692a08e7d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440734"
---
# <a name="how-to-programmatically-print-worksheets"></a>Procedura: Stampare fogli di lavoro a livello di codice

È possibile stampare qualsiasi foglio di lavoro da una cartella di lavoro.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Stampare un foglio di lavoro in una personalizzazione a livello di documento

### <a name="to-print-a-worksheet"></a>Per stampare un foglio di lavoro

1. Chiamare il metodo `PrintOut` di `Sheet1`, richiedere due copie e visualizzare l'anteprima del documento prima della stampa.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet22":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet22":::

   Il <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metodo consente di visualizzare l'oggetto specificato nella finestra Anteprima **di** stampa. Il codice seguente presuppone l'esistenza di un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> denominato `Sheet1`.

### <a name="to-preview-a-page-before-printing"></a>Per visualizzare l'anteprima di una pagina prima della stampa

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> del foglio di lavoro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet23":::

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Stampare un foglio di lavoro in VSTO componente aggiuntivo

### <a name="to-print-a-worksheet"></a>Per stampare un foglio di lavoro

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> del foglio di lavoro attivo, richiedere due copie e visualizzare l'anteprima del documento prima della stampa.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet14":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet14":::

   Il <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodo consente di visualizzare l'oggetto specificato nella finestra Anteprima **di** stampa.

### <a name="to-preview-a-page-before-printing"></a>Per visualizzare l'anteprima di una pagina prima della stampa

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> del foglio di lavoro attivo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Vedi anche

- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Eseguire il controllo ortografico nei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Elemento host foglio di lavoro](../vsto/worksheet-host-item.md)
- [Accesso globale agli oggetti nei progetti Office globali](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
