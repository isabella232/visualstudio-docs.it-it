---
title: 'Procedura: a livello di codice vengono usati i file di cartella di lavoro di elenco | Documenti Microsoft'
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
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 629b27c5947a2744886ac0d3fed8898ece386c6b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Procedura: elencare i file di cartelle di lavoro utilizzati di recente a livello di codice
  Il <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> proprietà restituisce una raccolta che contiene i nomi di tutti i file che vengono visualizzati nell'elenco dei file usati di recente di Microsoft Office Excel. La lunghezza dell'elenco varia a seconda del numero di file, che l'utente ha selezionato da mantenere. È possibile visualizzare i risultati in un intervallo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Per le cartelle di lavoro elenco usato di recente in un oggetto range  
  
1.  Scorrere l'elenco dei file recenti e visualizzare i nomi nelle celle relative a un <xref:Microsoft.Office.Interop.Excel.Range> oggetto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  