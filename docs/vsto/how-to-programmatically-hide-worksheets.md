---
title: 'Procedura: nascondere i fogli di lavoro a livello di codice'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a60a0189af5608496e1f0f415a2d668e896af8e3
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673631"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Procedura: nascondere i fogli di lavoro a livello di codice
  È possibile mostrare o nascondere qualsiasi foglio di lavoro da una cartella di lavoro. Per nascondere un foglio di lavoro, usare l'elemento host Worksheet o accedere al foglio di lavoro usando la raccolta Sheets della cartella di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>Usare l'elemento host foglio di lavoro  
 Se il foglio di lavoro è stato aggiunto in fase di progettazione in una personalizzazione a livello di documento, per nasconderlo usare la proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> .  
  
### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Per nascondere un foglio di lavoro usando un elemento host Worksheet  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> dell'elemento host `Sheet1` sul valore di enumerazione <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usare la raccolta Sheets della cartella di lavoro di Excel  
 Accedere ai fogli di lavoro mediante la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Microsoft Office Excel nei casi seguenti:  
  
-   Si desidera nascondere un foglio di lavoro in un componente aggiuntivo VSTO.  
  
-   Se il foglio di lavoro che si vuole nascondere è stato creato in fase di esecuzione in una personalizzazione a livello di documento  
  
### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Per nascondere un foglio di lavoro usando la raccolta Sheets della cartella di lavoro di Excel  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> del foglio di lavoro sul valore di enumerazione <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>Vedere anche  
 [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: eliminare a livello di programmazione i fogli di lavoro dalle cartelle di lavoro](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Procedura: spostare fogli di lavoro all'interno di cartelle di lavoro](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Procedura: proteggere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)  
  