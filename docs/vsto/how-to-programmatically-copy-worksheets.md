---
title: 'Procedura: copiare a livello di codice i fogli di lavoro | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
ms.assetid: e49e03f5-7b2f-416b-b5fe-0965336c47e1
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f78f4272eb42440c2ddf9ade423ceef9364f75e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-copy-worksheets"></a>Procedura: copiare fogli di lavoro a livello di codice
  È possibile creare una copia di un foglio di lavoro e inserirla prima o dopo un foglio di lavoro esistente nella cartella di lavoro. e non si specifica dove inserire il foglio di lavoro, Excel crea una nuova cartella di lavoro per il nuovo foglio di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Indipendentemente dal fatto che il foglio di lavoro venga copiato a livello di codice o manualmente dall'utente finale, non è presente codice nel nuovo foglio di lavoro e i controlli presenti sul nuovo foglio non funzionano perché il foglio di lavoro appena copiato è un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> e non un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>. I controlli Windows Form e i controlli host possono essere aggiunti solo agli elementi host. Per altre informazioni, vedere [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Per aggiungere una copia di un foglio di lavoro a una cartella di lavoro in una personalizzazione a livello di documento  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> per copiare il primo foglio nella cartella di lavoro corrente e inserire la copia dopo il terzo foglio.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Per aggiungere una copia di un foglio di lavoro a una cartella di lavoro in un componente aggiuntivo VSTO  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> per copiare il primo foglio nella cartella di lavoro corrente e inserire la copia dopo il terzo foglio.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: aggiungere nuovi fogli di lavoro alle cartelle di lavoro](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Procedura: eliminare a livello di codice i fogli di lavoro dalle cartelle di lavoro](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Procedura: selezionare a livello di codice i fogli di lavoro](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  