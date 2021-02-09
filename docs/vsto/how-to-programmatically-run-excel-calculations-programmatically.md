---
title: 'Procedura: eseguire calcoli di Excel a livello di codice'
description: Informazioni su come usare Visual Studio per eseguire calcoli a livello di codice in una cartella di lavoro di Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 761f58027171ccaa667aa26569e41c3b4a8b75a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880476"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Procedura: eseguire calcoli di Excel a livello di codice
  Si usa un processo simile per eseguire calcoli in un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o in un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Eseguire calcoli in un controllo NamedRange
 Nell'esempio seguente viene creato un oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> nella cella a1, quindi viene calcolata la cella. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

### <a name="to-run-calculations-in-a-namedrange-control"></a>Per eseguire calcoli in un controllo NamedRange

1. Creare l'intervallo denominato.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. Chiamare il <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> metodo dell'intervallo specificato.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Eseguire calcoli in un intervallo di Excel nativo

### <a name="to-run-calculations-in-a-native-excel-range"></a>Per eseguire calcoli in un intervallo di Excel nativo

1. Creare l'intervallo denominato.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. Chiamare il <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> metodo dell'intervallo specificato.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Vedi anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
