---
title: 'Procedura: fare riferimento a intervalli di fogli di fogli di codice a livello di codice'
description: Informazioni su come usare Visual Studio per fare riferimento a livello di codice al contenuto di un controllo NamedRange o a un oggetto intervallo di Excel nativo in un foglio di lavoro di Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 9756123038de33e8f8e69bd9a824822c26e2dc00
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526670"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Procedura: fare riferimento a intervalli di fogli di fogli di codice a livello di codice
  Si usa un processo simile per fare riferimento al contenuto di un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o di un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 Nell'esempio seguente viene aggiunto un oggetto <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di testo, quindi viene aggiunto il testo alla cella nell'intervallo.

### <a name="to-refer-to-a-namedrange-control"></a>Per fare riferimento a un controllo NamedRange

1. Assegnare una stringa alla <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> proprietà del <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Usa intervalli di Excel nativi
 Nell'esempio seguente viene aggiunto un intervallo di Excel nativo a un foglio di lavoro e quindi viene aggiunto il testo alla cella nell'intervallo.

### <a name="to-refer-to-a-native-range-object"></a>Per fare riferimento a un oggetto intervallo nativo

1. Assegnare una stringa alla <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> proprietà dell'intervallo.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>Vedere anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Procedura: eseguire il controllo ortografico nei fogli di codice a livello di codice](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Procedura: applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: riempire automaticamente gli intervalli con dati modificati in modo incrementale a livello di codice](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Procedura: ricerca di testo negli intervalli dei fogli di testo a livello di codice](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
