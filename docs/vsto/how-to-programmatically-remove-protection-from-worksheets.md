---
title: 'Procedura: rimuovere la protezione dai fogli di lavoro a livello di codice | Documenti Microsoft'
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
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
ms.assetid: 034688d2-eda7-4b4a-bcc2-d0999ff879a4
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 08de10397c8abd132a94ed288c7795f068190f24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Procedura: Rimuovere la protezione dai fogli di lavoro a livello di codice
  È possibile rimuovere la protezione a livello di codice da un foglio di lavoro di Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 L'esempio seguente usa la variabile `getPasswordFromUser`, che contiene una password ottenuta dall'utente.  
  
### <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Per rimuovere la protezione da un foglio di lavoro in una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> del foglio di lavoro e passare la password, se necessario. Questo esempio presuppone l'utilizzo di un foglio di lavoro denominato `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]  
  
### <a name="to-unprotect-a-worksheet-in-an-vsto-add-in"></a>Per rimuovere la protezione di un foglio di lavoro in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> del foglio di lavoro attivo e passare la password, se necessario.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: proteggere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Procedura: proteggere a livello di codice le cartelle di lavoro](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Procedura: nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  