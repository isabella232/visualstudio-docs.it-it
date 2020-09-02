---
title: 'Procedura: nascondere i fogli di programmazione a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83cf1f63a67525dca4cf9dbb5a4916da5d70b4ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547407"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Procedura: nascondere i fogli di programmazione a livello di codice
  È possibile mostrare o nascondere qualsiasi foglio di lavoro da una cartella di lavoro. Per nascondere un foglio di lavoro, usare l'elemento host Worksheet o accedere al foglio di lavoro usando la raccolta Sheets della cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Usare l'elemento host Worksheet
 Se il foglio di lavoro è stato aggiunto in fase di progettazione in una personalizzazione a livello di documento, per nasconderlo usare la proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> .

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Per nascondere un foglio di lavoro usando un elemento host Worksheet

1. Impostare la proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> dell'elemento host `Sheet1` sul valore di enumerazione <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usare la raccolta Sheets della cartella di lavoro di Excel
 Accedere ai fogli di lavoro mediante la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Microsoft Office Excel nei casi seguenti:

- Si vuole nascondere un foglio di un foglio di un componente aggiuntivo VSTO.

- Se il foglio di lavoro che si vuole nascondere è stato creato in fase di esecuzione in una personalizzazione a livello di documento

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Per nascondere un foglio di lavoro usando la raccolta Sheets della cartella di lavoro di Excel

1. Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> del foglio di lavoro sul valore di enumerazione <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .

     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: eliminare fogli di lavoro dalle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Procedura: spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Procedura: proteggere i fogli di fogli di un foglio di codice](../vsto/how-to-programmatically-protect-worksheets.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)
