---
title: 'Procedura: proteggere cartelle di lavoro a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee7444c63c2d774e9b22ea612049f09429729c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537631"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Procedura: proteggere cartelle di lavoro a livello di codice
  È possibile proteggere una cartella di lavoro di Excel Microsoft Office in modo che gli utenti non possano aggiungere o eliminare fogli di lavoro e anche rimuovere la protezione della cartella di lavoro a livello di codice. Facoltativamente, è possibile specificare una password, indicare se si desidera che la struttura sia protetta (in modo che gli utenti non possano spostare i fogli) e indicare se si desidera proteggere le finestre della cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 La protezione di una cartella di lavoro non impedisce agli utenti di modificare le celle. Per proteggere i dati, è necessario proteggere i fogli di dati. Per altre informazioni, vedere [procedura: proteggere fogli di dati a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md).

 Negli esempi di codice seguenti viene utilizzata una variabile per contenere una password ottenuta dall'utente.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Proteggere una cartella di lavoro che fa parte di una personalizzazione a livello di documento

### <a name="to-protect-a-workbook"></a>Per proteggere una cartella di lavoro

1. Chiamare il <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metodo della cartella di lavoro e includere una password. Per usare l'esempio di codice seguente, eseguirlo nella `ThisWorkbook` classe e non in una classe Sheet.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>Per rimuovere la protezione di una cartella di lavoro

1. Chiamare il <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> metodo, passando una password, se necessario. Per usare l'esempio di codice seguente, eseguirlo nella `ThisWorkbook` classe e non in una classe Sheet.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Proteggere una cartella di lavoro tramite un componente aggiuntivo a livello di applicazione

### <a name="to-protect-a-workbook"></a>Per proteggere una cartella di lavoro

1. Chiamare il <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> metodo della cartella di lavoro e includere una password. In questo esempio di codice viene utilizzata la cartella di lavoro attiva. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>Per rimuovere la protezione di una cartella di lavoro

1. Chiamare il <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> metodo della cartella di lavoro attiva, passando una password, se necessario. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Vedere anche
- [Utilizzare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: proteggere i fogli di fogli di un foglio di codice](../vsto/how-to-programmatically-protect-worksheets.md)
- [Procedura: nascondere i fogli di programmazione a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
