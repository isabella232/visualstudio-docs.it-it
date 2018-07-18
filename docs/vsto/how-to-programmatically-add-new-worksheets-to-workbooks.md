---
title: 'Procedura: a livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 80e3ddaa3edd4520e16c8733d3310497ab4ea5af
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255011"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Procedura: a livello di codice aggiungere nuovi fogli di lavoro alle cartelle di lavoro
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
 [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: eliminare a livello di programmazione i fogli di lavoro dalle cartelle di lavoro](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Procedura: a livello di codice selezionare fogli di lavoro](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  