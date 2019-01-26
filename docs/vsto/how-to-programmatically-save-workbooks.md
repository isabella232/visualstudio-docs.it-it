---
title: 'Procedura: A livello di programmazione salvare cartelle di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bcc0869b8d255ba91e1a1fd017c93cdb24346b27
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874549"
---
# <a name="how-to-programmatically-save-workbooks"></a>Procedura: A livello di programmazione salvare cartelle di lavoro
  Una cartella di lavoro può essere salvata in più modi, ad esempio senza modificare il percorso. Se si tratta del primo salvataggio della cartella di lavoro, è necessario specificare un percorso. Se non viene specificato un percorso esplicito, Microsoft Office Excel salva il file nella cartella corrente con il nome assegnato al momento della creazione. È anche possibile salvare una copia della cartella di lavoro senza modificare la cartella di lavoro aperta in memoria.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="save-a-workbook-without-changing-the-path"></a>Salvare una cartella di lavoro senza modificare il percorso  
  
### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Per salvare una cartella di lavoro associata a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> della classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]  
  
### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Per salvare la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> per salvare la cartella di lavoro attiva. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="save-a-workbook-with-a-new-path"></a>Salvare una cartella di lavoro con un nuovo percorso  
 È possibile salvare la cartella di lavoro specificata in un nuovo percorso o con un nuovo nome, specificando eventualmente un formato di file, una password, una modalità di accesso e altre opzioni.  
  
> [!NOTE]  
>  È possibile impostare il <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> proprietà **False** prima di salvare la cartella di lavoro con un nuovo percorso poiché per il salvataggio in alcuni formati necessaria l'interazione. Impostando questa proprietà su **False** , in Excel usare tutti i valori predefiniti.  
  
### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Per salvare una cartella di lavoro associata a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> della classe `ThisWorkbook` . Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]  
  
### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Per salvare la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> per salvare la cartella di lavoro attiva in un nuovo percorso. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="save-a-copy-of-the-workbook"></a>Salvare una copia della cartella di lavoro  
 È possibile salvare una copia della cartella di lavoro in un file senza modificare la cartella di lavoro aperta in memoria. Questa operazione è utile per creare una copia di backup senza modificare il percorso della cartella di lavoro.  
  
### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Per salvare una cartella di lavoro associata a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> della classe `ThisWorkbook` . Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]  
  
### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Per salvare la cartella di lavoro attiva in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> per salvare una copia della cartella di lavoro attiva. Per usare l'esempio di codice seguente, eseguirlo nella classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Se si annulla in modo interattivo uno dei metodi usati per salvare o copiare la cartella di lavoro, viene generato un errore di run-time nel codice. Ad esempio, se la routine chiama il <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metodo ma non non disabilitati i prompt da Excel, e l'utente fa clic su **annullare** quando richiesto, Excel genera un errore di run-time.  
  
## <a name="see-also"></a>Vedere anche  
 [Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Procedura: A livello di programmazione chiudere cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)  
