---
title: Archiviare & valori di data negli intervalli di Excel a livello di codice
description: Informazioni su come usare le Visual Studio per archiviare e recuperare i valori di data negli intervalli di Microsoft Excel a livello di codice.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e3115e00147a5dff850f6e0c051ffc3b6733218
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826239"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Procedura: Archiviare e recuperare valori di data in intervalli di Excel a livello di codice
  È possibile archiviare e recuperare valori in un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o in un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Se si archivia un valore di data che rientra in o dopo l'1/1/1900 in un intervallo che usa gli strumenti di sviluppo di Office in Visual Studio, viene archiviato in formato Automazione OLE (OA). È necessario utilizzare il <xref:System.DateTime.FromOADate%2A> metodo per recuperare il valore delle date di automazione OLE(OA). Se la data è precedente a 1/1/1900, viene archiviata come stringa.

> [!NOTE]
> Le date di Excel differiscono dalle date di automazione OLE per i primi due mesi del 1900. Esistono anche differenze se è selezionata **l'opzione di sistema data 1904.** Gli esempi di codice seguenti non affrontano queste differenze.

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange

- Questo esempio è per le personalizzazioni a livello di documento. Il codice seguente deve essere inserito in una classe foglio, non nella `ThisWorkbook` classe .

### <a name="to-store-a-date-value-in-a-named-range"></a>Per archiviare un valore di data in un intervallo denominato

1. Creare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella **A1.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. Impostare la data odierna come valore per `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Per recuperare un valore di data da un intervallo denominato

1. Recuperare il valore della data da `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>Usare intervalli nativi di Excel

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Per archiviare un valore di data in un oggetto intervallo di Excel nativo

1. Creare un <xref:Microsoft.Office.Interop.Excel.Range> oggetto che rappresenta la cella **A1.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. Impostare la data odierna come valore per `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Per recuperare un valore di data da un oggetto intervallo di Excel nativo

1. Recuperare il valore della data da `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>Vedi anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Panoramica del modello a oggetti di Excel](../vsto/excel-object-model-overview.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Procedura: Aggiungere controlli NamedRange ai fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
