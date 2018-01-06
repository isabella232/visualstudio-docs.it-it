---
title: 'Procedura: aprire cartelle di lavoro | Documenti Microsoft'
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
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 541895b941789dd3dbec16e0caad3547f93de904
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-open-workbooks"></a>Procedura: aprire cartelle di lavoro a livello di codice
  Il <xref:Microsoft.Office.Interop.Excel.Workbooks> insieme in Microsoft Office Excel consente di lavorare con tutte le cartelle di lavoro e di aprire le cartelle di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-open-an-existing-workbook"></a>Per aprire una cartella di lavoro esistente  
  
1.  Utilizzare il <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metodo il <xref:Microsoft.Office.Interop.Excel.Workbooks> insieme, passando il percorso alla cartella di lavoro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Una cartella di lavoro denominato `YourWorkbook.xls` deve essere presente in una directory denominata `Test` sull'unità C.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: aprire il file di testo come cartelle di lavoro](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Procedura: creare nuove cartelle di lavoro](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Procedura: salvare a livello di codice le cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md)   
 [Procedura: chiudere a livello di codice le cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  