---
title: 'Procedura: A livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc23a3d0dfc18a9271db80df2cb1a42677b8ed5e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643691"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Procedura: A livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro
  È possibile creare un foglio di lavoro a livello di codice, quindi aggiungerlo alla raccolta di fogli di lavoro nella cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Per aggiungere un nuovo foglio di lavoro a una cartella di lavoro in una personalizzazione a livello di documento

1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> .

     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]

     Il nuovo foglio di lavoro è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo e non un elemento host. Per aggiungere un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> , aggiungere il foglio di lavoro in fase di progettazione.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Per aggiungere un nuovo foglio di lavoro a una cartella di lavoro in un componente aggiuntivo VSTO

1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]

     Il nuovo foglio di lavoro è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo e non un elemento host. È anche possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> dall'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)
- [Procedura: A livello di codice eliminare fogli di lavoro dalle cartelle di lavoro](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Procedura: A livello di codice selezionare fogli di lavoro](../vsto/how-to-programmatically-select-worksheets.md)
- [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
