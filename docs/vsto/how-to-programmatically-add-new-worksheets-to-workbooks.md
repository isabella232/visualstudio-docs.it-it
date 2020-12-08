---
title: 'Procedura: aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice'
description: Informazioni su come creare un foglio di lavoro a livello di codice e quindi aggiungere il foglio di lavoro alla raccolta di fogli di lavoro nella cartella di lavoro.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 3397b2ad8f656a7ada82ce0be17dcf21064d0ee3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96843984"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Procedura: aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice
  È possibile creare un foglio di lavoro a livello di codice, quindi aggiungerlo alla raccolta di fogli di lavoro nella cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Per aggiungere un nuovo foglio di lavoro a una cartella di lavoro in una personalizzazione a livello di documento

1. Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> .

     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]

     Il nuovo foglio di lavoro è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo e non un elemento host. Per aggiungere un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> , aggiungere il foglio di lavoro in fase di progettazione.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Per aggiungere un nuovo foglio di lavoro a una cartella di lavoro in un componente aggiuntivo VSTO

1. Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]

     Il nuovo foglio di lavoro è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo e non un elemento host. È anche possibile generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> dall'oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo. Per altre informazioni, vedere [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Vedi anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Procedura: eliminare fogli di lavoro dalle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Procedura: selezionare fogli di programmazione a livello di codice](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
