---
title: 'Procedura: a livello di codice selezionare fogli di lavoro'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09e477d802b9d92ca4f9e1cd3a532145ad0e68a0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673775"
---
# <a name="how-to-programmatically-select-worksheets"></a>Procedura: a livello di codice selezionare fogli di lavoro
  Il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> seleziona l'oggetto specificato e questa operazione sposta la selezione dell'utente al nuovo oggetto. Usare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> se si vuole applicare lo stato attivo all'oggetto senza modificare la selezione dell'utente.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Se si vuole selezionare un foglio di lavoro esistente in un componente aggiuntivo VSTO o se il foglio di lavoro è stato creato in fase di esecuzione in una personalizzazione a livello di documento, è necessario accedervi tramite Excel <xref:Microsoft.Office.Interop.Excel.Sheets> raccolta della cartella di lavoro di Excel; in caso contrario, è possibile accedere la <xref:Microsoft.Office.Tools.Excel.Worksheet>direttamente all'elemento host.  
  
## <a name="use-the-worksheet-host-item"></a>Usare l'elemento host foglio di lavoro  
 In una personalizzazione a livello di documento, aggiungere il codice seguente al *Sheet1.vb* oppure *Sheet1.cs*.  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Per selezionare il primo foglio di lavoro in una cartella di lavoro usando un elemento host  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> di `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usare la raccolta sheets della cartella di lavoro di Excel  
 Accedere al foglio di lavoro usando la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Excel.  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Per selezionare il primo foglio di lavoro in una cartella di lavoro usando la raccolta Sheets della cartella di lavoro di Excel  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> per selezionare il primo foglio di lavoro della cartella di lavoro attiva.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>Vedere anche  
 [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: stampa di fogli di lavoro](../vsto/how-to-programmatically-print-worksheets.md)   
 [Procedura: eliminare a livello di programmazione i fogli di lavoro dalle cartelle di lavoro](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Procedura: nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Procedura: proteggere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)  
  
  