---
title: 'Procedura: A livello di codice vengono usati i file della cartella di lavoro di elenco'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 850dc26b9a5f270b3806d9623795535d34cf8f4b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989631"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Procedura: A livello di codice vengono usati i file della cartella di lavoro di elenco
  Il <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> proprietà restituisce una raccolta che contiene i nomi di tutti i file che vengono visualizzati nell'elenco dei file usati di recente di Microsoft Office Excel. La lunghezza dell'elenco varia a seconda del numero di file selezionato dall'utente da conservare. È possibile visualizzare i risultati in un intervallo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Per le cartelle di lavoro elenco usato di recente in un oggetto range  
  
1.  Scorrere l'elenco dei file recenti e i nomi visualizzati nelle celle relative a un <xref:Microsoft.Office.Interop.Excel.Range> oggetto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Vedere anche  
 [Lavorare con le cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [NamedRange (controllo)](../vsto/namedrange-control.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
