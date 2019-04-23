---
title: 'Procedura: Applicare il colore a intervalli di Excel a livello di codice'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 56ecbfcdaf22132f63df1ecf5eadba97dee426af
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078083"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Procedura: Applicare il colore a intervalli di Excel a livello di codice
  Per applicare un colore di testo all'interno di un intervallo di celle, usare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo o un oggetto intervallo di Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usare un controllo NamedRange
 Questo esempio è per le personalizzazioni a livello di documento.

### <a name="to-apply-color-to-a-namedrange-control"></a>Per applicare il colore a un controllo NamedRange

1. Creare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo nella cella A1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Impostare il colore del testo di <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Usare gli intervalli di Excel nativi

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Per applicare colore in un oggetto intervallo di Excel nativo

1. Creare un intervallo nella cella A1 e quindi impostare il colore del testo.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Vedere anche
- [Lavorare con intervalli](../vsto/working-with-ranges.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Procedura: A livello di programmazione applicare stili agli intervalli in cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: A livello di codice fare riferimento agli intervalli del foglio di lavoro nel codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
