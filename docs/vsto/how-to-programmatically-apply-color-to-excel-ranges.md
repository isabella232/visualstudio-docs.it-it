---
title: 'Procedura: applicare il colore a intervalli di Excel a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d4a99e2e71e6a87b304ceea45a3cd595f911ff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543455"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Procedura: applicare il colore a intervalli di Excel a livello di codice
  Per applicare un colore al testo all'interno di un intervallo di celle, utilizzare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 Questo esempio è per le personalizzazioni a livello di documento.

### <a name="to-apply-color-to-a-namedrange-control"></a>Per applicare il colore a un controllo NamedRange

1. Creare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella a1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Imposta il colore del testo nel <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Usa intervalli di Excel nativi

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Per applicare il colore a un oggetto intervallo di Excel nativo

1. Creare un intervallo alla cella a1 e quindi impostare il colore del testo.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Vedere anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Procedura: applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: fare riferimento a intervalli di fogli di fogli di codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
