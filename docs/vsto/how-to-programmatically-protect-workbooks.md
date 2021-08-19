---
title: 'Procedura: Proteggere le cartelle di lavoro a livello di codice'
description: Informazioni su come proteggere una cartella di lavoro Microsoft Excel in modo che gli utenti non possano aggiungere o eliminare fogli di lavoro e rimuovere la protezione della cartella di lavoro a livello di codice.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 41875cb3be9ee49d696991c1eb4bc33605123cd2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092215"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Procedura: Proteggere le cartelle di lavoro a livello di codice
  È possibile proteggere una cartella di Microsoft Office Excel in modo che gli utenti non possano aggiungere o eliminare fogli di lavoro e rimuovere la protezione della cartella di lavoro a livello di codice. Facoltativamente, è possibile specificare una password, indicare se si vuole proteggere la struttura (in modo che gli utenti non possano spostare i fogli) e indicare se si vuole proteggere le finestre della cartella di lavoro.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 La protezione di una cartella di lavoro non consente agli utenti di modificare le celle. Per proteggere i dati, è necessario proteggere i fogli di lavoro. Per altre informazioni, vedere [Procedura: Proteggere i fogli di](../vsto/how-to-programmatically-protect-worksheets.md)lavoro a livello di codice.

 Negli esempi di codice seguenti viene utilizzata una variabile per contenere una password ottenuta dall'utente.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Proteggere una cartella di lavoro che fa parte di una personalizzazione a livello di documento

### <a name="to-protect-a-workbook"></a>Per proteggere una cartella di lavoro

1. Chiamare il <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metodo della cartella di lavoro e includere una password. Per usare l'esempio di codice seguente, eseguirlo nella `ThisWorkbook` classe , non in una classe foglio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet10":::

### <a name="to-unprotect-a-workbook"></a>Per rimuovere la protezione di una cartella di lavoro

1. Chiamare il <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> metodo , passando una password, se necessaria. Per usare l'esempio di codice seguente, eseguirlo nella `ThisWorkbook` classe , non in una classe foglio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet11":::

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Proteggere una cartella di lavoro usando un componente aggiuntivo a livello di applicazione

### <a name="to-protect-a-workbook"></a>Per proteggere una cartella di lavoro

1. Chiamare il <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> metodo della cartella di lavoro e includere una password. In questo esempio di codice viene utilizzata la cartella di lavoro attiva. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet6":::

### <a name="to-unprotect-a-workbook"></a>Per rimuovere la protezione di una cartella di lavoro

1. Chiamare il <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> metodo della cartella di lavoro attiva, passando una password, se necessaria. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Vedi anche
- [Usare le cartelle di lavoro](../vsto/working-with-workbooks.md)
- [Procedura: Proteggere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)
- [Procedura: Nascondere fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
