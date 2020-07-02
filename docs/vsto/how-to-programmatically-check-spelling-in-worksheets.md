---
title: 'Procedura: eseguire il controllo ortografico nei fogli di codice a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 797fc498c54bdbc466fe8ddc35229b2c106db80d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541544"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Procedura: eseguire il controllo ortografico nei fogli di codice a livello di codice
  A livello di codice è possibile eseguire il controllo ortografico delle parole in un foglio di lavoro. La finestra di dialogo **Controllo ortografia** viene visualizzata automaticamente se si sono parole formulate in modo non corretto nel foglio di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Per controllare l'ortografia in un foglio di lavoro in una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> del foglio di lavoro.

     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Per controllare l'ortografia in un foglio di controllo in un componente aggiuntivo VSTO

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> del foglio di lavoro attivo.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: eseguire calcoli di Excel a livello di codice](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange (controllo)](../vsto/namedrange-control.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
