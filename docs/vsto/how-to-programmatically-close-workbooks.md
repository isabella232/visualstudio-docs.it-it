---
title: 'Procedura: A livello di programmazione chiudere cartelle di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 187baa6805050507e8f824593a5b1b4f02666c46
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864891"
---
# <a name="how-to-programmatically-close-workbooks"></a>Procedura: A livello di programmazione chiudere cartelle di lavoro
  È possibile chiudere la cartella di lavoro attiva o specificare una cartella di lavoro da chiudere.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="close-the-active-workbook"></a>Chiudere la cartella di lavoro attiva  
 Esistono due procedure per chiudere la cartella di lavoro attiva: una per le personalizzazioni a livello di documento e una per i componenti aggiuntivi VSTO.  
  
### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Per chiudere la cartella di lavoro attiva in una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> per chiudere la cartella di lavoro associata alla personalizzazione. Per usare l'esempio di codice seguente, eseguirlo nella classe `Sheet1` in un progetto a livello di documento per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]  
  
### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Per chiudere la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> per chiudere la cartella di lavoro attiva. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="close-a-workbook-that-you-specify-by-name"></a>Chiudere una cartella di lavoro specificata in base al nome  
 Il modo in cui viene chiusa una cartella di lavoro specificata in base al nome è identico per i componenti aggiuntivi VSTO e per le personalizzazioni a livello di documento.  
  
### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Per chiudere una cartella di lavoro attiva specificata in base al nome  
  
1.  Specificare il nome della cartella di lavoro come argomento per la raccolta <xref:Microsoft.Office.Interop.Excel.Workbooks> . L'esempio di codice seguente presuppone l'apertura in Excel di una cartella di lavoro il cui nome è **NewWorkbook** .  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="see-also"></a>Vedere anche  
 [Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: A livello di programmazione salvare cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md)   
 [Procedura: A livello di codice aprire cartelle di lavoro](../vsto/how-to-programmatically-open-workbooks.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)  
