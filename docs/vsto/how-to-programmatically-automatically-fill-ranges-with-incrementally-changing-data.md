---
title: Riempimento automatico degli intervalli di dati a livello di codice
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 076381c93d11c2d13bdd89ea5c36c0039e15ef71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547472"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Procedura: riempire automaticamente gli intervalli con dati modificati in modo incrementale a livello di codice
  Il <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo dell' <xref:Microsoft.Office.Interop.Excel.Range> oggetto consente di riempire automaticamente un intervallo in un foglio di un foglio di test. In genere, il <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo viene utilizzato per archiviare i valori che aumentano o diminuiscono in modo incrementale in un intervallo. È possibile specificare il comportamento fornendo una costante facoltativa dall' <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> enumerazione.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Quando si usa, è necessario specificare due intervalli <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- Intervallo che chiama il <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo, che specifica il punto iniziale del riempimento e contiene un valore iniziale.

- Intervallo che si desidera riempire, passato come parametro al <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodo. Questo intervallo di destinazione deve includere l'intervallo che contiene il valore iniziale.

    > [!NOTE]
    > Non è possibile passare un <xref:Microsoft.Office.Tools.Excel.NamedRange> controllo al posto di <xref:Microsoft.Office.Interop.Excel.Range> . Per ulteriori informazioni, vedere [limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Esempio
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>Compilare il codice
 La prima cella dell'intervallo che si desidera riempire deve contenere un valore iniziale.

 Per l'esempio è necessario compilare tre aree:

- La colonna B prevede cinque giorni feriali. Per il valore iniziale digitare **Monday** nella cella B1.

- La colonna C prevede l'inclusione di cinque mesi. Per il valore iniziale, digitare **gennaio** nella cella C1.

- La colonna D prevede l'inclusione di una serie di numeri, incrementando di due per ogni riga. Per i valori iniziali, digitare **4** nella cella D1 e **6** nella cella D2.

## <a name="see-also"></a>Vedere anche
- [Usare gli intervalli](../vsto/working-with-ranges.md)
- [Procedura: fare riferimento a intervalli di fogli di fogli di codice a livello di codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Procedura: applicare stili agli intervalli nelle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Procedura: eseguire calcoli di Excel a livello di codice](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
