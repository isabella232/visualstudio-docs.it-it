---
title: 'Procedura: Eseguire calcoli di Excel a livello di codice'
description: Informazioni su come usare le Visual Studio per eseguire calcoli a livello di codice in una cartella Microsoft Excel lavoro.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 234457e235a78281858a45a202fdeff9ff781a849fef5a5757ad505f368cd023
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384236"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Procedura: Eseguire calcoli di Excel a livello di codice
  Si usa un processo simile per eseguire calcoli in un controllo o in un <xref:Microsoft.Office.Tools.Excel.NamedRange> oggetto intervallo Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Eseguire calcoli in un controllo NamedRange
 Nell'esempio seguente viene <xref:Microsoft.Office.Tools.Excel.NamedRange> creato un oggetto nella cella A1 e quindi viene calcolata la cella. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

### <a name="to-run-calculations-in-a-namedrange-control"></a>Per eseguire calcoli in un controllo NamedRange

1. Creare l'intervallo denominato.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet75":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet75":::

2. Chiamare il <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> metodo dell'intervallo specificato.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet76":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet76":::

## <a name="run-calculations-in-a-native-excel-range"></a>Eseguire calcoli in un intervallo di Excel nativo

### <a name="to-run-calculations-in-a-native-excel-range"></a>Per eseguire calcoli in un intervallo Excel nativo

1. Creare l'intervallo denominato.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet30":::

2. Chiamare il <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> metodo dell'intervallo specificato.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet31":::

## <a name="see-also"></a>Vedi anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
