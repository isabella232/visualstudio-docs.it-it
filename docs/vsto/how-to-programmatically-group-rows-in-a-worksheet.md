---
title: 'Procedura: Raggruppare righe in un foglio di lavoro a livello di codice'
description: Informazioni su come raggruppare a livello di codice una o più righe intere Microsoft Excel usando un controllo NamedRange o un oggetto intervallo Excel nativo.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 89d71b501dc7c9c65e2cf1d0d167b34233c30383
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147999"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Procedura: Raggruppare righe in un foglio di lavoro a livello di codice
  È possibile raggruppare una o più righe intere. Per creare un gruppo in un foglio di lavoro, usare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 Se si aggiunge un controllo a un progetto a livello di documento in fase di progettazione, è possibile usare il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> per creare un gruppo a livello di codice. Nell'esempio seguente si presuppone che nello stesso foglio di lavoro siano presenti tre <xref:Microsoft.Office.Tools.Excel.NamedRange> controlli: `data2001` , e `data2002` `dataAll` . Ogni intervallo denominato fa riferimento a un'intera riga nel foglio di lavoro.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Per creare un gruppo di controlli NamedRange in un foglio di lavoro

1. Raggruppare tre intervalli denominati chiamando <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> il metodo di ogni intervallo. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Per separare le righe, chiamare il <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> metodo .

## <a name="use-native-excel-ranges"></a>Usare intervalli Excel nativi
 Il codice presuppone che siano disponibili tre intervalli Excel denominati `data2001` , e in un foglio di `data2002` `dataAll` lavoro.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Per creare un gruppo di intervalli Excel in un foglio di lavoro

1. Raggruppare tre intervalli denominati chiamando <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> il metodo di ogni intervallo. Nell'esempio seguente si presuppone che nello stesso foglio di lavoro siano presenti tre controlli <xref:Microsoft.Office.Interop.Excel.Range> `data2001` denominati , e `data2002` `dataAll` . Ogni intervallo denominato fa riferimento a un'intera riga nel foglio di lavoro.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Per separare le righe, chiamare il <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> metodo .

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Procedura: Aggiungere controlli NamedRange ai fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
