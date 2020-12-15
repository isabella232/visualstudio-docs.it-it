---
title: Archiviare & recuperare i valori di data in intervalli di Excel a livello di codice
description: Informazioni su come usare Visual Studio per archiviare e recuperare i valori di data in intervalli di Microsoft Excel a livello di codice.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 673969e13b2f49b91416d730533be0f075813781
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523579"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Procedura: archiviare e recuperare valori di data in intervalli di Excel a livello di codice
  È possibile archiviare e recuperare i valori in un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o in un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Se si archivia un valore di data che rientra o dopo 1/1/1900 in un intervallo con gli strumenti di sviluppo di Office in Visual Studio, viene archiviato in formato di automazione OLE (OA). È necessario usare il <xref:System.DateTime.FromOADate%2A> metodo per recuperare il valore delle date di automazione OLE (OA). Se la data è precedente a 1/1/1900, viene archiviata come stringa.

> [!NOTE]
> Le date di Excel sono diverse dalle date di automazione OLE per i primi due mesi 1900. Esistono anche differenze se è selezionata l'opzione di **sistema data 1904** . Negli esempi di codice riportati di seguito non vengono affrontate queste differenze.

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange

- Questo esempio è per le personalizzazioni a livello di documento. Il codice seguente deve essere inserito in una classe foglio, non nella `ThisWorkbook` classe.

### <a name="to-store-a-date-value-in-a-named-range"></a>Per archiviare un valore di data in un intervallo denominato

1. Creare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. Impostare la data odierna come valore per `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Per recuperare un valore di data da un intervallo denominato

1. Recuperare il valore date da `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>Usa intervalli di Excel nativi

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Per archiviare un valore di data in un oggetto intervallo di Excel nativo

1. Creare un oggetto <xref:Microsoft.Office.Interop.Excel.Range> che rappresenta la cella **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. Impostare la data odierna come valore per `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Per recuperare un valore di data da un oggetto intervallo di Excel nativo

1. Recuperare il valore date da `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>Vedere anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Panoramica del modello a oggetti di Excel](../vsto/excel-object-model-overview.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Procedura: fare riferimento a intervalli di fogli di fogli di codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Procedura: aggiungere controlli NamedRange a fogli di foglio](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
