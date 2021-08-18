---
title: 'Procedura: Ordinare i dati nei fogli di lavoro a livello di codice'
description: Informazioni su come usare le Visual Studio per ordinare a livello di codice i dati contenuti negli intervalli e negli elenchi dei fogli di lavoro in fase di esecuzione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 073ad50f3bc5bc135e6fd7f22afcbaac721f8d99e08c8862816672387c111b32
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440682"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Procedura: Ordinare i dati nei fogli di lavoro a livello di codice
  È possibile ordinare i dati contenuti negli elenchi e negli intervalli del foglio di lavoro in fase di esecuzione. Il codice seguente ordina un intervallo a più colonne denominato `Fruits` in base ai dati nella prima colonna e quindi ai dati nella seconda colonna.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Ordinare i dati in una personalizzazione a livello di documento

### <a name="to-sort-data-in-a-namedrange-control"></a>Per ordinare i dati in un controllo NamedRange

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>. L'esempio seguente richiede un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `Fruits` in un foglio di lavoro. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet78":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet78":::

   Inserire il codice seguente in *Sheet1.vb o* *Sheet1.cs* per ordinare i dati in un <xref:Microsoft.Office.Tools.Excel.ListObject> controllo . Il codice presuppone l'esistenza di un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `fruitList` in un foglio di lavoro denominato `Sheet1`.

### <a name="to-sort-data-in-a-listobject-control"></a>Per ordinare i dati in un controllo ListObject

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> della proprietà <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> del controllo host <xref:Microsoft.Office.Tools.Excel.ListObject>.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet79":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet79":::

## <a name="sort-data-in-a-vsto-add-in"></a>Ordinare i dati VSTO componente aggiuntivo

### <a name="to-sort-data-in-a-native-range"></a>Per ordinare i dati in un intervallo nativo

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> del controllo Excel nativo <xref:Microsoft.Office.Interop.Excel.Range>. L'esempio seguente richiede un controllo Excel nativo denominato `Fruits` in un foglio di lavoro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet23":::

### <a name="to-sort-data-in-a-listobject-control"></a>Per ordinare i dati in un controllo ListObject

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> della proprietà <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> del controllo Excel nativo <xref:Microsoft.Office.Interop.Excel.ListObject>. L'esempio seguente presuppone l'esistenza di un controllo Excel nativo <xref:Microsoft.Office.Interop.Excel.ListObject> denominato `fruitList` nel foglio di lavoro attivo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet24":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Riempire automaticamente gli intervalli con dati che cambiano in modo incrementale](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Procedura: Fare riferimento a intervalli di fogli di lavoro nel codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Procedura: Applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Controllo ListObject](../vsto/listobject-control.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
