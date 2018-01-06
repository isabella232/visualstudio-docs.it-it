---
title: 'Procedura: riempire automaticamente a livello di codice gli intervalli con dati modificati in modo incrementale | Documenti Microsoft'
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
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
ms.assetid: 27639d55-8ab5-483c-8907-2ea50dfd2188
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4b832ed0e025cd374ac3cbc645824fe7f37dcf9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Procedura: riempire automaticamente gli intervalli con dati modificati in modo incrementale a livello di codice
  Il <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo il <xref:Microsoft.Office.Interop.Excel.Range> oggetto consente di immettere un intervallo in un foglio di lavoro con valori automaticamente. In genere, il <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo viene utilizzato per archiviare in modo incrementale valori crescenti o decrescenti in un intervallo. È possibile specificare il comportamento, fornendo una costante facoltativa dal <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> enumerazione.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Quando si utilizza, è necessario specificare due intervalli di <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   L'intervallo che chiama il <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> (metodo), che specifica il punto di partenza del riempimento e contiene un valore iniziale.  
  
-   L'intervallo che si desidera compilare, passato come parametro per il <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo. L'intervallo di destinazione deve includere l'intervallo che contiene il valore iniziale.  
  
    > [!NOTE]  
    >  Non è possibile passare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo anziché il <xref:Microsoft.Office.Interop.Excel.Range>. Per altre informazioni, vedere [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 La prima cella dell'intervallo che si desidera compilare deve contenere un valore iniziale.  
  
 Nell'esempio si presuppone che si compila tre aree:  
  
-   La colonna B consiste nell'includere cinque giorni della settimana. Il valore iniziale, digitare **lunedì** nella cella B1.  
  
-   La colonna C consiste nell'includere cinque mesi. Il valore iniziale, digitare **gennaio** nella cella C1.  
  
-   La colonna D consiste nell'includere una serie di numeri, con incrementi di due per ogni riga. Per i valori iniziali, digitare **4** nella cella D1 e **6** nella cella D2.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo degli intervalli](../vsto/working-with-ranges.md)   
 [Procedura: fare riferimento a livello di programmazione agli intervalli del foglio di lavoro nel codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Procedura: a livello di programmazione applicare stili agli intervalli nelle cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: eseguire calcoli in Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  