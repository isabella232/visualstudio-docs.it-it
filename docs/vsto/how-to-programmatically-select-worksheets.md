---
title: 'Procedura: Selezionare i fogli di foglio a livello di codice'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20ebc8fea14b3dc52c802543f97318ec7fae7529
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255625"
---
# <a name="how-to-programmatically-select-worksheets"></a>Procedura: Selezionare i fogli di foglio a livello di codice
  Il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> seleziona l'oggetto specificato e questa operazione sposta la selezione dell'utente al nuovo oggetto. Usare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> se si vuole applicare lo stato attivo all'oggetto senza modificare la selezione dell'utente.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Se si vuole selezionare un foglio di lavoro esistente in un componente aggiuntivo VSTO o se il foglio di lavoro è stato creato in fase di esecuzione in una personalizzazione a livello di documento, è necessario accedervi usando la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Excel della cartella di lavoro di Excel, altrimenti è possibile accedere direttamente all'elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>.

## <a name="use-the-worksheet-host-item"></a>Usare l'elemento host Worksheet
 In una personalizzazione a livello di documento aggiungere il codice seguente a *Sheet1. vb* o *Sheet1.cs*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Per selezionare il primo foglio di lavoro in una cartella di lavoro usando un elemento host

1. Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> di `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usare la raccolta Sheets della cartella di lavoro di Excel
 Accedere al foglio di lavoro usando la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Excel.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Per selezionare il primo foglio di lavoro in una cartella di lavoro usando la raccolta Sheets della cartella di lavoro di Excel

1. Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> della Collection <xref:Microsoft.Office.Interop.Excel.Sheets> per selezionare il primo foglio di lavoro della cartella di lavoro attiva.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: Stampa di fogli di codice a livello di codice](../vsto/how-to-programmatically-print-worksheets.md)
- [Procedura: Eliminare i fogli di lavoro a livello di codice dalle cartelle di lavoro](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Procedura: Nascondi i fogli di foglio di programmazione a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Procedura: Proteggi i fogli di foglio a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)
- [Elemento host Worksheet](../vsto/worksheet-host-item.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
