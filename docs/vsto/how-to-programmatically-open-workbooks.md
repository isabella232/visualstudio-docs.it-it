---
title: 'Procedura: aprire cartelle di lavoro'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd8f6786bd2f7b54ce6b50f2493ebd5d45bba51e
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257358"
---
# <a name="how-to-programmatically-open-workbooks"></a>Procedura: aprire cartelle di lavoro
  Il <xref:Microsoft.Office.Interop.Excel.Workbooks> insieme in Microsoft Office Excel consente di lavorare con tutte le cartelle di lavoro e di aprire le cartelle di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-open-an-existing-workbook"></a>Per aprire una cartella di lavoro esistente  
  
1.  Usare la <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metodo del <xref:Microsoft.Office.Interop.Excel.Workbooks> insieme, passando il percorso alla cartella di lavoro.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Una cartella di lavoro denominato `YourWorkbook.xls` deve essere presente in una directory denominata `Test` nell'unità C.  
  
## <a name="see-also"></a>Vedere anche  
 [Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: a livello di codice aprire i file di testo come cartelle di lavoro](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Procedura: creare nuove cartelle di lavoro](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Procedura: a livello di programmazione salvare cartelle di lavoro](../vsto/how-to-programmatically-save-workbooks.md)   
 [Procedura: chiudere a livello di codice le cartelle di lavoro](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)  
  
  