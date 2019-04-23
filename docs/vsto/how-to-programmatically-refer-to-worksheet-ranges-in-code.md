---
title: 'Procedura: A livello di codice fare riferimento agli intervalli del foglio di lavoro nel codice'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e82b884965c5c7362951c7d94199f90c93fbfc3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073696"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Procedura: A livello di codice fare riferimento agli intervalli del foglio di lavoro nel codice
  Un processo simile viene utilizzato per fare riferimento al contenuto di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 L'esempio seguente aggiunge un <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro e quindi aggiunge il testo alla cella nell'intervallo.

### <a name="to-refer-to-a-namedrange-control"></a>Per fare riferimento a un controllo NamedRange

1. Assegnare una stringa per il <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> proprietà del <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Usare gli intervalli di Excel nativi
 Nell'esempio seguente aggiunge un intervallo di Excel nativo a un foglio di lavoro e quindi aggiunge il testo alla cella nell'intervallo.

### <a name="to-refer-to-a-native-range-object"></a>Per fare riferimento a un oggetto intervallo nativo

1. Assegnare una stringa per il <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> proprietà dell'intervallo.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>Vedere anche
- [Lavorare con intervalli](../vsto/working-with-ranges.md)
- [Procedura: A livello di codice il controllo ortografico nei fogli di lavoro](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Procedura: A livello di programmazione applicare stili agli intervalli in cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: Compilare a livello di codice automaticamente gli intervalli con dati modificati in modo incrementale](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Procedura: A livello di codice cercare testo negli intervalli del foglio di lavoro](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
