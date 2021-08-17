---
title: 'Procedura: Eseguire il controllo ortografico nei fogli di lavoro a livello di codice'
description: Informazioni su come controllare a livello di codice l'ortografia delle parole in un foglio Microsoft Excel foglio di lavoro.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d45cafb20c1d021a893b5b650dff938f9ff5927e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026213"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Procedura: Eseguire il controllo ortografico nei fogli di lavoro a livello di codice
  A livello di codice è possibile eseguire il controllo ortografico delle parole in un foglio di lavoro. La finestra di dialogo **Controllo ortografia** viene visualizzata automaticamente se si sono parole formulate in modo non corretto nel foglio di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Per controllare l'ortografia in un foglio di lavoro in una personalizzazione a livello di documento

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> del foglio di lavoro.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet45":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet45":::

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Per controllare l'ortografia in un foglio di lavoro in VSTO componente aggiuntivo

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> del foglio di lavoro attivo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet22":::

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Eseguire calcoli Excel a livello di codice](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Controllo NamedRange](../vsto/namedrange-control.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
