---
title: 'Procedura: raggruppare righe in un foglio di codice a livello di codice'
description: Informazioni su come è possibile raggruppare a livello di codice una o più righe intere in Microsoft Excel usando un controllo NamedRange o un oggetto intervallo Excel nativo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eaa0bbcc2c26a36e43e862cbe5a8f117c2a1fb26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885417"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Procedura: raggruppare righe in un foglio di codice a livello di codice
  È possibile raggruppare una o più righe intere. Per creare un gruppo in un foglio di lavoro, usare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 Se si aggiunge un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo a un progetto a livello di documento in fase di progettazione, è possibile utilizzare il controllo per creare un gruppo a livello di codice. Nell'esempio seguente si presuppone che siano presenti tre <xref:Microsoft.Office.Tools.Excel.NamedRange> controlli nello stesso foglio di tempo: `data2001` , `data2002` e `dataAll` . Ogni intervallo denominato si riferisce a una riga intera del foglio di file.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Per creare un gruppo di controlli NamedRange in un foglio di foglio

1. Raggruppare tre intervalli denominati chiamando il <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> metodo di ogni intervallo. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Per raggruppare le righe, chiamare il <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> metodo.

## <a name="use-native-excel-ranges"></a>Usa intervalli di Excel nativi
 Il codice presuppone che siano disponibili tre intervalli di Excel denominati `data2001` , `data2002` e `dataAll` in un foglio di lavoro.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Per creare un gruppo di intervalli di Excel in un foglio di lavoro

1. Raggruppare tre intervalli denominati chiamando il <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> metodo di ogni intervallo. Nell'esempio seguente si presuppone che esistano tre <xref:Microsoft.Office.Interop.Excel.Range> controlli denominati `data2001` , `data2002` e nello `dataAll` stesso foglio di foglio. Ogni intervallo denominato si riferisce a una riga intera del foglio di file.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Per raggruppare le righe, chiamare il <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> metodo.

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Procedura: aggiungere controlli NamedRange a fogli di foglio](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
